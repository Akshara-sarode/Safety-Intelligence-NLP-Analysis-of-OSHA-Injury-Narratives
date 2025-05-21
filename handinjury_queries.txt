
--1.  unique machine
SELECT COUNT(DISTINCT [Cleaned Source]) AS uniqueMachines
        FROM HandInjuryData;


-- 2. missing value check
SELECT COUNT(*) AS MissingValues
        FROM HandInjuryData
        WHERE [Cleaned Source] IS NULL 
           OR [Likely Cause] IS NULL 
           OR [Final Narrative] IS NULL;


-- 3. Top machines by incidents
SELECT [Cleaned Source], COUNT(ID) AS NoOfIncidents
        FROM HandInjuryData
        GROUP BY [Cleaned Source]
        ORDER BY NoOfIncidents DESC
        LIMIT 10;


-- 4. Narrative length by machine
SELECT [Cleaned Source], 
               AVG(LENGTH([Final Narrative])) AS AvgNarrativeLength
        FROM HandInjuryData
        GROUP BY [Cleaned Source]
        ORDER BY AvgNarrativeLength DESC
        LIMIT 10;


-- 5. Event type by frequency
SELECT [EventTitle], COUNT(ID) AS TotalEvents
        FROM HandInjuryData
        GROUP BY [EventTitle]
        ORDER BY TotalEvents DESC
        LIMIT 10;


-- 6. Injury nature frequency
SELECT [General Nature], COUNT(ID) AS Frequency
        FROM HandInjuryData
        GROUP BY [General Nature]
        ORDER BY Frequency DESC
        LIMIT 10;


-- 7. Machines vs Causes
SELECT [Cleaned Source], [Likely Cause], COUNT(ID) AS CaseCount
        FROM HandInjuryData
        GROUP BY [Cleaned Source], [Likely Cause]
        ORDER BY CaseCount DESC
        LIMIT 10;


-- 8. States with Most Incidents
SELECT State, COUNT(ID) AS IncidentCount
        FROM HandInjuryData
        GROUP BY State
        ORDER BY IncidentCount DESC
        LIMIT 10;


-- 9. Month-wise Incident Trend
SELECT Month, COUNT(ID) AS MonthlyIncidents
        FROM HandInjuryData
        GROUP BY Month
        ORDER BY Month ASC;


-- 10. Most Common Body Parts Injured
SELECT [General Part of Body], COUNT(ID) AS BodyPartFrequency
        FROM HandInjuryData
        GROUP BY [General Part of Body]
        ORDER BY BodyPartFrequency DESC
        LIMIT 10;


-- 11. Average Narrative Length by State
SELECT State, AVG(LENGTH([Final Narrative])) AS AvgNarrativeLength
        FROM HandInjuryData
        GROUP BY State
        ORDER BY AvgNarrativeLength DESC
        LIMIT 10;


-- 12. Machine and State Combination Frequency
SELECT [Cleaned Source], State, COUNT(ID) AS CaseCount
        FROM HandInjuryData
        GROUP BY [Cleaned Source], State
        ORDER BY CaseCount DESC
        LIMIT 10;


-- 13. Event Title and Month Combination
SELECT EventTitle, Month, COUNT(ID) AS EventMonthlyCount
        FROM HandInjuryData
        GROUP BY EventTitle, Month
        ORDER BY EventMonthlyCount DESC
        LIMIT 10;


-- 14. Top 5 Machines per State
SELECT State, [Cleaned Source], COUNT(ID) AS IncidentCount
        FROM HandInjuryData
        GROUP BY State, [Cleaned Source]
        ORDER BY State, IncidentCount DESC;


-- 15. Monthly Narrative Volume (Avg Words)
SELECT Month, AVG(LENGTH([Final Narrative])) AS AvgWords
        FROM HandInjuryData
        GROUP BY Month
        ORDER BY Month ASC;


-- 16. Common Narratives by Machine Type
SELECT [Cleaned Source], [Final Narrative]
        FROM HandInjuryData
        ORDER BY LENGTH([Final Narrative]) DESC
        LIMIT 10;



-- 17. Body Part vs Machine
SELECT [General Part of Body], [Cleaned Source], COUNT(ID) AS Count
        FROM HandInjuryData
        GROUP BY [General Part of Body], [Cleaned Source]
        ORDER BY Count DESC
        LIMIT 10;


-- 18. Top Narratives by Length
SELECT [Final Narrative], LENGTH([Final Narrative]) AS CharLength
        FROM HandInjuryData
        ORDER BY CharLength DESC
        LIMIT 10;


-- 19. Top Injury Causes with Body Parts
SELECT [Likely Cause], [General Part of Body], COUNT(ID) AS Count
        FROM HandInjuryData
        GROUP BY [Likely Cause], [General Part of Body]
        ORDER BY Count DESC
        LIMIT 10;


-- 20. Machines with Most 'Caught-in' Cases
SELECT [Cleaned Source], COUNT(ID) AS Count
        FROM HandInjuryData
        WHERE [Likely Cause] LIKE '%Caught%'
        GROUP BY [Cleaned Source]
        ORDER BY Count DESC
        LIMIT 10;





-- 21. Top 10 States with Longest Average Injury Narratives
SELECT State, AVG(LENGTH([Final Narrative])) AS AvgNarrativeLength
FROM HandInjuryData
GROUP BY State
ORDER BY AvgNarrativeLength DESC
LIMIT 10;


-- 22. Most Frequent Machine Type per State (using window function logic)
SELECT State, [Cleaned Source], IncidentCount
FROM (
  SELECT State, [Cleaned Source], COUNT(ID) AS IncidentCount,
         RANK() OVER (PARTITION BY State ORDER BY COUNT(ID) DESC) AS rk
  FROM HandInjuryData
  GROUP BY State, [Cleaned Source]
)
WHERE rk = 1;






-- 23. Machine Types with Highest Diversity in Injury Causes
SELECT [Cleaned Source], COUNT(DISTINCT [Likely Cause]) AS CauseVariety
FROM HandInjuryData
GROUP BY [Cleaned Source]
ORDER BY CauseVariety DESC
LIMIT 10;


-- 24. Average Narrative Length by Month and Machine Type
SELECT Month, [Cleaned Source], AVG(LENGTH([Final Narrative])) AS AvgLength
FROM HandInjuryData
GROUP BY Month, [Cleaned Source]
ORDER BY Month, AvgLength DESC
LIMIT 20;


-- 25. Machines Associated with Injuries to Multiple Body Parts
SELECT [Cleaned Source], COUNT(ID) AS MultiPartInjuries
FROM HandInjuryData
WHERE [General Part of Body] = 'Multiple Body Parts'
GROUP BY [Cleaned Source]
ORDER BY MultiPartInjuries DESC
LIMIT 10;


-- 26. Most Common Event Titles for Upper Extremity Injuries
SELECT [EventTitle], COUNT(ID) AS Total
FROM HandInjuryData
WHERE [General Part of Body] = 'Upper Extremities'
GROUP BY [EventTitle]
ORDER BY Total DESC
LIMIT 10;


-- 27. States with Most 'Caught-in Machinery' Cases
SELECT State, COUNT(ID) AS CaughtInCases
FROM HandInjuryData
WHERE [Likely Cause] LIKE '%Caught%'
GROUP BY State
ORDER BY CaughtInCases DESC
LIMIT 10;


-- 28. Machines Linked to Injuries with the Longest Narratives (Top 15)
SELECT [Cleaned Source], AVG(LENGTH([Final Narrative])) AS AvgNarrativeLength
FROM HandInjuryData
GROUP BY [Cleaned Source]
ORDER BY AvgNarrativeLength DESC
LIMIT 15;

-- 29. Body Parts Most Affected by Machine Saw (Top 8)
SELECT [General Part of Body], COUNT(ID) AS InjuryCount
FROM HandInjuryData
WHERE [Cleaned Source] = 'Machine Saw'
GROUP BY [General Part of Body]
ORDER BY InjuryCount DESC
LIMIT 8;


-- 30. Most Common Likely Causes for Injuries Over All States (Top 25)
SELECT [Likely Cause], COUNT(ID) AS CauseCount
FROM HandInjuryData
GROUP BY [Likely Cause]
ORDER BY CauseCount DESC
LIMIT 25;


-- 31. Machines Involved in Injuries Containing the Word 'blade' in Narrative
SELECT [Cleaned Source], COUNT(ID) AS BladeMentions
FROM HandInjuryData
WHERE LOWER([Final Narrative]) LIKE '%blade%'
GROUP BY [Cleaned Source]
ORDER BY BladeMentions DESC
LIMIT 10;

-- 32. States with Both High Injury Counts AND Narrative Length Above Average
SELECT State, COUNT(ID) AS Incidents, AVG(LENGTH([Final Narrative])) AS AvgNarrativeLength
FROM HandInjuryData
GROUP BY State
HAVING Incidents > 500 AND AvgNarrativeLength > (
    SELECT AVG(LENGTH([Final Narrative])) FROM HandInjuryData
)
ORDER BY Incidents DESC;


-- 33. Count of Records Without a Likely Cause Mentioned (Missing Data)
SELECT COUNT(*) AS RecordsMissingCause
FROM HandInjuryData
WHERE [Likely Cause] IS NULL OR TRIM([Likely Cause]) = '';


-- 34. Machines With the Widest Variety of Body Parts Affected
SELECT [Cleaned Source], COUNT(DISTINCT [General Part of Body]) AS UniqueBodyParts
FROM HandInjuryData
GROUP BY [Cleaned Source]
ORDER BY UniqueBodyParts DESC
LIMIT 15;



G12: List current vocabulary release number
---

This query returns current vocabulary release number.

Sample query:


```sql
SELECT
  vocabulary_name,
  vocabulary_version
FROM vocabulary
;
```
Input:

None

Output:

| Field |  Description |
| --- | --- |
|  vocabulary_name |  Version number of current OMOP vocabulary release |

Sample output record:

| Field |  Value |
| --- | --- |
|  vocabulary_name |  OMOP Vocabulary v4.3 Q2-2013 |


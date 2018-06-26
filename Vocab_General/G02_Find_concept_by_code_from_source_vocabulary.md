G02: Find a concept by code from a source vocabulary
--
This query obtains the concept details associated with a concept code, such as name, class, level and source vocabulary.

Only concepts from the Standard Vocabularies can be searched using this query. If you want to translate codes from other Source Vocabularies to Standard Vocabularies use G06 query.

Sample query run:

The following is a sample run of the query to extract details for concept code of ‘74474003’ from concept vocabulary ID of ‘1’ (for SNOMED-CT) for the current date. The input parameters are highlighted in blue. Note that in contrast to concept ID the concept codes are not unique across different vocabularies. If you don't specify the vocabulary, you might get results for the same code in different vocabularies.

```sql
SELECT
  c.concept_id,
  c.concept_name,
  c.concept_code,
  c.concept_class_id,
  c.vocabulary_id
FROM concept AS c
WHERE c.concept_code = '74474003' -- PARAMETER
      AND c.vocabulary_id = 'SNOMED' -- PARAMETER
      AND sysdate BETWEEN valid_start_date AND valid_end_date -- PARAMETER
;
;
```
Input:

|  Parameter |  Example |  Mandatory |  Notes |
| --- | --- | --- | --- |
|  Concept Code |  '74474003' |  Yes | SNOMED-CT code for "GI - Gastrointestinal hemorrhage". Concept code can be alpha-numeric and should be enclosed in single quotes. |
|  Vocabulary ID |  'SNOMED' |  Yes | The vocabulary ID as listed in the VOCABULARY table. |
|  As of date |  Sysdate |  No | Valid record as of specific date. Current date – sysdate is a default |

Output:

|  Field |  Description |
| --- | --- |
|  Concept_ID |  Concept Identifier entered as input |
|  Concept_Name |  Name of the standard concept |
|  Concept_Code |  Concept code of the standard concept in the source vocabulary |
|  Concept_Class |  Concept class of standard vocabulary concept |
|  Vocabulary_ID |  Name of the vocabulary the standard concept is derived from |

Sample output record:

|  Field |  Value |
| --- | --- |
|  Concept_ID |  192671 |
|  Concept_Name |  GI - Gastrointestinal haemorrhage |
|  Concept_Code |  74474003 |
|  Concept_Class |  Clinical finding |
|  Vocabulary_ID |  SNOMED-CT |

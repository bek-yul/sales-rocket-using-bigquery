# Sales Rocket 🚀🚀🚀

Sales calls hold a wealth of untapped insights. Every transcript contains valuable signals about customer needs, objections, and pain points—but in most organizations, these records are left unused or are too cumbersome to analyze at scale. Traditional analytics tools struggle with this type of unstructured data, leaving sales teams without actionable guidance on how to improve their conversations or address recurring concerns.

This project tackles the problem by leveraging BigQuery’s advanced AI capabilities to transform raw sales call transcripts into structured insights. Using Generative AI (**ML.GENERATE_TEXT**) within BigQuery, it extracts recurring and new objections that directly impact purchasing decisions. Instead of letting transcripts collect dust, it creates a dynamic feedback loop that empowers sales teams to refine their messaging and close more deals.



#### Architecture Diagram

```text
      +----------------------------+        +------------------------------+
      |        Call transcripts    |        |          Google Cloud        |
      |        (text, CSV, JSON)   |        |    BigQuery & Vertex AI      |
      +-------------+--------------+        +---------------+--------------+
                    |  Load/ingest                          |
                    v                                       |
      +---------------------------+                         |
      | BigQuery: call_transcripts|                         |
      |           (table)         |                         |
      +-------------+-------------+                         |
                    |  Extract objections &                 |
                    |  assign categories using              v
                    |  ML.GENERATE_TEXT    +--------------------------------+   
                    |<---------------------| Vertex AI Connection           |
                    |                      | Gemini 2.5 Pro (generation)    |    
                    |                      +--------------------------------+              
                    v                                       
      +---------------------------+
      | BigQuery: objections      |
      |           (table)         |
      +-------------+-------------+
                    |
                    | Query / Dashboard / Export (e.g., BigQuery UI, BI)
                    v
      +---------------------------+
      |  Sales team / RevOps      |
      |  access insights          |
      +---------------------------+
```

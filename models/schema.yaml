version: 2

sources:
  - name: raw_covid19
    schema: airbyte_schema
    database: AIRBYTE_DATABASE
    description: A replica of the covid19 demographics data from Google BigQuery Open data.
    tables:
      - name: index
        columns:
          - name: _airbyte_index_hashid
            description: Hash column based on the values in the record.
            tests:
              - unique
              - not_null

      - name: demographics
        columns:
          - name: _airbyte_demographics_hashid
            description: Hash column based on the values in the record.
            tests:
              - unique
              - not_null

      - name: economy
        columns:
          - name: _airbyte_economy_hashid
            description: Hash column based on the values in the record.
            tests:
              - unique
              - not_null

      - name: epidemiology
        columns:
          - name: _airbyte_epidemiology_hashid
            description: Hash column based on the values in the record.
            tests:
              - unique
              - not_null



models:
  - name: base_index
    config:
      materialized: view  

  - name: base_demographics
    config:
      materialized: view
    columns:
      - name: location_key
        tests:
          - unique
          - not_null

  - name: base_economy
    config:
      materialized: view
    columns:
      - name: location_key
        tests:
          - unique
          - not_null
 
  - name: base_epidemiology
    config:
      tags: ['daily']
      materialized: view
    columns:
      - name: location_key
        tests:
          - relationships:
              to: ref('base_index')
              field: location_key
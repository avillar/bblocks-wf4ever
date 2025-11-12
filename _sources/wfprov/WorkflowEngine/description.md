# wfprov:WorkflowEngine

## Description

A **WorkflowEngine** represents a software agent that executes workflows. The workflow engine is responsible for enacting workflow and process executions, managing the execution environment and resources.

## Relations

- Process runs and workflow runs reference the engine via `wfprov:wasEnactedBy`
- This is the inverse relationship: the engine enacts the executions

## Examples of engines

- ZOO-Project WPS
- Apache Airflow
- Nextflow
- Snakemake
- CWL Runner

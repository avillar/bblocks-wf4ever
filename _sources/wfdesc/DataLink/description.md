# wfdesc:DataLink

## Description

A **DataLink** represents a data flow connection between processes in a workflow. It describes how the output of one process is connected to the input of another process, defining the data dependencies between workflow steps.

## Relations

- Links a `wfdesc:Output` (source) to a `wfdesc:Input` (sink)
- Used by `wfdesc:Workflow` via `hasDataLink`
- Defines the data flow between processes

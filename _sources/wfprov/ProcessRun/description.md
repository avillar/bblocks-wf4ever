# wfprov:ProcessRun

## Description

A **ProcessRun** represents an execution instance of a process. It captures what actually happened during the execution of a process described by `wfdesc:Process`, including the input artifacts used, output artifacts generated, and timing information.

## Relations

- Must be linked to a `wfdesc:Process` via `describedByProcess`
- Uses `wfprov:Artifact` via `usedInput`
- Output artifacts reference this ProcessRun via their `wasOutputFrom` property
- Can be part of a `wfprov:WorkflowRun` via `wasPartOfWorkflowRun`
- Can be enacted by a `wfprov:WorkflowEngine` via `wasEnactedBy`

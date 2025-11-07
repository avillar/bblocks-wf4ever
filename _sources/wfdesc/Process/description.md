# wfdesc:Process

## Description

A **Process** represents a unit of computation in a workflow. It is the base class that can be:
- An **atomic process**: A single computational task (e.g., running a command-line tool)
- A **Workflow**: A composite process containing sub-processes

Processes are characterized by their inputs (what data they consume) and outputs (what data they produce).

## Class Hierarchy

```
wfdesc:Process (base class)
└── wfdesc:Workflow (composite process with sub-processes)
```

## Process Interface

The interface of a process is defined by its inputs and outputs.

## Atomic vs Composite

### Atomic Process
- Performs a single computational task
- Cannot be decomposed further in the workflow model
- Examples: Run GDAL command, Execute Python script, Call web service

### Composite Process (Workflow)
- Contains sub-processes via `hasSubProcess`
- Has internal data flow via `hasDataLink`
- Can be treated as a black box via its inputs/outputs

## Related Classes

- **Input**: Parameters that feed data into the process
- **Output**: Parameters that produce data from the process
- **Workflow**: Subclass that represents composite processes
- **DataLink**: Connects processes together in a workflow

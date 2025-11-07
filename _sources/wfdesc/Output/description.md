# wfdesc:Output

## Description

An **Output** is a parameter that produces data from a workflow process. Outputs can:
- Produce final workflow results
- Feed data to inputs of other processes via DataLinks
- Be intermediate results in a workflow

## Class Hierarchy

```
wfdesc:Parameter
└── wfdesc:Output
```

## Usage in Workflows

Outputs are declared using the `hasOutput` property on a Process.

## Data Flow

Outputs can be connected to Inputs via DataLinks.

## Related Classes

- **Parameter**: Base class (parent)
- **Input**: Complementary class for process inputs
- **DataLink**: Connects Outputs to Inputs (Output is source)
- **Process**: Container that has outputs via `hasOutput` property

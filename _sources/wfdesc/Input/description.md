# wfdesc:Input

## Description

An **Input** is a parameter that receives data into a workflow process. Inputs can receive data from:
- External sources (workflow inputs)
- Outputs of other processes (via DataLinks)
- Default values or configurations

## Class Hierarchy

```
wfdesc:Parameter
└── wfdesc:Input
```

## Usage in Workflows

Inputs are declared using the `hasInput` property on a Process.

## Data Flow

Inputs can be connected to Outputs via DataLinks.

## Related Classes

- **Parameter**: Base class (parent)
- **Output**: Complementary class for process outputs
- **DataLink**: Connects Outputs to Inputs
- **Process**: Container that has inputs via `hasInput` property

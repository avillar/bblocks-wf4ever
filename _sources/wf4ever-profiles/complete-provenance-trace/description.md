# Complete Workflow Provenance Trace

## Overview

This master profile demonstrates the full integration of the Wf4Ever ontology suite, combining:

1. **Research Object (RO)**: Container and packaging
2. **Workflow Description (WFDESC)**: Prospective provenance
3. **Workflow Execution (WFPROV)**: Retrospective provenance

## Purpose

This building block serves as:

- **Integration test**: Validates that all Wf4Ever components work together
- **Documentation**: Shows how to combine all pieces
- **Example**: Real CWLProv data from scientific workflow
- **Validation**: End-to-end test of RDF graph generation

## Structure

A complete provenance trace contains four main components:

### 1. Research Object

The container that aggregates all resources:

```json
{
  "researchObject": {
    "id": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/",
    "type": "ResearchObject",
    "aggregates": [...],
    "annotations": [...]
  }
}
```

**Key properties:**
- `aggregates`: All files, data, workflows included
- `annotations`: Metadata about aggregated resources
- `manifest`: Points to the RO manifest
- `conformsTo`: CWLProv version

### 2. Workflow Description

The workflow structure (prospective provenance):

```json
{
  "workflow": {
    "id": "arcp://uuid,.../workflow/packed.cwl#main",
    "type": "Workflow",
    "hasInput": [...],
    "hasOutput": [...]
  }
}
```

**Key properties:**
- `hasInput`: Input parameters of the workflow
- `hasOutput`: Output parameters of the workflow
- `hasSubWorkflow`: Nested workflows (if any)

### 3. Workflow Execution

The execution trace (retrospective provenance):

```json
{
  "workflowRun": {
    "id": "urn:uuid:f02b8997-a6b1-4909-9946-9129c2b3f10c",
    "type": "WorkflowRun",
    "describedByWorkflow": "arcp://uuid,.../workflow/packed.cwl#main",
    "used": [...],
    "generated": [...],
    "wasAssociatedWith": [...]
  }
}
```

**Key properties:**
- `describedByWorkflow`: Links to workflow definition
- `used`: Input artifacts consumed
- `generated`: Output artifacts produced
- `wasAssociatedWith`: Agents/engines that executed
- `startedAtTime` / `endedAtTime`: Execution timeline

### 4. Manifest

The RO manifest describing the bundle:

```json
{
  "manifest": {
    "id": "arcp://uuid,.../metadata/manifest.json",
    "type": "Manifest",
    "authoredBy": {...},
    "describes": "arcp://uuid,f02b8997-a6b1-4909-9946-9129c2b3f10c/"
  }
}
```

## Relationships

The complete trace shows these key relationships:

```
Research Object
    ├─ ore:aggregates → Workflow (WFDESC)
    ├─ ore:aggregates → WorkflowRun Provenance (WFPROV)
    ├─ ore:aggregates → Input Data
    ├─ ore:aggregates → Output Data
    └─ ore:isDescribedBy → Manifest

Workflow (WFDESC)
    ├─ wfdesc:hasInput → Input Parameters
    └─ wfdesc:hasOutput → Output Parameters

WorkflowRun (WFPROV)
    ├─ wfprov:describedByWorkflow → Workflow
    ├─ prov:used → Input Artifacts
    ├─ prov:generated → Output Artifacts
    ├─ prov:wasAssociatedWith → Agents
    ├─ prov:startedAtTime → Start Time
    └─ prov:endedAtTime → End Time
```

## PROV-O Mapping

This complete trace maps to PROV-O as follows:

- **Research Object** → `prov:Collection` (specialized as `prov:Bundle`)
- **Workflow** → Description (no direct PROV equivalent, stays in WFDESC)
- **WorkflowRun** → `prov:Activity`
- **Input/Output Artifacts** → `prov:Entity`
- **Workflow Engine** → `prov:Agent` (specialized as `prov:SoftwareAgent`)

## Use Cases

### 1. Scientific Workflow Archival

Package a complete workflow execution for long-term preservation:

- Workflow definition (how to reproduce)
- Execution trace (what actually happened)
- Input data (what was used)
- Output data (what was generated)
- Software environment (how it was run)

### 2. Reproducibility

Enable others to:

1. Understand the workflow structure
2. See the actual execution parameters
3. Trace data lineage
4. Reproduce the results

### 3. FAIR Data Compliance

Meet FAIR principles:

- **Findable**: Unique identifiers for all components
- **Accessible**: Standard formats (JSON-LD, RDF)
- **Interoperable**: Standard ontologies (PROV-O, DCAT)
- **Reusable**: Complete provenance metadata

### 4. Workflow Comparison

Compare different executions:

- Same workflow, different parameters
- Same workflow, different data
- Different versions of workflow
- Performance analysis

## Example: Mangrove Mapping Workflow

The included example shows a real scientific workflow for mangrove mapping using Sentinel-2 satellite imagery.

**Workflow inputs:**
- `cloud_cover_max`: 20% (maximum acceptable cloud coverage)
- `days_back`: 90 (days of historical data)
- `east`: 95.35° (longitude)
- `north`: 16.1° (latitude)

**Execution:**
- Started: 2025-11-03T15:14:02
- Ended: 2025-11-03T15:14:17
- Duration: ~15 seconds
- Engine: cwltool 3.1.20251031082601

**Outputs:**
- Mangrove classification results
- Aggregated in Research Object

## Validation

This building block enables validation at multiple levels:

1. **JSON Schema**: Structure validation
2. **JSON-LD**: RDF graph generation
3. **SHACL**: Semantic constraints (future)
4. **PROV Constraints**: PROV-O model compliance (future)

## Next Steps

To complete the master profile validation:

1. ✅ Create complete trace schema
2. ✅ Create real example
3. ⏳ Add SHACL shapes for validation
4. ⏳ Create SPARQL queries for analysis
5. ⏳ Generate transformations to other formats

## See Also

- [Research Object](../ro/ResearchObject/description.md)
- [Workflow](../wfdesc/Workflow/description.md)
- [WorkflowRun](../wfprov/WorkflowRun/description.md)
- [CWLProv Specification](https://w3id.org/cwl/prov)

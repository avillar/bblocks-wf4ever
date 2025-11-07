# wf4ever:File

## Description

A **File** is a specialization of `wfdesc:Artifact` representing a file-based data entity. Files are commonly used as inputs and outputs in scientific workflows, and this class provides semantic precision for file-typed artifacts.

## Relationship to Base Classes

```
wfdesc:Artifact
  └─ wf4ever:File
```

A File is a specific type of Artifact that represents file-system based data, as opposed to in-memory values or streamed data.

## Properties

Inherits all properties from `wfdesc:Artifact`, plus:

- `@type` : Must include "File" (can be multi-typed with wfprov:Artifact, etc.)
- `basename` : The base filename (without directory path)
- `checksum` : File integrity checksum (e.g., SHA256, MD5)
- `size` : File size in bytes
- `format` : Media type or file format (e.g., "text/csv", "image/tiff")

## Usage in CWL Provenance

In CWLProv (Common Workflow Language Provenance), files are dual-typed to combine provenance semantics with artifact type precision:

```json
{
  "@id": "id:4d15cb37-a4a3-4170-a7aa-529399cb4753",
  "prov:type": [
    {
      "$": "wfprov:Artifact",
      "type": "prov:QUALIFIED_NAME"
    },
    {
      "$": "wf4ever:File",
      "type": "prov:QUALIFIED_NAME"
    }
  ],
  "cwlprov:basename": "catalog.json"
}
```

## Common File Types in Workflows

- **Data files**: CSV, JSON, GeoTIFF, NetCDF, HDF5
- **Configuration files**: YAML, XML, INI
- **Scripts**: Python, R, Shell scripts
- **Documents**: PDF, HTML, Markdown
- **Images**: PNG, JPEG, TIFF (for raster data)

## Relations

- Subclass of `wfdesc:Artifact`
- Can be used in `wfprov:Artifact` contexts for provenance tracking
- Can be aggregated in `ro:Folder` via `ro:FolderEntry`


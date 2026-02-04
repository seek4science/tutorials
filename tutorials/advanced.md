# Advanced FAIRDOM-SEEK Tutorial

This tutorial covers advanced features for power users and administrators.

## Sample and Sample Types

### Understanding Sample Types

Sample Types define templates for biological samples with custom attributes:

- Text fields
- Controlled vocabularies
- Links to other samples
- Ontology terms

### Creating a Sample Type

1. Navigate to **Create** → **Sample Type**
2. Define attributes:
   - Name and description
   - Data type (text, number, date, etc.)
   - Required/optional status
   - Controlled vocabulary options
3. Save the sample type

### Registering Samples

```yaml
# Example sample attributes
Sample:
  title: "Cell Culture Sample A"
  sample_type: "Cell Line"
  attributes:
    organism: "Homo sapiens"
    cell_line: "HeLa"
    passage_number: 5
    culture_date: "2024-01-15"
```

## Templates and Metadata

### Using ISA-JSON Templates

SEEK supports ISA-JSON for standardized metadata:

1. Download a template from your project
2. Fill in metadata using a spreadsheet or ISA tools
3. Upload the completed template
4. SEEK parses and creates linked assets

### Custom Metadata Extensions

Extend default metadata schemas:

1. Go to **Admin** → **Extended Metadata Types**
2. Create attribute definitions
3. Associate with asset types
4. Users can now add custom metadata

## Workflows and Pipelines

### Galaxy Integration

Connect SEEK with Galaxy for computational workflows:

1. Register your Galaxy workflow in SEEK
2. Link input data files
3. Execute workflows directly
4. Results automatically registered

### CWL Workflows

```yaml
# Example CWL workflow reference
cwlVersion: v1.0
class: Workflow
inputs:
  input_file: File
outputs:
  output_file:
    type: File
    outputSource: analysis/result
```

## Ontology Integration

### Adding Ontologies

SEEK integrates with BioPortal and OLS:

1. Configure ontology sources in settings
2. Enable ontology-based search
3. Tag assets with ontology terms

### Semantic Annotations

Annotate assets with controlled vocabularies:

- Sample attributes linked to ontologies
- Searchable semantic metadata
- Cross-platform interoperability

## Bulk Operations

### Batch Upload

For uploading multiple assets:

1. Prepare a spreadsheet with metadata
2. Use **Batch Upload** feature
3. Map columns to SEEK fields
4. Review and confirm

### Bulk Editing

Edit multiple assets simultaneously:

1. Select assets from search results
2. Click **Bulk Edit**
3. Modify shared attributes
4. Apply changes

## Project Administration

### Managing Members

| Role | Permissions |
|------|-------------|
| **Administrator** | Full control, manage members |
| **Project Manager** | Create/edit assets, manage studies |
| **Member** | Create/edit own assets |
| **Guest** | View only |

### Access Policies

Create reusable sharing policies:

```yaml
Policy:
  name: "Consortium Sharing"
  access_type: "download"
  scope:
    - type: "Project"
      id: 123
    - type: "Programme"
      id: 456
```

## Snapshots and Versioning

### Creating Snapshots

Preserve asset states for publications:

1. Navigate to the asset
2. Click **Create Snapshot**
3. Add version description
4. Snapshot is immutable and citable

### DOI Registration

Register DOIs for citations:

1. Enable DataCite integration
2. Create a snapshot
3. Click **Mint DOI**
4. Receive persistent identifier

## Integration with External Systems

### ELIXIR AAI

Single sign-on with ELIXIR:

1. Configure ELIXIR AAI in settings
2. Users authenticate via their institution
3. Automatic account provisioning

### openBIS Integration

Sync with openBIS for raw data:

1. Configure openBIS connection
2. Map data spaces to SEEK projects
3. Automatic synchronization

## Next Steps

- Explore the [API Tutorial](api.md) for programmatic access
- Review [SEEK Administration Guide](https://docs.seek4science.org/tech/administration.html)
- Join the [FAIRDOM community](https://fair-dom.org/community)

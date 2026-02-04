# ISA Structure

SEEK uses the ISA (Investigation-Study-Assay) framework to organize research data hierarchically.

## The Hierarchy

```
Project
└── Investigation
    └── Study
        └── Assay
            ├── Data Files
            ├── Models
            └── SOPs
```

## Projects

Projects are collaborative workspaces that contain all related research.

- Group members with defined roles
- Contain one or more Investigations
- Define default sharing policies

### Creating a Project

1. Click **Create** → **Project**
2. Enter title and description
3. Add members and assign roles
4. Click **Create**

## Investigations

Investigations represent high-level research questions or goals.

- Belong to one or more Projects
- Contain related Studies
- Describe the overall research aim

### Creating an Investigation

1. Click **Create** → **Investigation**
2. Provide a descriptive title
3. Link to your Project
4. Add description of research goals

## Studies

Studies represent specific experimental approaches within an Investigation.

- Belong to one Investigation
- Contain related Assays
- Describe experimental design

### Creating a Study

1. Navigate to your Investigation
2. Click **Add Study**
3. Describe the experimental approach
4. Add relevant protocols

## Assays

Assays are individual experiments or analyses that produce data.

- Belong to one Study
- Link directly to Data Files, Models, SOPs
- Describe specific measurements

### Assay Types

| Type | Description |
|------|-------------|
| **Experimental** | Lab-based measurements |
| **Modelling** | Computational analysis |

## Best Practices

- Create Projects for distinct research efforts
- Use Investigations for major research questions
- Group related experiments in Studies
- Link all data to specific Assays

## Next Steps

Learn how to [Upload Data](uploading-data.md) and attach it to your ISA structure.

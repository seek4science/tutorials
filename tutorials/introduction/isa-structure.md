# ISA Structure

SEEK uses the ISA (Investigation-Study-Assay) framework to organize research data hierarchically.

## The Hierarchy

```text
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
2. Select the programme (if applicable) that your project belongs to
3. Enter project title and description (optional)
4. Add the name of the institution you are affiliated with
5. Click **Create**

## Investigations

Investigations represent high-level research questions or goals.

- Belongs to one Project
- Contain related Studies
- Describe the overall research aim

### Creating an Investigation

1. Click **Create** → **Investigation**
2. Provide a descriptive title and description of the research question
3. Link to your Project
4. Set the default sharing policy (when unsure, choose "Public, no access")
5. Optionally, add Creators, Tags, Publications, and Discussion Channels
6. Click **Create**

## Studies

Studies represent specific experimental approaches within an Investigation.

- Belong to one Investigation
- Contain related Assays
- Describe experimental design

### Creating a Study

1. Navigate to your Investigation and add study or click Create in the top menu and select Study
2. Add a descriptive title and description of the experimental approach
3. Link to your Investigation
4. Set the default sharing policy (when unsure, choose "Public, no access")
5. Optionally, add Creators, Tags, Publications, and Discussion Channels
6. Click **Create**

## Assays

Assays are individual experiments or analyses that produce data.

- Belong to one Study
- Link directly to Data Files, Models, SOPs
- Describe specific measurements

### Assay Types

| Type             | Description            |
|------------------|------------------------|
| **Experimental** | Lab-based measurements |
| **Modelling**    | Computational analysis |

### Creating an Assay

1. Navigate to your Study and add assay or click Create in the top menu and select Assay
2. Select the assay type (Experimental or Modelling)
3. Add a descriptive title and description of the experiment
4. Specify the study it belongs to
5. Set the assay type and technology type (if applicable)
6. When using an organism or cell line, select the appropriate term from the list (needs to be added to the system by an administrator)
7. Set the default sharing policy (when unsure, choose "Public, no access")
8. Optionally, add Creators, Tags, Publications, and Discussion Channels
9. Click **Create**

## Best Practices

- Create Projects for distinct research efforts
- Use Investigations for major research questions
- Group related experiments in Studies
- Link all data to specific Assays

## Next Steps

Learn how to [Upload Data](uploading-data.md) and attach it to your ISA structure.

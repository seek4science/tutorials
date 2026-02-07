# UNDER DEVELOPMENT

# Uploading Data

Learn how to add and manage research assets in FAIRDOM-SEEK.

## Asset Types

SEEK supports various asset types:

| Asset Type        | Description                   | Examples             |
|-------------------|-------------------------------|----------------------|
| **Data Files**    | Raw or processed data         | CSV, Excel, images   |
| **Models**        | Computational models          | SBML, CellML, MATLAB |
| **SOPs**          | Standard Operating Procedures | Protocols, methods   |
| **Publications**  | Published papers              | DOI links            |
| **Documents**     | Supporting docs               | PDFs, Word files     |
| **Presentations** | Slides and posters            | PowerPoint, PDF      |

## Uploading a Data File

### Step 1: Start Upload

1. Click **Create** → **Data File**
2. Or navigate to an Assay and click **Add Data File**

### Step 2: Add File

Choose one of:

- **Local file** - Upload from your computer
- **Remote URL** - Link to external storage

### Step 3: Add Metadata

Required fields:

- **Title** - Descriptive name
- **Projects** - Associated project

Recommended fields:

- **Description** - What the data contains
- **Tags** - Keywords for discovery

### Step 4: Set template (if applicable)

If your SEEK instance has templates configured, you may be prompted to select a template that matches your data type. This will pre-populate metadata fields and ensure consistency. In addition you can also set Data type and format annotations to further describe the content of your data file.

### Step 5: Set License & Permissions

Choose who can access:

- **Private** - Only you
- **Project members** - Your collaborators
- **Public** - Everyone

### Step 6: Link to ISA

Associate with your research structure:

- Select relevant **Assay(s)**
- Or create a new Assay and link the data file to it

### Step 7: Other associated items

Optionally, you can also link your data file to other associated items such as:

- **Publications** - Link to related papers
- **Discussion Channels** - Add URLs for related discussions
- **Attributions** - Link to other assets such as models, SOPs, etc. that are relevant to the data file you are uploading.
- **Events** - Link to events such as conferences, workshops, etc. that are relevant to the data file you are uploading.
- **Workflows** - Link to workflows that are relevant to the data file you are uploading.
- **Observation Units** - Link to observation units that are relevant to the data file you are uploading.

### Step 8: Create

Click **Create** to finish upload.

## Managing Assets

### Editing

1. Navigate to the asset
2. Click **Edit**
3. Update metadata
4. Save changes

### Versioning

Create new versions when data changes:

1. Navigate to the asset
2. Click **New Version**
3. Upload updated file
4. Add version comment

### Downloading

- Click **Download** for single files
- Use **Export** for metadata

## File Size Limits

Default limits vary by installation:

- Typical max: 2GB per file
- Contact admin for larger files
- Consider linking to external storage

## Next Steps

Learn about [Sharing & Permissions](sharing.md) to control access to your data.

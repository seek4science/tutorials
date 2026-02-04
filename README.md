# FAIRDOM-SEEK Tutorials

Tutorials for working with FAIRDOM-SEEK, built with Jupyter Book v2.

## View Online

Visit the tutorials at: https://seek4science.github.io/tutorials/

## Local Development

### Prerequisites

- Python 3.8+
- Node.js 18+
- pip

### Setup

```bash
# Create a virtual environment (optional but recommended)
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
pip install -r requirements.txt
```

### Build and preview locally

```bash
# Build and start dev server
jupyter-book build --html

# Or for local testing without base URL
BASE_URL="" jupyter-book build --html
```

The dev server starts automatically at http://localhost:3000 (or next available port).

### Adding new content

1. Create a new `.md` or `.ipynb` file in the appropriate directory
2. Add the file to `myst.yml` under the `toc` section
3. Build and preview locally
4. Commit and push to deploy

## Deployment

The book is automatically built and deployed to GitHub Pages when changes are pushed to the `main` branch.

### GitHub Pages Setup

1. Go to repository Settings > Pages
2. Under "Build and deployment", select "GitHub Actions" as the source
3. The workflow will automatically deploy on push to main

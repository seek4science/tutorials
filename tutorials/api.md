# UNDER DEVELOPMENT

# FAIRDOM-SEEK API Tutorial

This tutorial covers programmatic access to SEEK using the JSON API.

## Overview

SEEK provides a RESTful JSON API following the [JSON:API specification](https://jsonapi.org/). You can:

- Read and search assets
- Create and update content
- Manage permissions
- Automate workflows

## Authentication

### API Tokens

Generate an API token for authentication:

1. Log in to SEEK
2. Go to **My Profile** → **Actions** → **API Tokens**
3. Click **Generate New Token**
4. Copy and store securely

### Using Tokens

Include the token in request headers:

```bash
curl -H "Authorization: Token YOUR_API_TOKEN" \
     https://fairdomhub.org/people/current
```

## Basic Requests

### List Assets

```bash
# List all data files
curl https://fairdomhub.org/data_files

# List projects
curl https://fairdomhub.org/projects

# List with pagination
curl "https://fairdomhub.org/data_files?page[number]=1&page[size]=25"
```

### Get Single Asset

```bash
# Get a specific data file
curl https://fairdomhub.org/data_files/123
```

### Response Format

```json
{
  "data": {
    "id": "123",
    "type": "data_files",
    "attributes": {
      "title": "Experiment Results",
      "description": "Raw data from experiment 1",
      "created_at": "2024-01-15T10:30:00Z"
    },
    "relationships": {
      "projects": {
        "data": [{"id": "1", "type": "projects"}]
      }
    }
  }
}
```

## Python Examples

### Setup

```python
import requests

BASE_URL = "https://fairdomhub.org"
TOKEN = "your_api_token_here"

headers = {
    "Authorization": f"Token {TOKEN}",
    "Content-Type": "application/vnd.api+json",
    "Accept": "application/vnd.api+json"
}
```

### List Data Files

```python
def list_data_files(page=1, per_page=25):
    """List data files with pagination."""
    response = requests.get(
        f"{BASE_URL}/data_files",
        headers=headers,
        params={"page[number]": page, "page[size]": per_page}
    )
    response.raise_for_status()
    return response.json()

# Get first page of data files
data_files = list_data_files()
for item in data_files["data"]:
    print(f"{item['id']}: {item['attributes']['title']}")
```

### Search Assets

```python
def search_assets(query, asset_type=None):
    """Search for assets by keyword."""
    params = {"q": query}
    if asset_type:
        params["type"] = asset_type

    response = requests.get(
        f"{BASE_URL}/search",
        headers=headers,
        params=params
    )
    response.raise_for_status()
    return response.json()

# Search for cancer-related data
results = search_assets("cancer", asset_type="data_files")
```

### Create a Data File

```python
def create_data_file(title, description, project_id, file_path):
    """Create a new data file."""
    payload = {
        "data": {
            "type": "data_files",
            "attributes": {
                "title": title,
                "description": description,
                "content_blobs": [{
                    "original_filename": file_path.split("/")[-1],
                    "content_type": "application/octet-stream"
                }]
            },
            "relationships": {
                "projects": {
                    "data": [{"id": str(project_id), "type": "projects"}]
                }
            }
        }
    }

    response = requests.post(
        f"{BASE_URL}/data_files",
        headers=headers,
        json=payload
    )
    response.raise_for_status()
    return response.json()
```

### Upload File Content

```python
def upload_content(data_file_id, file_path):
    """Upload content to a data file."""
    # Get the content blob URL
    df = requests.get(
        f"{BASE_URL}/data_files/{data_file_id}",
        headers=headers
    ).json()

    blob_url = df["data"]["attributes"]["content_blobs"][0]["link"]

    # Upload the file
    with open(file_path, "rb") as f:
        response = requests.put(
            blob_url,
            headers={"Authorization": f"Token {TOKEN}"},
            data=f
        )
    response.raise_for_status()
    return response
```

## Common Operations

### Working with Projects

```python
# List your projects
def my_projects():
    me = requests.get(f"{BASE_URL}/people/current", headers=headers).json()
    return me["data"]["relationships"]["projects"]["data"]

# Get project details
def get_project(project_id):
    response = requests.get(
        f"{BASE_URL}/projects/{project_id}",
        headers=headers
    )
    return response.json()
```

### Managing Permissions

```python
def set_permissions(asset_type, asset_id, access_type="view", project_ids=None):
    """Update asset permissions."""
    policy = {
        "access": access_type,  # view, download, edit, manage
    }

    if project_ids:
        policy["permissions"] = [
            {"resource_type": "Project", "resource_id": pid, "access": access_type}
            for pid in project_ids
        ]

    payload = {
        "data": {
            "type": asset_type,
            "id": str(asset_id),
            "attributes": {
                "policy": policy
            }
        }
    }

    response = requests.patch(
        f"{BASE_URL}/{asset_type}/{asset_id}",
        headers=headers,
        json=payload
    )
    return response.json()
```

### Creating ISA Structure

```python
def create_investigation(title, description, project_id):
    """Create an investigation."""
    payload = {
        "data": {
            "type": "investigations",
            "attributes": {
                "title": title,
                "description": description
            },
            "relationships": {
                "projects": {
                    "data": [{"id": str(project_id), "type": "projects"}]
                }
            }
        }
    }
    return requests.post(
        f"{BASE_URL}/investigations",
        headers=headers,
        json=payload
    ).json()


def create_study(title, investigation_id):
    """Create a study within an investigation."""
    payload = {
        "data": {
            "type": "studies",
            "attributes": {"title": title},
            "relationships": {
                "investigation": {
                    "data": {"id": str(investigation_id), "type": "investigations"}
                }
            }
        }
    }
    return requests.post(
        f"{BASE_URL}/studies",
        headers=headers,
        json=payload
    ).json()
```

## Error Handling

```python
from requests.exceptions import HTTPError

def safe_request(func, *args, **kwargs):
    """Wrapper for API calls with error handling."""
    try:
        return func(*args, **kwargs)
    except HTTPError as e:
        if e.response.status_code == 401:
            print("Authentication failed. Check your API token.")
        elif e.response.status_code == 403:
            print("Permission denied.")
        elif e.response.status_code == 404:
            print("Resource not found.")
        elif e.response.status_code == 422:
            errors = e.response.json().get("errors", [])
            for error in errors:
                print(f"Validation error: {error.get('detail')}")
        else:
            print(f"API error: {e}")
        raise
```

## Rate Limiting

Be mindful of API usage:

```python
import time

def batch_operation(items, operation, delay=0.5):
    """Process items with rate limiting."""
    results = []
    for item in items:
        result = operation(item)
        results.append(result)
        time.sleep(delay)  # Respect rate limits
    return results
```

## API Reference

| Endpoint | Methods | Description |
|----------|---------|-------------|
| `/projects` | GET, POST | List/create projects |
| `/investigations` | GET, POST | List/create investigations |
| `/studies` | GET, POST | List/create studies |
| `/assays` | GET, POST | List/create assays |
| `/data_files` | GET, POST | List/create data files |
| `/models` | GET, POST | List/create models |
| `/sops` | GET, POST | List/create SOPs |
| `/samples` | GET, POST | List/create samples |
| `/people` | GET | List people |
| `/people/current` | GET | Current user info |
| `/search` | GET | Search assets |

## Next Steps

- Review the full [API documentation](https://docs.seek4science.org/tech/api/)
- Explore the [SEEK API documentation](https://docs.seek4science.org/tech/api/)
- Check the [JSON:API specification](https://jsonapi.org/)

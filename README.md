# Aljam3 MCP Server

An MCP (Model Context Protocol) server that provides access to the Aljam3 digital library API.

## Features

This MCP server provides tools to interact with the Aljam3 digital library:

### Available Tools

- **list_authors** - List authors with optional search functionality
- **get_author** - Get author details with optional books expansion
- **list_books** - List books with optional search functionality
- **get_book** - Get book details with optional files expansion
- **list_categories** - List all available categories
- **get_category** - Get category details with optional books expansion
- **list_libraries** - List all available libraries
- **get_library** - Get library details with optional books expansion
- **get_file** - Get file details with optional pages expansion
- **get_file_pages** - Get all pages of a specific file
- **search** - Search across all pages with filtering options

## Installation

1. Clone this repository:
```bash
git clone <repository-url>
cd aljam3-mcp
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

## Usage

### Running the Server

```bash
python server.py
```

### Configuration

The server connects to the Aljam3 API at `https://aljam3.com` by default. You can modify the `base_url` in the `Aljam3Client` class initialization if needed.

### Tool Examples

#### Search for authors
```python
# List authors with search query
await list_authors(q="محمد", limit=10)
```

#### Get book details with files
```python
# Get book by ID with file information
await get_book(book_id=123, expand_files=True)
```

#### Search content across all books
```python
# Search for specific content with filters
await search(
    query="الفقه الإسلامي",
    library=1,
    categories=[5, 6],
    limit=50
)
```

## API Coverage

This MCP server covers all endpoints from the Aljam3 OpenAPI specification:

- `/api/v1/authors` - Authors listing and search
- `/api/v1/authors/{id}` - Individual author details
- `/api/v1/books` - Books listing and search
- `/api/v1/books/{id}` - Individual book details
- `/api/v1/categories` - Categories listing
- `/api/v1/categories/{id}` - Individual category details
- `/api/v1/libraries` - Libraries listing
- `/api/v1/libraries/{id}` - Individual library details
- `/api/v1/files/{id}` - File details
- `/api/v1/files/{file_id}/pages` - File pages
- `/api/v1/search` - Global content search

## Development

### Project Structure

```
aljam3-mcp/
├── server.py          # Main MCP server implementation
├── requirements.txt   # Python dependencies
├── pyproject.toml    # Project configuration
├── swagger.yaml      # API specification
└── README.md        # This file
```

### Dependencies

- `mcp>=1.0.0` - Model Context Protocol framework
- `httpx>=0.25.0` - Modern HTTP client for API requests

## License

MIT License
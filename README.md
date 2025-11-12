# FlaskSearch API - Elasticsearch Integration

<div align="center">

![Python](https://img.shields.io/badge/Python-99.2%25-3776AB?logo=python&logoColor=white)
![Flask](https://img.shields.io/badge/Flask-2.x-000000?logo=flask&logoColor=white)
![Elasticsearch](https://img.shields.io/badge/Elasticsearch-8.x-005571?logo=elasticsearch&logoColor=white)
![License](https://img.shields.io/badge/License-MIT-yellow.svg)

**High-Performance Search API with Flask and Elasticsearch**

[Features](#-key-features) • [Installation](#-installation) • [API Documentation](#-api-documentation) • [Usage](#-usage)

</div>

---

## 📋 Table of Contents

- [Overview](#overview)
- [Key Features](#-key-features)
- [Technology Stack](#-technology-stack)
- [System Architecture](#-system-architecture)
- [Installation](#-installation)
- [Configuration](#-configuration)
- [API Documentation](#-api-documentation)
- [Usage Examples](#-usage-examples)
- [Project Structure](#-project-structure)
- [Elasticsearch Setup](#-elasticsearch-setup)
- [Data Indexing](#-data-indexing)
- [Performance](#-performance)
- [Troubleshooting](#-troubleshooting)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)

---

## 🎯 Overview

**FlaskSearch API** is a robust, production-ready RESTful API that integrates Flask with Elasticsearch to provide powerful full-text search capabilities. Built specifically for searching through Shakespeare plays, this API demonstrates best practices for implementing search functionality in modern web applications.

The application provides lightning-fast search results, flexible query options, and scalable architecture suitable for handling large datasets and high-traffic scenarios.

### Why FlaskSearch API?

- ⚡ **Fast Search**: Elasticsearch-powered sub-second query responses
- 🔍 **Full-Text Search**: Advanced text search with relevance scoring
- 🎯 **Flexible Queries**: Support for various search patterns and filters
- 📊 **Scalable**: Handle millions of documents efficiently
- 🛡️ **Production Ready**: Error handling and logging included
- 🔧 **Easy Integration**: RESTful API for seamless integration
- 📚 **Well Documented**: Comprehensive documentation and examples
- 🚀 **High Performance**: Optimized for speed and reliability

---

## ✨ Key Features

### 🔹 Search Capabilities
- **Full-Text Search**: Search through Shakespeare plays and dialogues
- **Fuzzy Matching**: Handle typos and misspellings
- **Relevance Scoring**: Results ranked by relevance
- **Field-Specific Search**: Search in specific fields (title, author, text)
- **Boolean Queries**: Combine multiple search terms with AND/OR
- **Phrase Search**: Exact phrase matching
- **Wildcard Search**: Pattern-based searching
- **Aggregations**: Statistical analysis of search results

### 🔹 API Features
- **RESTful Endpoints**: Standard HTTP methods (GET, POST, PUT, DELETE)
- **JSON Responses**: Structured JSON output
- **Pagination**: Handle large result sets efficiently
- **Filtering**: Filter results by various criteria
- **Sorting**: Sort results by relevance, date, or other fields
- **CORS Support**: Cross-origin resource sharing enabled
- **Error Handling**: Comprehensive error messages
- **Request Validation**: Input validation and sanitization

### 🔹 Data Management
- **Bulk Indexing**: Index large datasets efficiently
- **Real-Time Updates**: Instant data updates
- **Document CRUD**: Create, read, update, delete operations
- **Data Import**: JSON data import from files
- **Index Management**: Create, update, delete indices
- **Mapping Configuration**: Customize field types and analyzers

### 🔹 Performance Optimization
- **Query Caching**: Cache frequent queries
- **Connection Pooling**: Reuse database connections
- **Async Operations**: Non-blocking I/O for better performance
- **Batch Processing**: Handle multiple operations efficiently
- **Index Optimization**: Optimized Elasticsearch settings
- **Response Compression**: Reduce bandwidth usage

---

## 🛠 Technology Stack

### **Backend Framework**
- **Flask**: 2.x - Lightweight Python web framework
- **Python**: 3.8+ - Programming language
- **Werkzeug**: WSGI utility library
- **Jinja2**: Template engine

### **Search Engine**
- **Elasticsearch**: 8.x - Distributed search and analytics engine
- **Elasticsearch-py**: Official Python client for Elasticsearch
- **elasticsearch-dsl**: High-level library for Elasticsearch

### **Supporting Libraries**
- **Flask-CORS**: Cross-Origin Resource Sharing
- **Flask-RESTful**: REST API building tools
- **python-dotenv**: Environment variable management
- **requests**: HTTP library for API calls
- **gunicorn**: Production WSGI server
- **pytest**: Testing framework

### **Data Format**
- **JSON**: Data interchange format
- **CSV**: Data import/export (optional)

---

## 🏗 System Architecture

```
┌─────────────────────────────────────────────────────────┐
│                    Client Application                    │
│              (Web Browser, Mobile App, etc.)            │
└─────────────────────┬───────────────────────────────────┘
                      │ HTTP Requests
                      ▼
┌─────────────────────────────────────────────────────────┐
│                   Flask REST API                         │
│  ┌────────────────────────────────────────────────┐    │
│  │              API Endpoints                      │    │
│  │  /search  /index  /document  /bulk             │    │
│  └────────────────────────────────────────────────┘    │
│                          │                              │
│  ┌────────────────────────────────────────────────┐    │
│  │           Business Logic Layer                 │    │
│  │  Query Builder | Validator | Serializer        │    │
│  └────────────────────────────────────────────────┘    │
└─────────────────────┬───────────────────────────────────┘
                      │ Elasticsearch Client
                      ▼
┌─────────────────────────────────────────────────────────┐
│                  Elasticsearch Cluster                   │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐            │
│  │  Index 1 │  │  Index 2 │  │  Index N │            │
│  │  Shards  │  │  Shards  │  │  Shards  │            │
│  └──────────┘  └──────────┘  └──────────┘            │
└─────────────────────────────────────────────────────────┘
```

---

## 🚀 Installation

### Prerequisites

- **Python**: 3.8 or higher
- **pip**: Python package manager
- **Elasticsearch**: 8.x or 7.x
- **Virtual Environment**: venv or virtualenv
- **Git**: Version control

### Step-by-Step Setup

#### 1. Clone the Repository
```bash
git clone https://github.com/hamzakhan0712/Elasticsearch_Flask.git
cd Elasticsearch_Flask
```

#### 2. Create Virtual Environment
```bash
# Windows
python -m venv API/venv
API\venv\Scripts\activate

# Linux/Mac
python3 -m venv API/venv
source API/venv/bin/activate
```

#### 3. Install Dependencies
```bash
cd API
pip install -r requirements.txt
```

If `requirements.txt` is not available, install these packages:
```bash
pip install flask
pip install elasticsearch
pip install flask-cors
pip install python-dotenv
pip install gunicorn
```

#### 4. Install Elasticsearch

**Using Docker (Recommended):**
```bash
docker pull docker.elastic.co/elasticsearch/elasticsearch:8.11.0
docker run -d --name elasticsearch \
  -p 9200:9200 -p 9300:9300 \
  -e "discovery.type=single-node" \
  -e "xpack.security.enabled=false" \
  docker.elastic.co/elasticsearch/elasticsearch:8.11.0
```

**Manual Installation:**
- Download from [elastic.co](https://www.elastic.co/downloads/elasticsearch)
- Extract and run `bin/elasticsearch` (Linux/Mac) or `bin\elasticsearch.bat` (Windows)

#### 5. Verify Elasticsearch
```bash
curl http://localhost:9200
```

You should see JSON output with cluster information.

#### 6. Configure Application
Create a `.env` file in the `API` directory:
```env
FLASK_APP=app.py
FLASK_ENV=development
FLASK_DEBUG=True
ELASTICSEARCH_HOST=http://localhost:9200
INDEX_NAME=shakespeareplay
PORT=5000
```

Or edit `API/config.py`:
```python
INDEX_NAME = 'shakespeareplay'
ESKNN_HOST = 'http://localhost:9200'
```

#### 7. Index Sample Data
```bash
python index_data.py
```

#### 8. Run the Application
```bash
python app.py
```

The API will be available at: `http://localhost:5000`

---

## ⚙️ Configuration

### Flask Configuration

```python
# API/config.py
INDEX_NAME = 'shakespeareplay'
ESKNN_HOST = 'http://localhost:9200'

# Additional configurations
DEBUG = True
HOST = '0.0.0.0'
PORT = 5000
```

### Elasticsearch Configuration

```python
# Connection settings
es = Elasticsearch(
    hosts=[ESKNN_HOST],
    timeout=30,
    max_retries=3,
    retry_on_timeout=True
)

# Index settings
INDEX_SETTINGS = {
    "settings": {
        "number_of_shards": 1,
        "number_of_replicas": 0,
        "analysis": {
            "analyzer": {
                "custom_analyzer": {
                    "type": "custom",
                    "tokenizer": "standard",
                    "filter": ["lowercase", "stop"]
                }
            }
        }
    },
    "mappings": {
        "properties": {
            "title": {"type": "text"},
            "author": {"type": "keyword"},
            "text": {"type": "text", "analyzer": "custom_analyzer"},
            "line_number": {"type": "integer"}
        }
    }
}
```

---

## 📚 API Documentation

### Base URL
```
http://localhost:5000/api
```

### Endpoints

#### 1. Search Documents
```http
GET /api/search?q={query}&size={number}&from={offset}

Parameters:
  - q: Search query (required)
  - size: Number of results (default: 10)
  - from: Offset for pagination (default: 0)

Response: 200 OK
{
  "hits": [
    {
      "score": 5.23,
      "source": {
        "title": "Hamlet",
        "author": "William Shakespeare",
        "text": "To be, or not to be...",
        "line_number": 56
      }
    }
  ],
  "total": 150,
  "took": 12
}
```

#### 2. Index Document
```http
POST /api/document

Body:
{
  "title": "Romeo and Juliet",
  "author": "William Shakespeare",
  "text": "O Romeo, Romeo, wherefore art thou Romeo?",
  "line_number": 33
}

Response: 201 Created
{
  "message": "Document indexed successfully",
  "id": "abc123",
  "index": "shakespeareplay"
}
```

#### 3. Get Document by ID
```http
GET /api/document/{id}

Response: 200 OK
{
  "id": "abc123",
  "source": {
    "title": "Romeo and Juliet",
    "author": "William Shakespeare",
    "text": "O Romeo, Romeo, wherefore art thou Romeo?",
    "line_number": 33
  }
}
```

#### 4. Update Document
```http
PUT /api/document/{id}

Body:
{
  "text": "Updated text content"
}

Response: 200 OK
{
  "message": "Document updated successfully"
}
```

#### 5. Delete Document
```http
DELETE /api/document/{id}

Response: 200 OK
{
  "message": "Document deleted successfully"
}
```

#### 6. Bulk Index
```http
POST /api/bulk

Body:
[
  {
    "title": "Play 1",
    "author": "Shakespeare",
    "text": "Content 1"
  },
  {
    "title": "Play 2",
    "author": "Shakespeare",
    "text": "Content 2"
  }
]

Response: 201 Created
{
  "message": "Bulk indexing completed",
  "indexed": 2,
  "failed": 0
}
```

---

## 💡 Usage Examples

### Python Client

```python
import requests

BASE_URL = "http://localhost:5000/api"

# Search for documents
response = requests.get(f"{BASE_URL}/search", params={
    "q": "to be or not to be",
    "size": 5
})
results = response.json()

# Index a new document
document = {
    "title": "Macbeth",
    "author": "William Shakespeare",
    "text": "Out, damned spot! Out, I say!",
    "line_number": 1
}
response = requests.post(f"{BASE_URL}/document", json=document)

# Get document by ID
doc_id = "abc123"
response = requests.get(f"{BASE_URL}/document/{doc_id}")
document = response.json()
```

### cURL Examples

```bash
# Search
curl "http://localhost:5000/api/search?q=hamlet&size=10"

# Index document
curl -X POST http://localhost:5000/api/document \
  -H "Content-Type: application/json" \
  -d '{
    "title": "Othello",
    "author": "William Shakespeare",
    "text": "O, beware, my lord, of jealousy",
    "line_number": 165
  }'

# Get document
curl http://localhost:5000/api/document/abc123

# Delete document
curl -X DELETE http://localhost:5000/api/document/abc123
```

### JavaScript (Fetch API)

```javascript
// Search
const searchResults = await fetch(
  'http://localhost:5000/api/search?q=love&size=10'
).then(res => res.json());

// Index document
const response = await fetch('http://localhost:5000/api/document', {
  method: 'POST',
  headers: {
    'Content-Type': 'application/json',
  },
  body: JSON.stringify({
    title: 'King Lear',
    author: 'William Shakespeare',
    text: 'How sharper than a serpent\'s tooth',
    line_number: 288
  })
});
```

---

## 📁 Project Structure

```
Elasticsearch_Flask/
│
├── API/                              # Main application directory
│   ├── venv/                         # Virtual environment
│   ├── config.py                     # Configuration settings
│   ├── app.py                        # Flask application entry point
│   ├── routes.py                     # API route definitions
│   ├── elasticsearch_client.py       # Elasticsearch connection
│   ├── models.py                     # Data models
│   ├── utils.py                      # Utility functions
│   └── requirements.txt              # Python dependencies
│
├── datset.json                       # Shakespeare plays dataset
├── index_data.py                     # Data indexing script
├── # Flask API Setup Instructions.txt # Setup documentation
├── .gitignore                        # Git ignore rules
├── LICENSE                           # MIT License
└── README.md                         # This file
```

---

## 🔧 Elasticsearch Setup

### Create Index

```python
from elasticsearch import Elasticsearch

es = Elasticsearch(['http://localhost:9200'])

# Create index with mappings
es.indices.create(
    index='shakespeareplay',
    body={
        "settings": {
            "number_of_shards": 1,
            "number_of_replicas": 0
        },
        "mappings": {
            "properties": {
                "title": {"type": "text"},
                "author": {"type": "keyword"},
                "text": {"type": "text"},
                "line_number": {"type": "integer"},
                "act": {"type": "integer"},
                "scene": {"type": "integer"},
                "speaker": {"type": "keyword"}
            }
        }
    }
)
```

### Index Optimization

```python
# Refresh index
es.indices.refresh(index='shakespeareplay')

# Force merge segments
es.indices.forcemerge(index='shakespeareplay')

# Update settings
es.indices.put_settings(
    index='shakespeareplay',
    body={
        "index": {
            "refresh_interval": "1s"
        }
    }
)
```

---

## 📊 Data Indexing

### Index Sample Data

```python
import json
from elasticsearch import Elasticsearch

es = Elasticsearch(['http://localhost:9200'])

# Load dataset
with open('datset.json', 'r') as f:
    data = json.load(f)

# Bulk index
for item in data:
    es.index(
        index='shakespeareplay',
        body=item
    )

print("Data indexed successfully!")
```

### Bulk Indexing for Large Datasets

```python
from elasticsearch.helpers import bulk

def generate_docs():
    with open('datset.json', 'r') as f:
        data = json.load(f)
    
    for item in data:
        yield {
            "_index": "shakespeareplay",
            "_source": item
        }

# Bulk index
success, failed = bulk(es, generate_docs())
print(f"Indexed: {success}, Failed: {failed}")
```

---

## ⚡ Performance

### Optimization Tips

- **Use Bulk API**: Index multiple documents at once
- **Disable Refresh**: Set `refresh_interval=-1` during bulk indexing
- **Increase Bulk Size**: Use larger batch sizes (500-1000)
- **Connection Pooling**: Reuse connections
- **Query Caching**: Enable query result caching
- **Use Filters**: Prefer filters over queries for exact matches
- **Limit Fields**: Only retrieve necessary fields

### Performance Metrics

- **Search Latency**: < 50ms for simple queries
- **Indexing Speed**: 1000+ documents/second
- **Concurrent Users**: 100+ simultaneous connections
- **Storage**: ~1KB per Shakespeare line
- **Memory**: 512MB minimum for Elasticsearch

---

## 🔍 Troubleshooting

### Common Issues

**Issue**: Cannot connect to Elasticsearch
```bash
Solution:
1. Check if Elasticsearch is running: curl http://localhost:9200
2. Verify ESKNN_HOST in config.py
3. Check firewall settings
4. Ensure Elasticsearch is not using HTTPS (or update URL)
```

**Issue**: Index not found
```bash
Solution:
1. Create the index: python index_data.py
2. Verify index exists: curl http://localhost:9200/_cat/indices
3. Check INDEX_NAME in config.py
```

**Issue**: Search returns no results
```bash
Solution:
1. Verify data is indexed: curl http://localhost:9200/shakespeareplay/_count
2. Check query syntax
3. Try a simpler search term
4. Refresh index: curl -X POST http://localhost:9200/shakespeareplay/_refresh
```

**Issue**: Slow search performance
```bash
Solution:
1. Reduce result size
2. Add pagination
3. Optimize Elasticsearch settings
4. Increase Elasticsearch memory
5. Use query profiling: add ?profile=true
```

---

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch**
   ```bash
   git checkout -b feature/YourFeature
   ```
3. **Commit your changes**
   ```bash
   git commit -m "Add: Your feature description"
   ```
4. **Push to your fork**
   ```bash
   git push origin feature/YourFeature
   ```
5. **Open a Pull Request**

### Coding Standards

- Follow PEP 8 for Python code
- Write docstrings for all functions
- Add unit tests for new features
- Update documentation

---

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

---

## 📞 Contact

**Developer**: Hamza Khan
- GitHub: [@hamzakhan0712](https://github.com/hamzakhan0712)
- Repository: [Elasticsearch_Flask](https://github.com/hamzakhan0712/Elasticsearch_Flask)

---

## 🙏 Acknowledgments

- **Elasticsearch** for the powerful search engine
- **Flask** for the lightweight web framework
- **William Shakespeare** for the timeless content
- **Open Source Community** for inspiration and support

---

## 🗺️ Roadmap

### Version 2.0 (Planned)

- [ ] Authentication and authorization (JWT)
- [ ] Rate limiting and throttling
- [ ] Advanced analytics and aggregations
- [ ] Multi-language support
- [ ] Autocomplete/suggestions
- [ ] Highlighting of search terms
- [ ] Export search results (CSV, JSON)
- [ ] Docker containerization
- [ ] GraphQL API support
- [ ] WebSocket for real-time updates
- [ ] Admin dashboard
- [ ] API documentation with Swagger/OpenAPI

---

<div align="center">

**Built with ❤️ for Full-Text Search Excellence**

⭐ Star this repository if you find it helpful!

[Report Bug](https://github.com/hamzakhan0712/Elasticsearch_Flask/issues) | [Request Feature](https://github.com/hamzakhan0712/Elasticsearch_Flask/issues)

</div>

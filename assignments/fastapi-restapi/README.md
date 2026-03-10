# 📘 Assignment: Building REST APIs with FastAPI

## 🎯 Objective

Learn to build, validate, document, and test RESTful APIs using the FastAPI framework and Pydantic models. Implement CRUD endpoints, input validation, automatic OpenAPI documentation, and basic tests.

## 📝 Tasks

### 🛠️ Basic CRUD API

#### Description
Create a simple REST API for a `books` resource that supports creating, reading, updating, and deleting entries. Use FastAPI and Pydantic for request/response modelling and run the app with `uvicorn`.

#### Requirements
Completed program should:

- Provide endpoints:
  - `GET /books` — return list of books
  - `GET /books/{id}` — return a single book by id
  - `POST /books` — create a new book
  - `PUT /books/{id}` — update an existing book
  - `DELETE /books/{id}` — delete a book
- Use a Pydantic model for request and response validation (e.g., `Book` with `id`, `title`, `author`, `year`)
- Use an in-memory store (list/dict) for data (persistence not required)
- Return appropriate HTTP status codes (`201` for create, `404` when not found, etc.)
- Include example requests and expected responses

Example Pydantic model and minimal endpoint snippet:
```python
from pydantic import BaseModel
from typing import Optional

class Book(BaseModel):
    id: int
    title: str
    author: str
    year: Optional[int] = None
```

Example `curl` requests:
```bash
# Create a book
curl -X POST http://localhost:8000/books -H "Content-Type: application/json" \
  -d '{"id":1,"title":"Clean Code","author":"R. Martin","year":2008}'

# Get list
curl http://localhost:8000/books

# Get single
curl http://localhost:8000/books/1
```

Example response for `GET /books/1`:
```json
{
  "id": 1,
  "title": "Clean Code",
  "author": "R. Martin",
  "year": 2008
}
```

### 🛠️ Validation, Docs, and Testing

#### Description
Enhance the API with input validation, clear error handling, dependency usage, automatic OpenAPI documentation, and a small test suite using FastAPI's TestClient and `pytest`.

#### Requirements
Completed program should:

- Use request and response models to enforce input/response shapes and add field validation (e.g., title length, year range)
- Return structured error responses for invalid input with appropriate status codes
- Expose interactive API docs at `/docs` (OpenAPI) and a machine-readable schema at `/openapi.json`
- Demonstrate dependency injection for a simple service (e.g., a function that returns a data store)
- Include at least two automated tests using `pytest` and FastAPI's `TestClient`:
  - Test creating a book and retrieving it
  - Test handling of an invalid request (e.g., missing required field or invalid type)

Example test using `TestClient`:
```python
from fastapi.testclient import TestClient
from myapi import app  # your FastAPI app

client = TestClient(app)

def test_create_and_get_book():
    payload = {"id":2,"title":"The Pragmatic Programmer","author":"A. Hunt"}
    r = client.post("/books", json=payload)
    assert r.status_code == 201
    assert r.json()["title"] == "The Pragmatic Programmer"

def test_invalid_book_missing_title():
    payload = {"id":3,"author":"Unknown"}
    r = client.post("/books", json=payload)
    assert r.status_code == 422
```

### 🛠️ Bonus — Async Endpoints and Deployment (Optional)

#### Description
Make endpoints asynchronous and provide a simple `Dockerfile` to containerize the app. Optionally add a `requirements.txt` and a basic CI workflow to run tests.

#### Requirements
Completed program should:

- Use `async def` for at least the main endpoints
- Include a `Dockerfile` that runs the app with `uvicorn`
- Provide a `requirements.txt` listing dependencies (e.g., `fastapi`, `uvicorn`, `pytest`)
- (Optional) Add a basic GitHub Actions workflow to run `pytest` on push

Example Dockerfile snippet:
```dockerfile
FROM python:3.11-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
CMD ["uvicorn", "myapi:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

Good luck — include clear README instructions for how to run the app locally (e.g., `uvicorn myapi:app --reload`) and how to run tests (`pytest`).

# Routes and HTTP Methods

## Client-Server Model

### Overview
- **Client**: User's device that runs the frontend (UI and user interaction)
- **Server**: Powerful computer that runs backend code and handles data
- **Communication**: Clients send requests to servers, servers process and return responses

### How It Works
1. Client initiates request
2. DNS translates domain names to IP addresses
3. Server processes request
4. Server sends response back to client

## HTTP Methods & CRUD Operations

### CRUD Operations
- **C**reate: Add new data (POST)
- **R**etrieve: Get existing data (GET)
- **U**pdate: Modify existing data (PUT/PATCH)
- **D**elete: Remove data (DELETE)

### Common HTTP Methods
- `GET`: Retrieve data
- `POST`: Create new data
- `PUT/PATCH`: Update existing data
- `DELETE`: Remove data

## Response Codes

### Success Codes (2xx)
- `200`: OK - Request succeeded
- `201`: Created - New resource created
- `204`: No Content - Request succeeded but no content returned

### Error Codes
- `400`: Bad Request - Invalid request
- `404`: Not Found - Resource doesn't exist
- `500`: Internal Server Error - Server-side error

## Flask Routes Example

### Basic Route Structure
```python
@app.route("/path/", methods=["GET"])
def function_name():
    # Handle request
    return response, status_code
```

### Common Route Patterns
1. **Get All Items**
   ```python
   @app.route("/items/")
   def get_items():
       return json.dumps(items), 200
   ```

2. **Get Single Item**
   ```python
   @app.route("/items/<int:id>/")
   def get_item(id):
       item = items.get(id)
       if not item:
           return json.dumps({"error": "Not found"}), 404
       return json.dumps(item), 200
   ```

3. **Create Item**
   ```python
   @app.route("/items/", methods=["POST"])
   def create_item():
       body = json.loads(request.data)
       # Create new item
       return json.dumps(new_item), 201
   ```

4. **Update Item**
   ```python
   @app.route("/items/<int:id>/", methods=["PUT"])
   def update_item(id):
       item = items.get(id)
       if not item:
           return json.dumps({"error": "Not found"}), 404
       # Update item
       return json.dumps(item), 200
   ```

5. **Delete Item**
   ```python
   @app.route("/items/<int:id>/", methods=["DELETE"])
   def delete_item(id):
       item = items.get(id)
       if not item:
           return json.dumps({"error": "Not found"}), 404
       # Delete item
       return json.dumps(item), 200
   ```

## Development Setup

### Virtual Environment
```bash
# Create virtual environment
python3 -m venv venv

# Activate virtual environment
source venv/bin/activate

# Install dependencies
pip3 install -r requirements.txt
```

### Running the Application
```bash
# Run Flask app
python3 app.py
```

## Best Practices

### Documentation
- Use docstrings to document functions
- Include parameter descriptions
- Document return values and status codes

### Error Handling
- Always check if resources exist
- Return appropriate status codes
- Provide meaningful error messages

### Testing
- Use Postman for API testing
- Test all CRUD operations
- Verify error handling
- Check response formats

## Common Patterns

### JSON Response Format
```python
{
    "data": [...],  # For list responses
    "error": "...", # For error responses
    "message": "..." # For success messages
}
```

### URL Structure
- Use plural nouns for resources
- Include trailing slashes
- Use consistent URL patterns
- Include version numbers if needed (e.g., `/v1/items/`) 
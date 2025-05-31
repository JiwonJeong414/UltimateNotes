# Demo Application: Task Management API

This demo application demonstrates a simple task management API using Flask. It shows basic CRUD operations and best practices for building RESTful APIs.

## Project Structure
```
.
├── routes.py        # Main Flask application
└── requirements.txt # Dependencies
```

## Data Structure
```python
# Dictionary to store tasks - acts as our simple database
tasks = {
    0: {"id": 0, "description": "laundry", "done": False},
    1: {"id": 1, "description": "homework", "done": False},
}
```

## API Endpoints

### 1. Get All Tasks
```python
@app.route("/tasks/")
def get_tasks():
    """Lists all tasks."""
    res = {"tasks": list(tasks.values())}
    return json.dumps(res), 200
```

### 2. Create Task
```python
@app.route("/tasks/", methods=["POST"])
def create_task():
    """Creates new task."""
    global task_id_counter
    body = json.loads(request.data)
    description = body.get("description")
    task = {
        "id": task_id_counter,
        "description": description,
        "done": False
    }
    tasks[task_id_counter] = task
    task_id_counter += 1
    return json.dumps(task), 201
```

### 3. Get Single Task
```python
@app.route("/tasks/<int:task_id>/")
def get_task(task_id):
    """Gets single task."""
    task = tasks.get(task_id)
    if not task:
        return json.dumps({"error": "Task not found"}), 404
    return json.dumps(task), 200
```

### 4. Update Task
```python
@app.route("/tasks/<int:task_id>/", methods=["POST"])
def update_task(task_id):
    """Updates existing task."""
    task = tasks.get(task_id)
    if not task:
        return json.dumps({"error": "Task not found"}), 404
    body = json.loads(request.data)
    task["description"] = body["description"]
    task["done"] = body["done"]
    return json.dumps(task), 200
```

### 5. Delete Task
```python
@app.route("/tasks/<int:task_id>/", methods=["DELETE"])
def delete_task(task_id):
    """Removes task."""
    task = tasks.get(task_id)
    if not task:
        return json.dumps({"error": "Task not found"}), 404
    del tasks[task_id]
    return json.dumps(task), 200
```

## Key Features Demonstrated

1. **Basic CRUD Operations**
   - Create: POST /tasks/
   - Read: GET /tasks/ and GET /tasks/<id>/
   - Update: POST /tasks/<id>/
   - Delete: DELETE /tasks/<id>/

2. **Error Handling**
   - 404 for non-existent tasks
   - Proper error messages in JSON format

3. **Data Management**
   - Using dictionary as simple database
   - Auto-incrementing IDs
   - Task status tracking

4. **Code Organization**
   - Clear route structure
   - Descriptive function names
   - Docstrings for documentation

## Best Practices Shown

1. **Route Organization**
   - Consistent URL patterns
   - Proper HTTP methods
   - Clear endpoint naming

2. **Error Handling**
   - Resource existence checks
   - Appropriate status codes
   - Informative error messages

3. **Response Formatting**
   - Consistent JSON structure
   - Proper status codes
   - Clear success/error responses

4. **Code Documentation**
   - Function docstrings
   - Clear variable names
   - Code comments where needed 
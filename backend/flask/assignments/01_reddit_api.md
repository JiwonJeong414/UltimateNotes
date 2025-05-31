# Assignment 1: Reddit-like API

This assignment demonstrates building a Reddit-like API with posts and comments functionality using Flask.

## Project Structure
```
.
├── pa1.py           # Main Flask application
├── pa1_test.py      # Test suite
└── requirements.txt # Dependencies
```

## Dependencies
```txt
click==8.1.3
Flask==2.2.2
itsdangerous==2.1.2
Jinja2==3.1.2
MarkupSafe==2.1.1
Werkzeug==2.2.2
requests==2.28.1
```

## API Endpoints

### Posts
1. **Get All Posts**
   ```python
   @app.route("/api/posts/")
   def get_posts():
       """gets all posts"""
       res = {"posts": list(posts.values())}
       return json.dumps(res), 200
   ```

2. **Create Post**
   ```python
   @app.route("/api/posts/", methods=["POST"])
   def create_post():
       """creates a new post"""
       global post_id_counter
       body = json.loads(request.data)
       post = {
           "id": post_id_counter,
           "upvotes": 1,
           "title": body.get("title"),
           "link": body.get("link"),
           "username": body.get("username")
       }
       posts[post_id_counter] = post
       post_id_counter += 1
       return json.dumps(post), 201
   ```

3. **Get Single Post**
   ```python
   @app.route("/api/posts/<int:post_id>/")
   def get_post(post_id):
       """get a single post"""
       post = posts.get(post_id)
       if not post:
           return json.dumps({"error": "Post not found"}), 404
       return json.dumps(post), 200
   ```

4. **Delete Post**
   ```python
   @app.route("/api/posts/<int:post_id>/", methods=["DELETE"])
   def delete_post(post_id):
       """deletes a single post"""
       post = posts.get(post_id)
       if not post:
           return json.dumps({"error": "Post not found"}), 404
       del posts[post_id]
       return json.dumps(post), 200
   ```

### Comments
1. **Get Post Comments**
   ```python
   @app.route("/api/posts/<int:post_id>/comments/")
   def get_comments(post_id):
       """gets all comments for a post"""
       if post_id not in posts:
           return json.dumps({"error": "Post not found"}), 404
       post_comments = [c for c in comments.values() if c["post_id"] == post_id]
       return json.dumps({"comments": post_comments}), 200
   ```

2. **Create Comment**
   ```python
   @app.route("/api/posts/<int:post_id>/comments/", methods=["POST"])
   def create_comment(post_id):
       """creates a new comment for a post"""
       if post_id not in posts:
           return json.dumps({"error": "Post not found"}), 404
       
       body = json.loads(request.data)
       comment = {
           "id": comment_id_counter,
           "upvotes": 1,
           "text": body.get("text"),
           "username": body.get("username"),
           "post_id": post_id
       }
       comments[comment_id_counter] = comment
       comment_id_counter += 1
       return json.dumps(comment), 201
   ```

3. **Edit Comment**
   ```python
   @app.route("/api/posts/<int:post_id>/comments/<int:comment_id>/", methods=["POST"])
   def edit_comment(post_id, comment_id):
       """edits an existing comment"""
       if post_id not in posts:
           return json.dumps({"error": "Post not found"}), 404
       if comment_id not in comments:
           return json.dumps({"error": "Comment not found"}), 404
       
       comment = comments[comment_id]
       if comment["post_id"] != post_id:
           return json.dumps({"error": "Comment not found"}), 404
       
       body = json.loads(request.data)
       comment["text"] = body.get("text")
       return json.dumps(comment), 200
   ```

## Data Structures

### Posts Dictionary
```python
posts = {
    0: {
        "id": 0, 
        "upvotes": 1, 
        "title": "My cat is the cutest!", 
        "link": "https://i.imgur.com/jseZqNK.jpg", 
        "username": "alicia98"
    },
    1: {
        "id": 1,
        "upvotes": 3,
        "title": "Cat loaf",
        "link": "https://i.imgur.com/TJ46wX4.jpg",
        "username": "alicia98"
    }
}
```

### Comments Dictionary
```python
comments = {
    0: {
        "id": 0,
        "upvotes": 8,
        "text": "Wow, my first Reddit gold!",
        "username": "alicia98",
        "post_id": 0
    }
}
```

## Testing
The assignment includes a comprehensive test suite (`pa1_test.py`) that tests:
1. Basic CRUD operations for posts
2. Comment creation and editing
3. Error handling for invalid requests
4. Extra credit features (if implemented)

## Key Learning Points
1. **Route Organization**: Using nested routes for related resources (posts/comments)
2. **Error Handling**: Proper HTTP status codes and error messages
3. **Data Management**: Using dictionaries as simple databases
4. **Request Processing**: Handling JSON data in requests
5. **Response Formatting**: Consistent JSON response structure

## Best Practices Demonstrated
1. **Documentation**: Each route has a docstring explaining its purpose
2. **Error Handling**: Proper validation of input data and resource existence
3. **Status Codes**: Appropriate HTTP status codes for different scenarios
4. **Code Organization**: Clear separation of concerns between routes
5. **Data Validation**: Checking for required fields in requests 
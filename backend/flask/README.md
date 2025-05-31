# Flask Documentation

This directory contains comprehensive documentation for learning Flask, including lectures, assignments, and examples.

## Directory Structure

```
flask/
├── lectures/           # Lecture materials and examples
│   ├── 01_routes.md   # Routes and HTTP methods
│   └── 02_demo.md     # Demo application walkthrough
└── assignments/        # Assignment specifications and examples
    ├── 01_reddit_api.md
    └── ...            # Future assignments
```

## Learning Path

1. **Routes and HTTP Methods** (`lectures/01_routes.md`)
   - Client-server model
   - HTTP methods and CRUD operations
   - Response codes
   - Route patterns
   - Best practices

2. **Demo Application** (`lectures/02_demo.md`)
   - Task management API
   - Basic CRUD operations
   - Error handling
   - Response formatting

3. **Assignments**
   - **Reddit-like API** (`assignments/01_reddit_api.md`)
     - Posts and comments functionality
     - Nested routes
     - Data management
     - Testing

## Getting Started

1. Set up your development environment:
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```

2. Start with the routes lecture to understand basic concepts
3. Review the demo application for practical examples
4. Complete the assignments to apply your knowledge

## Best Practices

1. **Code Organization**
   - Use clear route patterns
   - Separate concerns
   - Document your code

2. **Error Handling**
   - Validate input data
   - Use appropriate status codes
   - Provide meaningful error messages

3. **Testing**
   - Write comprehensive tests
   - Test edge cases
   - Verify error handling

4. **Documentation**
   - Document API endpoints
   - Include example requests/responses
   - Explain complex logic

## Additional Resources

- [Flask Documentation](https://flask.palletsprojects.com/)
- [HTTP Status Codes](https://developer.mozilla.org/en-US/docs/Web/HTTP/Status)
- [REST API Best Practices](https://restfulapi.net/) 
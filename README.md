# FastAPI JSON API

This is a FastAPI application that interacts with external APIs and formats JSON data.

## Objectives:
- Familiarize and identify JSON as a primary data format for API development
- Parse JSON strings and traverse data in the JSON string using Python
- Convert Python data structures into a valid JSON format
- Integrate and manipulate data from external APIs

## Features

- Fetch posts and comments from an external API
- Format and structure API responses
- Return data in JSON format
- Provide an endpoint that combines posts with their respective comments

## Installation

Ensure you have Python installed. Then, install FastAPI, Uvicorn, and Requests:

```bash
pip install fastapi uvicorn requests
```

## Running the API

To start the FastAPI server, run the following command:

```bash
uvicorn main:app --reload
```

This will start the server, and the API will be available at `http://127.0.0.1:8000`.

## API Endpoints

### Fetch Posts

Retrieves all posts or a specific post by ID.

```
GET /posts/
GET /posts/?postId={postId}
```

#### Example Response:
```json
[
  {
    "userId": 1,
    "id": 1,
    "title": "Sample Post",
    "body": "This is a post body."
  }
]
```

### Fetch Comments

Retrieves all comments or comments for a specific post.

```
GET /comments/
GET /comments/?postId={postId}
```

#### Example Response:
```json
[
  {
    "postId": 1,
    "id": 1,
    "name": "User Comment",
    "email": "user@example.com",
    "body": "This is a comment."
  }
]
```

### Fetch Formatted Posts by User

Retrieves all posts for a given user, formatted with only titles and bodies.

```
GET /formatted_posts/{userID}
```

#### Example Response:
```json
{
  "userID": 1,
  "posts": [
    {
      "post_title": "Sample Post",
      "post_body": "This is a post body."
    }
  ]
}
```

### Fetch Formatted Comments by Post

Retrieves all comments for a given post, formatted with commenter details.

```
GET /formatted_comment/{postID}
```

#### Example Response:
```json
{
  "post_id": 1,
  "comments": [
    {
      "commenter_email": "user@example.com",
      "commenter_name": "User Comment",
      "comment": "This is a comment."
    }
  ]
}
```

### Fetch Detailed Posts with Comments by User

Retrieves all posts of a user and includes all comments for each post.

```
GET /detailed_post/{userID}
```

#### Example Response:
```json
{
  "userID": 1,
  "posts": [
    {
      "post_id": 1,
      "post_title": "Sample Post",
      "post_body": "This is a post body.",
      "comments": [
        {
          "commenter_email": "user@example.com",
          "commenter_name": "User Comment",
          "comment": "This is a comment."
        }
      ]
    }
  ]
}
```

## API Documentation

FastAPI automatically generates interactive API documentation:
- Swagger UI: [http://127.0.0.1:8000/docs](http://127.0.0.1:8000/docs)
- ReDoc: [http://127.0.0.1:8000/redoc](http://127.0.0.1:8000/redoc)

## License

This project is licensed under the MIT License.


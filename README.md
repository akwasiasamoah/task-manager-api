# Task Manager API Documentation

## Overview

The Task Manager API is a simple Node.js application that provides CRUD (Create, Read, Update, Delete) functionality for managing tasks. The API is built using Express.js and MongoDB, with error handling and asynchronous operations wrapped in custom middleware.

## Features

- Create a task
- Retrieve all tasks
- Retrieve a single task by ID
- Update a task by ID
- Delete a task by ID

## Technologies Used

- **Node.js**: JavaScript runtime
- **Express.js**: Web framework for building RESTful APIs
- **MongoDB**: NoSQL database
- **Mongoose**: ODM library for MongoDB
- **Custom Error Handling**: For better error management
- **Async Wrapper Middleware**: To streamline async/await usage

## Installation and Setup

1. Clone the repository:

   ```bash
   git clone <repository-url>
   cd <repository-name>
   ```

2. Install dependencies:

   ```bash
   npm install
   ```

3. Set up the environment variables:
   Create a `.env` file in the root directory and configure the following:

   ```env
   MONGO_URI=<your-mongodb-connection-string>
   PORT=5000
   ```

4. Start the application:
   ```bash
   npm start
   ```

## API Endpoints

### Base URL

```
http://localhost:5000/api/v1/tasks
```

### Endpoints

#### 1. Get All Tasks

- **URL**: `/`
- **Method**: `GET`
- **Description**: Retrieve all tasks from the database.
- **Response**:
  ```json
  {
    "success": true,
    "data": {
      "tasks": [
        {
          "_id": "64bff3a4cd77db09c97a00ec",
          "name": "Sample Task",
          "completed": false,
          "__v": 0
        }
      ],
      "nbhits": 1
    }
  }
  ```

#### 2. Create a Task

- **URL**: `/`
- **Method**: `POST`
- **Description**: Create a new task.
- **Request Body**:
  ```json
  {
    "name": "test1",
    "completed": true
  }
  ```
- **Response**:
  ```json
  {
    "name": "test1",
    "completed": true
  }
  ```

#### 3. Get a Task by ID

- **URL**: `/:id`
- **Method**: `GET`
- **Description**: Retrieve a task by its ID.
- **Response**:
  ```json
  {
    "task": {
      "_id": "64bff3a4cd77db09c97a00ec",
      "name": "Sample Task",
      "completed": false,
      "__v": 0
    }
  }
  ```

#### 4. Update a Task by ID

- **URL**: `/:id`
- **Method**: `PATCH`
- **Description**: Update a task's details by its ID.
- **Request Body**:
  ```json
  {
    "name": "Updated Task",
    "completed": true
  }
  ```
- **Response**:
  ```json
  {
    "task": {
      "_id": "64bff3a4cd77db09c97a00ec",
      "name": "Updated Task",
      "completed": true,
      "__v": 0
    }
  }
  ```

#### 5. Delete a Task by ID

- **URL**: `/:id`
- **Method**: `DELETE`
- **Description**: Delete a task by its ID.
- **Response**:
  ```json
  {
    "task": {
      "_id": "64bff3a4cd77db09c97a00ec",
      "name": "Sample Task",
      "completed": false,
      "__v": 0
    }
  }
  ```

## Error Handling

Errors are handled using a custom error-handling middleware.

### Custom Error Structure

```json
{
  "message": "<error-message>",
  "statusCode": <error-status-code>
}
```

### Example Error Response

- **Status Code**: `404`
- **Response**:
  ```json
  {
    "message": "No task with id: <taskID>",
    "statusCode": 404
  }
  ```

## License

This project is licensed under the MIT License.

---

Feel free to modify this documentation as per your project needs!

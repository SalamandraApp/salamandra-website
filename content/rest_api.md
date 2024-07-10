---
title: ""
---

# Resources
## Users
### GET /users/{user_id}
_(Authenticated)_ Return user with corresponding id
- Path Parameters
	- `user_id` UUID format
- Response
	- `application/json`
	- 200 OK
	- [User](#user)

### GET /users?username=
_(Authenticated)_ Return list of condensed user information given search term
- Query Parameters
	- `username` username of the user to search for
- Response
	- `application/json`
	- 200 OK
	- List[[UserInfo](#userinfo)]
	
### POST /users
_(Authenticated)_ Create a new user in the system using the information provided. Note: The user must have been previously registered in Cognito
- Body Parameters
	- `CreateUserRequest` [CreateUserRequest](#createuserrequest)
- Response
	- `application/json`
	- 201 CREATED
	- [User](#user)
	
## Exercises
### GET /exercise/{exercise_id}
Return exercise with corresponding id
- Path Parameters
	- `exercise_id` UUID format
- Response
	- `application/json`
	- 200 OK
	- [Exercise](#exercise)

### GET /exercise?name=
Return list of exercises given search term
- Query Parameters
	- `name` name of the exercise to search for
- Response
	- `application/json`
	- 200 OK
	- List[[Exercise](#exercise)]

## Workout-Templates
### POST /users/{user_id}/workout-templates
_(Protected)_ Creates a new workout-template for an existing user
- Path Parameters
	- `user_id` UUID format
- Body Parameters
	- `CreateWkTemplateRequest` [CreateWkTemplateRequest](#createwktemplaterequest)
- Response
	- `application/json`
	- 201 CREATED
	- [WorkoutTemplate](#workouttemplate)

### DELETE /users/{user_id}/workout-templates/{workout_template_id}
_(Protected)_ Delete a user's workout template with corresponding user id and template id
- Path Parameters
	- `workout_template_id` UUID format
	- `user_id` UUID format
- Response
	- 204 NO CONTENT

### GET /users/{user_id}/workout-templates
_(Authenticated)_ Return a summary of all templates for a given user
- Path Parameters
	- `user_id` UUID format
- Response
	- `application/json`
	- 200 OK
	- [GetAllTemplatesResponse](#getalltemplatesresponse)

### GET /users/{user_id}/workout-templates/{workout_template_id}
_(Authenticated)_ Return a detailed description of a given template for a given user
- Path Parameters
	- `workout_template_id` UUID format
	- `user_id` UUID formt
- Response
	- `application/json`
	- 200 OK
	- [GetTemplateResponse](#gettemplateresponse)

# Definitions
## User
```json
{
  "id": "string (UUID format)",
  "username": "string",
  "display_name": "string",
  "date_joined": "string (YYYY-MM-DD format)",
  "date_of_birth": "string (YYYY-MM-DD format) or null",
  "height": "integer or null",
  "weight": "number (float) or null",
  "gender": "integer or null",
  "fitness_goal": "integer or null",
  "fitness_level": "integer or null"
}
```
## UserInfo
```json
{
  "id": "string (UUID format)",
  "username": "string",
  "display_name": "string",
}
```
## CreateUserRequest
```json
{
  "uuid": "string (UUID format)",
  "username": "string",
  "date_joined": "string (YYYY-MM-DD format)"
}
```
## Exercise
```json
{
  "id": "string (UUID format)",
  "name": "string",
  "main_muscle_group": "integer or null",
  "secondary_muscle_group": "integer or null",
  "necessary_equipment": "integer or null",
  "exercise_type": "integer or null"
}
```
## WorkoutTemplate
```json
{
  "id": "string (UUID format)",
  "user_id": "string (UUID format)",
  "name": "string",
  "description": "string or null",
  "date_created": "string (YYYY-MM-DD format)"
}
```
## CreateWkTemplateRequest
The `elements` array must follow specific rules for the structure to be valid. The position of the exercises should range from 0 to n, without any missing spots or repetitions. Superset values should range from 0 to m, with at least two exercises sharing the same superset value. Additionally, for a given superset value, all exercises must have sequential position values.
```json
{
  "name": "string",
  "description": "string or null",
  "date_created": "string (YYYY-MM-DD format)",
  "elements": [
    {
      "exercise_id": "string (UUID format)",
      "position": "integer",
      "reps": "integer",
      "sets": "integer",
      "weight": "integer",
      "rest": "integer",
      "super_set": "integer or null"
    }
  ]
}
```
## GetAllTemplatesResponse
```json
{
  "count": "integer",
  "templates": [
    {
      "id": "string (UUID format)",
      "user_id": "string (UUID format)",
      "name": "string",
      "description": "string or null",
      "date_created": "string (YYYY-MM-DD format)"
    }
  ]
}
```
## GetTemplateResponse
```json
{
  "id": "string (UUID format)",
  "user_id": "string (UUID format)",
  "name": "string",
  "description": "string or null",
  "date_created": "string (YYYY-MM-DD format)",
  "elements": [
    {
      "id": "string (UUID format)",
      "workout_template_id": "string (UUID format)",
      "exercise_id": "string (UUID format)",
      "exercise_name": "string",
      "position": "integer",
      "reps": "integer",
      "sets": "integer",
      "weight": "integer",
      "rest": "integer",
      "super_set": "integer or null"
    }
  ]
}
```

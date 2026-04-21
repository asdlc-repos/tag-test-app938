# Overview

A lightweight REST API service that provides a greeting endpoint. The API accepts HTTP requests and returns personalized or default greeting messages in JSON format.

# Personas

- **API Consumer** — Developer integrating the greeting endpoint into their application or testing the API functionality.
- **System Administrator** — Operations personnel responsible for deploying, monitoring, and maintaining the API service.

# Capabilities

## Core Greeting Functionality

- The system SHALL provide a GET endpoint at `/greeting` that returns a JSON response.
- WHEN a request is made to `/greeting` without parameters, the system SHALL return a default greeting message "Hello, World!".
- WHEN a request is made to `/greeting` with a `name` query parameter, the system SHALL return a personalized greeting incorporating the provided name.
- The system SHALL return all greeting responses with HTTP status code 200.
- The system SHALL format all greeting responses as valid JSON with a `message` field.

## Error Handling

- IF a request is made with an unsupported HTTP method, THEN the system SHALL return HTTP status code 405.
- IF a request is made to an undefined endpoint, THEN the system SHALL return HTTP status code 404.
- IF the server encounters an internal error, THEN the system SHALL return HTTP status code 500 with a generic error message.

## API Standards

- The system SHALL set the Content-Type header to `application/json` for all responses.
- The system SHALL accept requests with UTF-8 encoded query parameters.
- The system SHALL sanitize the `name` parameter to prevent injection attacks before including it in the response.

## Performance & Availability

- The system SHALL respond to greeting requests within 100 milliseconds under normal load.
- The system SHALL support at least 100 concurrent requests without degradation.
- The system SHALL log all incoming requests with timestamp, endpoint, and response status.
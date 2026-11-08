# API Testing Postman Portfolio

A Postman collection for practicing and demonstrating REST API testing against the [Simple Books API](https://simple-books-api.glitch.me). The collection uses Postman test scripts written in JavaScript to check HTTP status codes, response data, JSON schemas, authentication, and common error cases.

## What's covered

- **Service status** — checks the `/status` endpoint and expected `OK` response.
- **Books** — lists books, validates the response schema, checks filtering by book type and limit, and exercises invalid query values.
- **Single book** — retrieves books by ID and checks book details and not-found behavior.
- **Authentication** — registers an API client and saves the returned access token as the collection variable `accessToken`.
- **Orders** — submits orders with and without a bearer token, lists orders, retrieves an order, updates and deletes an order, and checks error responses.
- **Duplicate client registration** — checks the conflict response.

## Requirements

- [Postman](https://www.postman.com/downloads/) desktop app or Postman web app.
- An environment where the Simple Books API is reachable.

## Getting started

1. Import `simple-books-api.postman_collection.json` into Postman.
2. Select the collection and verify the `base_url` variable is set to `https://simple-books-api.glitch.me`.
3. Run **API Authentication → api-clients** to register a client. The test script stores the returned token in the collection variable `accessToken`.
4. Run the authenticated order requests using that token. Create an order before retrieving, updating, or deleting it; set `orderId` to the ID returned by the create-order response when needed.
5. Run the collection or individual requests from the Postman Collection Runner.

The API may impose its own rate limits and data constraints. Requests that create, update, or delete orders change API state, so use them deliberately. The collection currently includes example IDs and expected values; update them if the API data or your created orders differ.

## Collection variables

| Variable | Purpose | Default |
| --- | --- | --- |
| `base_url` | Base URL for the API | `https://simple-books-api.glitch.me` |
| `accessToken` | Bearer token saved after client registration | Empty until registered |
| `orderId` | Order ID used by order requests | Example ID; replace with a valid order ID |
| `item_id` | Example item identifier | `3` |
| `Mock-server` | Existing collection variable | `mock-server` |

## Notes

- The collection schema is Postman Collection v2.1.
- Tests are defined in the collection's request-level Postman test scripts.
- Some example assertions depend on fixed API data. If a request fails because the service data has changed, refresh the expected values or use a newly created order.

## License

No license is specified in this repository yet.

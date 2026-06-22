#  JokeAPI

A simple RESTful API that i developed under my coursera work

## 🚀 Features

* Get a random joke
* Get a specific joke by ID
* Filter jokes by category/type
* Add new jokes
* Replace existing jokes
* Partially update jokes
* Delete individual jokes
* Delete all jokes (protected with API key)

---

## 📌 Base URL

```text
http://localhost:3000
```

---

# 📖 API Endpoints

## 🎲 Get a Random Joke

Returns a random joke from the database.

### Request

```http
GET /random
```

### Example

```bash
curl http://localhost:3000/random
```

### Response

```json
{
  "id": 43,
  "jokeText": "What did one ocean say to the other ocean? Nothing, they just waved.",
  "jokeType": "Wordplay"
}
```

---

## 🔍 Get a Specific Joke

Returns a joke matching the provided ID.

### Request

```http
GET /jokes/:id
```

### Example

```bash
curl http://localhost:3000/jokes/2
```

### Response

```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
  "jokeType": "Puns"
}
```

---

## 🏷️ Filter Jokes by Type

Returns all jokes that match the specified joke type.

### Request

```http
GET /filter?type=<jokeType>
```

### Example

```bash
curl "http://localhost:3000/filter?type=Puns"
```

### Response

```json
[
  {
    "id": 2,
    "jokeText": "Why did the scarecrow win an award? Because he was outstanding in his field.",
    "jokeType": "Puns"
  }
]
```

---

## ➕ Create a New Joke

Adds a new joke to the collection.

### Request

```http
POST /jokes
```

### Body Parameters

| Field | Type   | Required |
| ----- | ------ | -------- |
| text  | string | Yes      |
| type  | string | Yes      |

### Example Request

```json
{
  "text": "I am on the moon and there is nowhere to get a beer. There is no space bar.",
  "type": "Science"
}
```

### Response

```json
{
  "id": 101,
  "jokeText": "I am on the moon and there is nowhere to get a beer. There is no space bar.",
  "jokeType": "Science"
}
```

---

## 🔄 Replace a Joke

Completely replaces an existing joke.

### Request

```http
PUT /jokes/:id
```

### Body Parameters

| Field | Type   | Required |
| ----- | ------ | -------- |
| text  | string | Yes      |
| type  | string | Yes      |

### Example

```json
{
  "text": "Why did the scarecrow win a prize? Because he was outstanding in his field.",
  "type": "Science"
}
```

### Response

```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win a prize? Because he was outstanding in his field.",
  "jokeType": "Science"
}
```

---

## ✏️ Edit a Joke

Partially updates an existing joke.

### Request

```http
PATCH /jokes/:id
```

### Body Parameters

Both fields are optional.

| Field | Type   |
| ----- | ------ |
| text  | string |
| type  | string |

### Example

```json
{
  "type": "Agriculture"
}
```

### Response

```json
{
  "id": 2,
  "jokeText": "Why did the scarecrow win a prize? Because he was outstanding in his field.",
  "jokeType": "Agriculture"
}
```

---

## 🗑️ Delete a Joke

Deletes a joke using its ID.

### Request

```http
DELETE /jokes/:id
```

### Example

```bash
curl -X DELETE http://localhost:3000/jokes/2
```

### Response

```text
OK
```

---

## ☠️ Delete All Jokes

Deletes every joke in the database.

> **Warning:** This action is irreversible.

### Authentication

An API key is required.

### Request

```http
DELETE /jokes/all
```

### Example

```bash
curl -X DELETE http://localhost:3000/jokes/all \
-H "x-api-key: YOUR_API_KEY"
```

### Response

```text
OK
```

---

# 📊 Joke Object Structure

```json
{
  "id": 1,
  "jokeText": "Why don't scientists trust atoms? Because they make up everything.",
  "jokeType": "Science"
}
```

| Property | Type   | Description            |
| -------- | ------ | ---------------------- |
| id       | number | Unique joke identifier |
| jokeText | string | The joke content       |
| jokeType | string | Category of the joke   |

---

# ⚠️ Error Responses

### Joke Not Found

```json
{
  "error": "Joke not found"
}
```

### Invalid Joke Type

```json
{
  "error": "No jokes found for the specified type"
}
```

### Unauthorized Request

```json
{
  "error": "Invalid API Key"
}
```

---

# 🛠️ Tech Stack

* Node.js
* Express.js
* REST API
* JSON

---

# 📄 License

This project is open-source and available under the MIT License.

---

Made with ❤️ to spread laughter around the world.

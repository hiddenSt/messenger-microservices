# User management api


## POST `/user`

Creates new user in system. On successfull creation publishes message to rabbitmq.
.
### Request body

<i>application/json</i>:

```json
{
  "username": "user123",
  "first_name": "John",
  "last_name": "AA",
  "email": "example@email.com"
}
```

* `username` - string which must start with a letter.
* `first_name` - string
* `last_name` - string
* `email` - valid email

### Responses

**`201 Created`** - User is successfully created.<br><br>
<i>applicaton/json</i>:

```json
{
  "id": 1,
  "username": "user123",
  "first_name": "John",
  "last_name": "AA",
  "email": "example@email.com",
}
```

**`200 OK`** - User already created.<br><br>
<i>application/json</i>:

```json
{
  "id": 1,
  "username": "user123",
  "first_name": "John",
  "last_name": "AA",
  "email": "example@mail.com",
}
```

**`400 Bad Request`** - Request contains errors.<br><br>
<i>application/json</i>:

```json
{
  "error": "error description",
}
```

## GET `/user/{id}`

Returns information about user.

### Query parameters
* `id` - unsigned integer, user identifier.

### Responses

**`200 OK`** - User is present in system.<br><br>
<i>application/json</i>
```json
{
  "id": 1,
  "username": "user123",
  "first_name": "John",
  "last_name": "AA",
  "email": "example@mail.com",
}
```

**`404 Not Found`** - User with given id is not in system.<br><br>
Body is empty.

**`400 Bad Request`** - Errors in identifier.<br><br>
<i>application/json</i>:

```json
{
  "error": "error description"
}
```

## DELETE `/user/{id}`

### Query parameters
* `id` - unsigned integer, user identifier.

### Responses

**`204 No Content`** - User is successfully removed from system. <br><br>


**`404 Not Found`** - User with given id is not found in system. <br><br>
Body is empty

**`404 Not Found`** - User with given id is not in system.<br><br>
Body is empty.

**`400 Bad Request`** - Errors in identifier.<br><br>
<i>application/json</i>:

```json
{
  "error": "error description"
}
```



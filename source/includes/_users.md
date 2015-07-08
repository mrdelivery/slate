# Users

This service deals with Users and UserGroups.

## List Users

Gets the full list of users in the system.

> Request: 

```shell
http://52.27.51.33:8888/users
```

> Response:

```json
{
  "1": {
    "name": "John",
    "surname": "Lewis",
    "role": "Developer"
  },
  "2": {
    "name": "Shannon",
    "surname": "Black",
    "role": "Team Lead"
  },
  "3": {
    "name": "Monde",
    "surname": "Masiko",
    "role": "Product Owner"
  },
  "4": {
    "name": "Himesh",
    "surname": "Ramjee",
    "role": "Software Development Manager"
  },
  "5": {
    "name": "Andrew",
    "surname": "Cooper",
    "role": "Gun Toting American"
  },
  "6": {
    "name": "Christian",
    "surname": "Ndala",
    "role": "Tester and code fault finder"
  },
  "7": {
    "name": "Devin",
    "surname": "Sinclair",
    "role": "Head honcho"
  },
  "8": {
    "name": "Alex",
    "surname": "xxx",
    "role": "Operations Manager"
  },
  "9": {
    "name": "Ezna",
    "surname": "van Vyk",
    "role": "Head honcho"
  },
  "10": {
    "name": "Teddy",
    "surname": "Muba",
    "role": "Data Capturer"
  },
  "11": {
    "name": "Natasha",
    "surname": "Thomas",
    "role": "Data Capturer"
  }
}
```
### HTTP Request

`GET /users`

## Get Single User

Returns a single user record.

> Request: 

```shell
http://52.27.51.33:8888/users/1
```
> Response:

```json
{
  "name": "John",
  "surname": "Lewis",
  "role": "Developer"
}
```
### HTTP Request

`GET http://example.com/users/<id>`

### Query Parameters
Parameter | Type | Default | Required? | Description
--------- | -----| --------| --------- | -----------
id|numeric identifier|N/A|mandatory|The DB identifier of the entity to retrieve

## List User Groups

Lists all the user groups in the system.

> Request: 

```shell
http://52.27.51.33:8888/usergroups
```

> Response:

```json
{
  "1": {
    "name": "Development Team",
    "members": [
      1,
      2,
      5,
      6
    ],
    "type": "Users"
  },
  "2": {
    "name": "Business Team",
    "members": [
      3,
      7,
      4
    ],
    "type": "Users"
  },
  "3": {
    "name": "Operations Team",
    "members": [
      8,
      9,
      10,
      11
    ],
    "type:": "Users"
  }
}
```
### HTTP Request

`GET /usergroups`


## Get Single User Group

Gets a single user group.

> Request: 

```shell
http://52.27.51.33:8888/usergroups/5
```
> Response:

```json
{
  "name": "Development Team",
  "members": [
    1,
    2,
    5,
    6
  ],
  "type": "Users"
}
```
### HTTP Request

`http://52.27.51.33:8888/usergroups/5`

### Query Parameters
Parameter | Type | Default | Required? | Description
--------- | -----| --------| --------- | -----------
id|numeric identifier|N/A|mandatory|The DB identifier of the entity to retrieve


CurseForge API
==============
The CurseForge API allows users to automate managing their projects, and retrieve data such as game versions and dependencies from CurseForge.

Generate a Token
----------------
To access the API, you must generate an API token. This can be done by going to "My Account" and going to the "API Tokens" tab.

Authorization
-------------
To authenticate with the API, you must provide your generate token using the X-Api-Token header.

Game Dependencies
-----------------
To retrieve a list of game dependencies issue a GET request to `/api/game/dependencies`. It will return an array of json objects containing the following data:

```js
{
    id: 42,
    name: "Bukkit",
    slug: "bukkit"
}
```

Game Versions
-------------
To retrieve a list of game versions issue a GET request to `/api/game/versions`. It will return an array of json objects containing the following data:

```js
{
    id: 158,
    gameDependencyID: 42
    name: "1.8.4",
    slug: "1-8-4"
}
```

Uploading a File to a Project
-----------------------------
TODO

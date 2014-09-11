CurseForge API
==============
The CurseForge API allows users to automate managing their projects, and retrieve data such as game versions and dependencies from CurseForge.


Generate a Token
----------------
To access the API, you must first generate an API token. To do that, go to the "API Tokens" tab under "My Account" on CurseForge.


Authentication
-------------
To authenticate with the API, you must provide your generated token using the `X-Api-Token` header.


Game Dependencies API
---------------------
To retrieve a list of game dependencies issue a GET request to `/api/game/dependencies`. It will return an array of json objects containing the following data:

```js
{
    id: 42,
    name: "Bukkit",
    slug: "bukkit"
}
```


Game Versions API
-----------------
To retrieve a list of game versions issue a GET request to `/api/game/versions`. It will return an array of json objects containing the following data:

```js
{
    id: 158,
    gameDependencyID: 42, // This field will be omitted if the version doesn't belong to a dependency.
    name: "1.8.4",
    slug: "1-8-4"
}
```


Project Upload File API
-----------------------
To upload a file, issue a POST multipart/form-data request to `/api/projects/<projectID>/upload-file`, containing two fields: `metadata` and `file`, which must be the actual file. The ID of your project will be in the URL when you go to its overview page.

`metadata` must contain a json object with the following fields:

```js
{
    changelog: "A plaintext string describing changes.",
    displayName: "Foo", // Optional: A friendly display name used on the site if provided.
    parentFileID: 42, // Optional: The parent file of this file.
    gameVersions: [157, 158], // A list of supported game versions, see the Game Versions API for details. Not supported if parentFileID is provided.
    releaseType: "alpha" // One of "alpha", "beta", "release".
}
```

On successful upload, returns a json object containing the new file's ID:

```js
{
    id: 20402
}
```

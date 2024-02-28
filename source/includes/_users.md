# Users

This section describes the various object types, mutations and queries available for users in the GraphQL API

## Social SignIn

```graphql
mutation socialSignIn($data: LoginInput) {
  socialSignIn(data: $data) {
    token
    status
    user {
      _id
      name
      picUrl
    }
  }
}
```

```javascript
import { ApolloClient, gql } from "@apollo/client";

const client = new ApolloClient({
  uri: "http://localhost:8080/graphql",
});

const socialSignInMutation = gql`
  mutation SocialSignIn($data: LoginInput) {
    socialSignIn(data: $data) {
      token
      status
      user {
        _id
        name
        picUrl
      }
    }
  }
`;
client
  .mutate({
    mutation: socialSignInMutation,
    variables: {
      data: {
        /* Input data as described */
      },
    },
  })
  .then((result) => {})
  .catch((error) => {});
```

> The above code samples return a JSON structured like this:

```json
{
  "data": {
    "socialSignIn": {
      "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
      "status": true,
      "user": {
        "_id": "abc123",
        "name": "John Doe",
        "picUrl": "https://example.com/profile.jpg"
      }
    }
  }
}
```

This `socialSignIn` mutation allows users to sign in using social media credentials. If a user is not found, a new record is created in the database

- **Input** A `LoginInput` object containing the necessary data for social sign-in.

- **Output** A `LoginSuccess` object containing the status of the sign-in attempt, an authentication token, and user information.

| Parameter | Type        | Description                                              |
| --------- | ----------- | -------------------------------------------------------- |
| status    | Boolean     | Represents the status of the login attempt.              |
| token     | String      | Contains the authentication token upon successful login. |
| user      | UserSummary | Represents a summary of the user who logged in.          |

The `UserSummary` is an object representing the user details as shown below.

| Parameter | Type   | Description                                             |
| --------- | ------ | ------------------------------------------------------- |
| \_id      | String | Represents the unique identifier of the user.           |
| name      | String | Represents the name of the user.                        |
| picUrl    | String | Contains the URL or path to the user's profile picture. |

## Update Profile

```graphql
mutation updateProfile($profile: UserInput) {
  updateProfile(data: $profile) {
    _id
    name
    picUrl
    email
    emailVerified
    phone
    phoneVerified
  }
}
```

```javascript
import { ApolloClient, gql } from "@apollo/client";
const client = new ApolloClient({
  uri: "http://localhost:8080/graphql",
});

const updateProfileMutation = gql`
  mutation UpdateProfile($profile: UserInput) {
    updateProfile(data: $profile) {
      _id
      name
      picUrl
      email
      emailVerified
      phone
      phoneVerified
    }
  }
`;

// Usage example:
client
  .mutate({
    mutation: updateProfileMutation,
    variables: {
      profile: {
        // Provide updated profile information
      },
    },
  })
  .then((result) => {})
  .catch((error) => {});
```

> The above code sample returns a JSON structured like this

```json
{
  "data": {
    "updateProfile": {
      "_id": "def456",
      "name": "Jane Smith",
      "picUrl": "https://example.com/new_profile.jpg",
      "email": "jane@example.com",
      "emailVerified": true,
      "phone": "+1234567890",
      "phoneVerified": true
    }
  }
}
```

The `updateProfile` mutation allows users to update their profile information.

- **Input** A `UserInput` object containing the updated profile information.

| Parameter | Type   | Description                               |
| --------- | ------ | ----------------------------------------- |
| name      | String | Represents the name of the user.          |
| picUrl    | String | Contains the URL of the user's picture.   |
| email     | String | Represents the email address of the user. |
| phone     | String | Represents the phone number of the user.  |

- **Output** The `User` object as described below

| Parameter     | Type    | Description                                                  |
| ------------- | ------- | ------------------------------------------------------------ |
| \_id          | String  | Represents the unique identifier of the user.                |
| name          | String  | Represents the name of the user.                             |
| picUrl        | String  | Contains the URL or path to the user's profile picture.      |
| googleId      | String  | Represents the Google ID associated with the user.           |
| facebookId    | String  | Represents the Facebook ID associated with the user.         |
| email         | String  | Represents the email address of the user.                    |
| emailVerified | Boolean | Indicates whether the user's email is verified.              |
| phone         | String  | Represents the phone number of the user.                     |
| phoneVerified | Boolean | Indicates whether the user's phone number is verified.       |
| createdAt     | String  | Represents the date and time when the user was created.      |
| updatedAt     | String  | Represents the date and time when the user was last updated. |

## My Profile

```graphql
query myProfile {
  myProfile {
    _id
    name
    picUrl
    email
    emailVerified
    phone
    phoneVerified
  }
}
```

```javascript

```

> The above code sample returns a JSON structured like this

```json
{
  "data": {
    "updateProfile": {
      "_id": "def456",
      "name": "Jane Smith",
      "picUrl": "https://example.com/new_profile.jpg",
      "email": "jane@example.com",
      "emailVerified": true,
      "phone": "+1234567890",
      "phoneVerified": true
    }
  }
}
```

The `myProfile` query allows a logged in user to get their profile information.

- **Output** A `User` object containing the logged in user profile information.

| Parameter     | Type    | Description                                                  |
| ------------- | ------- | ------------------------------------------------------------ |
| \_id          | String  | Represents the unique identifier of the user.                |
| name          | String  | Represents the name of the user.                             |
| picUrl        | String  | Contains the URL or path to the user's profile picture.      |
| googleId      | String  | Represents the Google ID associated with the user.           |
| facebookId    | String  | Represents the Facebook ID associated with the user.         |
| email         | String  | Represents the email address of the user.                    |
| emailVerified | Boolean | Indicates whether the user's email is verified.              |
| phone         | String  | Represents the phone number of the user.                     |
| phoneVerified | Boolean | Indicates whether the user's phone number is verified.       |
| createdAt     | String  | Represents the date and time when the user was created.      |
| updatedAt     | String  | Represents the date and time when the user was last updated. |

## Find User

```graphql
query findUser($id: String) {
  findUser(userId: $id) {
    _id
    name
    picUrl
    email
    emailVerified
    phone
    phoneVerified
  }
}
```

```javascript
// Import necessary modules
import { ApolloClient, InMemoryCache, gql } from "@apollo/client";

// Create an instance of ApolloClient
const client = new ApolloClient({
  uri: "YOUR_GRAPHQL_ENDPOINT_URL",
  cache: new InMemoryCache(),
});

// Define the GraphQL query
const FIND_USER_QUERY = gql`
  query FindUser($id: String) {
    findUser(userId: $id) {
      _id
      name
      picUrl
      email
      emailVerified
      phone
      phoneVerified
    }
  }
`;
// Execute the query using ApolloClient
client
  .query({
    query: FIND_USER_QUERY,
    variables: { id: "YOUR_USER_ID" },
  })
  .then((result) => {
    console.log(result.data.findUser);
  })
  .catch((error) => {});
```

> The above code sample returns a JSON structured like this

```json
{
  "data": {
    "updateProfile": {
      "_id": "def456",
      "name": "Jane Smith",
      "picUrl": "https://example.com/new_profile.jpg",
      "email": "jane@example.com",
      "emailVerified": true,
      "phone": "+1234567890",
      "phoneVerified": true
    }
  }
}
```

The `findUser` query allows a logged in user to get their profile information.

- **Input** A `id` string that represents the unique identifier of the user you want to find.
- **Output** A `User` object containing the user's profile information.

| Parameter     | Type    | Description                                                  |
| ------------- | ------- | ------------------------------------------------------------ |
| \_id          | String  | Represents the unique identifier of the user.                |
| name          | String  | Represents the name of the user.                             |
| picUrl        | String  | Contains the URL or path to the user's profile picture.      |
| googleId      | String  | Represents the Google ID associated with the user.           |
| facebookId    | String  | Represents the Facebook ID associated with the user.         |
| email         | String  | Represents the email address of the user.                    |
| emailVerified | Boolean | Indicates whether the user's email is verified.              |
| phone         | String  | Represents the phone number of the user.                     |
| phoneVerified | Boolean | Indicates whether the user's phone number is verified.       |
| createdAt     | String  | Represents the date and time when the user was created.      |
| updatedAt     | String  | Represents the date and time when the user was last updated. |

## Find Users

```graphql
query findUsers($filter: [FilterOption]) {
  findUsers(options: $filter) {
    _id
    name
    picUrl
    email
    emailVerified
    phone
    phoneVerified
  }
}
```

```javascript
// Import necessary modules
import { ApolloClient, InMemoryCache, gql } from "@apollo/client";

// Create an instance of ApolloClient
const client = new ApolloClient({
  uri: "YOUR_GRAPHQL_ENDPOINT_URL",
  cache: new InMemoryCache(),
});

// Define the GraphQL query
const FIND_USERS_QUERY = gql`
  query FindUsers($filter: [FilterOption]) {
    findUsers(options: $filter) {
      _id
      name
      picUrl
      email
      emailVerified
      phone
      phoneVerified
    }
  }
`;

// Define the filter options
const filterOptions = [
  // Define your filter options here
  // Example: { key: "name", value: "John" }
];

// Execute the query using ApolloClient
client
  .query({
    query: FIND_USERS_QUERY,
    variables: { filter: filterOptions },
  })
  .then((result) => {
    console.log(result.data.findUsers);
  })
  .catch((error) => {});
```

> The above code sample returns a JSON structured like this

```json
[
  {
    "data": {
      "updateProfile": {
        "_id": "def456",
        "name": "Jane Smith",
        "picUrl": "https://example.com/new_profile.jpg",
        "email": "jane@example.com",
        "emailVerified": true,
        "phone": "+1234567890",
        "phoneVerified": true
      }
    }
  }
]
```

The `findUsers` query allows a logged in user to get their profile information.

- **Input** An array of `FilterOption` objects containing the fields to use to find users.

| Parameter   | Type           | Description                                            |
| ----------- | -------------- | ------------------------------------------------------ |
| key         | String         | Represents the key or field to filter on.              |
| dataType    | FilterDataType | Enum for the data value: STRING, BOOLEAN, INT, FLOAT   |
| stringValue | String         | (optional) Represents the string value for filtering.  |
| boolValue   | Boolean        | (optional) Represents the boolean value for filtering. |
| floatValue  | Float          | (optional) Represents the float value for filtering.   |

- **Output** An array of `User` objects containing the user profile information.

| Parameter     | Type    | Description                                                  |
| ------------- | ------- | ------------------------------------------------------------ |
| _id          | String  | Represents the unique identifier of the user.                |
| name          | String  | Represents the name of the user.                             |
| picUrl        | String  | Contains the URL or path to the user's profile picture.      |
| googleId      | String  | Represents the Google ID associated with the user.           |
| facebookId    | String  | Represents the Facebook ID associated with the user.         |
| email         | String  | Represents the email address of the user.                    |
| emailVerified | Boolean | Indicates whether the user's email is verified.              |
| phone         | String  | Represents the phone number of the user.                     |
| phoneVerified | Boolean | Indicates whether the user's phone number is verified.       |
| createdAt     | String  | Represents the date and time when the user was created.      |
| updatedAt     | String  | Represents the date and time when the user was last updated. |

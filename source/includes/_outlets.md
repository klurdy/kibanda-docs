# Outlets

This section describes the various object types, mutations and queries available for outlets in the GraphQL API

## Add Outlet 

```graphql
mutation addOutlet($data: OutletInput){
  addOutlet(data: $data){
    _id
    name
    streetAddress
    meals
    features
    type
    openingTime
    closingTime
    minPrice
    maxPrice
    geolocation {
      coordinates
    }
    menus {
      _id
      name
      price
      description
      picture
    }
    reviews {
      total
      average
    }
  }
}
```

```javascript
// Import necessary modules
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';

// Create an instance of ApolloClient
const client = new ApolloClient({
  uri: 'YOUR_GRAPHQL_ENDPOINT_URL',
  cache: new InMemoryCache()
});

// Define the GraphQL mutation
const ADD_OUTLET_MUTATION = gql`
  mutation AddOutlet($data: OutletInput) {
    addOutlet(data: $data) {
      _id
      name
      streetAddress
      meals
      features
      type
      openingTime
      closingTime
      minPrice
      maxPrice
      geolocation {
        coordinates
      }
      menus {
        _id
        name
        price
        description
        picture
      }
      reviews {
        total
        average
      }
    }
  }
`;

// Define the outlet data object
const outletData = {
  name: "My Outlet",
  displayPicture: "https://example.com/menu_item_1.jpg"
  streetAddress: "123 Main Street",
  meals: ["Breakfast", "Lunch", "Dinner"],
  features: ["12345", "67890"],
  type: "Restaurant",
  openingTime: "08:00 AM",
  closingTime: "10:00 PM",
  minPrice: 10,
  maxPrice: 50,
  geolocation: {
    type: "Point",
    coordinates: [10.2, 56.25]
  }
};

// Execute the mutation using ApolloClient
client.mutate({
  mutation: ADD_OUTLET_MUTATION,
  variables: { data: outletData }
})
.then(result => { console.log( result.data.addOutlet);})
.catch(error => { });
```

> The above code samples return a JSON structured like this:

```json
{
  "_id": "abc123",
  "name": "Sample Outlet",
  "displayPicture": "https://example.com/outlet_picture.jpg",
  "geolocation": {
    "latitude": 123.456,
    "longitude": -78.910
  },
  "streetAddress": "123 Main Street",
  "features": ["WiFi", "Outdoor Seating"],
  "type": "Restaurant",
  "openingTime": "08:00 AM",
  "closingTime": "10:00 PM",
  "meals": ["Breakfast", "Lunch", "Dinner"],
  "menus": [],
  "reviews": {
    "total": 0,
    "average": 0
  },
  "minPrice": 8,
  "maxPrice": 30
}

```

This `addOutlet` mutation allows authenticated users to add a new outlet in the system.

- **Input** A `OutletInput` object containing the necessary data for adding a new outlet.

Parameter | Type | Description
--------- | ------- | -----------
name | String | Represents the name of the outlet.
displayPicture | String | Contains the URL or path to the outlet's display picture.
geolocation | geoLocation | Represents the geographical coordinates of the outlet.
streetAddress | String | Represents the street address of the outlet.
features | [String] | Represents a list of features or amenities of the outlet.
type | String | Represents the type or category of the outlet.
openingTime | String | Represents the opening time of the outlet.
closingTime | String | Represents the closing time of the outlet.
meals | [String] | Represents a list of meals or food options available at the outlet.
minPrice | Int | Represents the minimum price range at the outlet.
maxPrice | Int | Represents the maximum price range at the outlet.
author | UserSummary | Represents a summary of the user who authored the outlet.

- **Output** A `Outlet` object containing the status of the sign-in attempt, an authentication token, and user information.

Parameter | Type | Description
--------- | ------- | -----------
name | String | Represents the name of the outlet.
displayPicture | String | Contains the URL or path to the outlet's display picture.
geolocation | geoLocation | Represents the geographical coordinates of the outlet.
streetAddress | String | Represents the street address of the outlet.
features | [String] | Represents a list of features or amenities of the outlet.
type | String | Represents the type or category of the outlet.
openingTime | String | Represents the opening time of the outlet.
closingTime | String | Represents the closing time of the outlet.
distance | String | Represents the distance of the outlet from a reference point.
meals | [String] | Represents a list of meals or food options available at the outlet.
isOpen | Boolean | Indicates whether the outlet is currently open.
isFavourite | Boolean | Indicates whether the outlet is marked as a favorite.
menus | [OutletMenu] | Represents a list of menus available at the outlet.
reviews | OutletReviewSummary | Represents a summary of reviews for the outlet.
minPrice | Int | Represents the minimum price range at the outlet.
maxPrice | Int | Represents the maximum price range at the outlet.
author | UserSummary | Represents a summary of the user who authored the outlet.
ownedBy | String | Represents the owner of the outlet.
createdBy | String | Represents the user who created the outlet.
createdAt | String | Represents the date and time when the outlet was created.
updatedAt | String | Represents the date and time when the outlet was last updated.

## Update Outlet 

```graphql
mutation updateOutlet($data: OutletInput){
  updateOutlet(data: $data){
    _id
    name
    streetAddress
    meals
    features
    type
    openingTime
    closingTime
    minPrice
    maxPrice
    geolocation {
      coordinates
    }
    menus {
      _id
      name
      price
      description
      picture
    }
    reviews {
      total
      average
    }
  }
}
```

```javascript
// Import necessary modules
import { ApolloClient, InMemoryCache, gql } from '@apollo/client';

// Create an instance of ApolloClient
const client = new ApolloClient({
  uri: 'YOUR_GRAPHQL_ENDPOINT_URL',
  cache: new InMemoryCache()
});

// Define the GraphQL mutation
const UPDATE_OUTLET_MUTATION = gql`
  mutation UpdateOutlet($data: OutletInput) {
    updateOutlet(data: $data) {
      _id
      name
      streetAddress
      meals
      features
      type
      openingTime
      closingTime
      minPrice
      maxPrice
      geolocation {
        coordinates
      }
      menus {
        _id
        name
        price
        description
        picture
      }
      reviews {
        total
        average
      }
    }
  }
`;

// Define the outlet data object
const outletData = {
  _id: "abc123",
  name: "Updated Outlet",
  streetAddress: "456 Oak Street",
  meals: ["Breakfast", "Lunch", "Dinner"],
  features: ["WiFi", "Outdoor Seating"],
  type: "Cafe",
  openingTime: "07:00 AM",
  closingTime: "11:00 PM",
  minPrice: 15,
  maxPrice: 40,
  geolocation: {
    coordinates: [latitude, longitude]
  }
};

// Execute the mutation using ApolloClient
client.mutate({
  mutation: UPDATE_OUTLET_MUTATION,
  variables: { data: outletData }
})
.then(result => { console.log(result.data.updateOutlet); })
.catch(error => { console.error('Error updating outlet:', error); });

```

> The above code samples return a JSON structured like this:

```json

n

{
  "_id": "abc123",
  "name": "Sample Outlet",
  "streetAddress": "123 Main Street",
  "meals": ["Breakfast", "Lunch", "Dinner"],
  "features": ["WiFi", "Outdoor Seating"],
  "type": "Restaurant",
  "openingTime": "08:00 AM",
  "closingTime": "10:00 PM",
  "minPrice": 10,
  "maxPrice": 50,
  "geolocation": {
    "coordinates": [123.456, -78.910]
  },
  "menus": [
    {
      "_id": "menu1",
      "name": "Menu Item 1",
      "price": 10.99,
      "description": "Description of Menu Item 1",
      "picture": "https://example.com/menu_item_1.jpg"
    },
    {
      "_id": "menu2",
      "name": "Menu Item 2",
      "price": 12.99,
      "description": "Description of Menu Item 2",
      "picture": "https://example.com/menu_item_2.jpg"
    }
  ],
  "reviews": {
    "total": 50,
    "average": 4.5
  }
}

```

## View Outlet

```graphql
query viewOutlet($options: [FilterOption]){
  viewOutlet(options: $options){
    _id
    name
    displayPicture
    streetAddress
    type
    meals
    features
    minPrice
    maxPrice
    isOpen
    geolocation {
      coordinates
    }
    menus {
      _id
      name
      price
      description
      picture
    }
    reviews {
      total
      average
      list {
        _id
        menuItem
        price
        rating
        location
        description
        picture
      }
    }
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json

{
  "_id": "abc123",
  "name": "Sample Outlet",
  "displayPicture": "https://example.com/outlet_picture.jpg",
  "streetAddress": "123 Main Street",
  "type": "Restaurant",
  "meals": ["Breakfast", "Lunch", "Dinner"],
  "features": ["WiFi", "Outdoor Seating"],
  "minPrice": 10,
  "maxPrice": 50,
  "isOpen": true,
  "geolocation": {
    "coordinates": [123.456, -78.910]
  },
  "menus": [
    {
      "_id": "menu1",
      "name": "Menu Item 1",
      "price": 10.99,
      "description": "Description of Menu Item 1",
      "picture": "https://example.com/menu_item_1.jpg"
    },
    ...
  ],
  "reviews": {
    "total": 50,
    "average": 4.5,
    "list": [
      {
        "_id": "review1",
        "menuItem": "Menu Item 1",
        "price": 10.99,
        "rating": 4.8,
        "location": "Indoor",
        "description": "Great food and atmosphere!",
        "picture": "https://example.com/review_picture1.jpg"
      },
      ...
    ]
  }
}

```

Parameter | Type | Description
--------- | ------- | -----------
_id	| String | Represents the unique identifier of the outlet.
name | String | Represents the name of the outlet.
displayPicture | String | Contains the URL of the outlet's display picture.
streetAddress | String | Represents the street address of the outlet.
type | String | Represents the type or category of the outlet.
meals | [String] | Represents the meals offered by the outlet.
features | [String] | Represents the features or amenities of the outlet.
minPrice | Int | Represents the minimum price range at the outlet.
maxPrice | Int | Represents the maximum price range at the outlet.
isOpen | Boolean | Indicates whether the outlet is currently open.
geolocation | GeoLocation | Represents the geographical coordinates of the outlet.
menus	| [OutletMenu]	| Represents the menu items offered by the outlet.
reviews	| OutletReviewSummary	| Represents the summary of reviews for the outlet.

- `GeoLocation`: Object containing the latitude and longitude coordinates of the outlet.
  - `coordinates`: Array containing the latitude and longitude coordinates.
- `OutletMenu`: Object representing a menu item offered by the outlet.
    - `_id`: String representing the unique identifier of the menu item.
    - `name`: String representing the name of the menu item.
    - `price`: Float representing the price of the menu item.
    - `description`: String representing the description of the menu item.
    - `picture`: String containing the URL of the menu item's picture.
- `OutletReviewSummary`: Object representing the summary of reviews for the outlet.
    - `total`: Int representing the total number of reviews for the outlet.
    - `average`: Float representing the average rating of the reviews for the outlet.
    - `list`: Array containing individual reviews for the outlet, each with the following fields:
        - `_id`: String representing the unique identifier of the review.
        - `menuItem`: String representing the name of the menu item reviewed.
        - `price`: Float representing the price of the menu item reviewed.
        - `rating`: Float representing the rating given in the review.
        - `location`: String representing the location where the review was made.
        - `description`: String representing the description of the review.
        picture: String containing the URL of the review picture.



## Find Outlets

```graphql
query findOutlets($query: OutletFilterInput){
  findOutlets(query: $query){
    _id
    reviews {
      total
      average
    }
    isOpen
    name
    displayPicture
    minPrice
    maxPrice
    type
    distance
    geolocation {
      coordinates
    }
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```


## Add Menu Item

```graphql
mutation addOutletMenuItem($id: String, $data: OutletMenuInput){
  addOutletMenuItem(id: $id, data: $data){
    _id
    name
    streetAddress
    meals
    features
    type
    openingTime
    closingTime
    minPrice
    maxPrice
    menus {
      _id
      name
      price
      description
      picture
    }
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```



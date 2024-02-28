## Like Outlet

```graphql
mutation favouriteOutlet($id: String){
  favouriteOutlet(id: $id)
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

## Liked Outlets

```graphql
query findFavouriteOutlets{
  findFavouriteOutlets{
    _id
    name
    displayPicture
    type
    features
    meals
    minPrice
    maxPrice
    isOpen
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

## Most Liked Outlets

```graphql
query mostLikedOutlets{
  mostLikedOutlets{
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
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```









The outlet type depends on other nested data types like OutletMenu, OutletReviewSummary and geoLocation. 

The outlet menu data type is described in the table below.

Parameter | Type | Description
--------- | ------- | -----------
_id	| String | Represents the unique identifier of the menu.
outletId | String | Represents the ID of the outlet the menu belongs to.
name | String | Represents the name of the menu item.
picture | String | Contains the URL or path to the menu item's picture.
price | String | Represents the price of the menu item.
description | String | Provides a description of the menu item.
createdBy | String | Represents the user who created the menu item.
createdAt | String | Represents the date and time when the menu item was created.
updatedAt | String | Represents the date and time when the menu item was last updated.

The Outlet Review Summary data type is described in the table below.

Parameter | Type | Description
--------- | ------- | -----------
total | Int | Represents the total number of reviews.
average | Float | Represents the average rating of the reviews.
list | [OutletReview] | Represents a list of outlet reviews.

The outlet review data type
Parameter | Type | Description
--------- | ------- | -----------
_id | String | Represents the unique identifier of the review.
outletId | String | Represents the ID of the outlet the review belongs to.
outletName | String	| Represents the name of the outlet being reviewed.
description	| String | Provides a description or comment about the review.
rating | Int | Represents the rating given in the review.
menuItem | String | Represents the name of the menu item being reviewed.
price | Float | Represents the price of the menu item being reviewed.
picture | String | Contains the URL or path to the picture associated with the review.
location | String | Represents the location or context of the review.
createdBy | String | Represents the user who created the review.
createdAt | String | Represents the date and time when the review was created.
updatedAt | String | Represents the date and time when the review was last updated.

The geolocation data type
Parameter | Type | Description
--------- | ------- | -----------
type | String | Represents the type of the geo-cordinates according to mongodb. Should be "Point"
coordinates | [Float] | Represents the latitude and longitude cordinates



## Add Review

```graphql
mutation addOutletReview($data: OutletReviewInput){
  addOutletReview(data: $data){
    _id
    rating
    description
    price
    menuItem
    location
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

## Outlet Reviews

```graphql
query findOutletReviews($options: [FilterOption]){
  findOutletReviews(options: $options){
    _id
    menuItem
    price
    rating
    location
    description
    picture
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

## Most Rated Outlets

```graphql
query mostRatedOutlets{
  mostRatedOutlets{
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

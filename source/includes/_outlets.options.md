## Add Outlet Option 

```graphql
mutation addOutletOption($data: OutletOptionInput){
  addOutletOption(data: $data){
    _id
    name
    icon
    description
    class
    createdBy
    createdAt
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

## View Outlet Options

```graphql
query viewOutletOptions($options: [FilterOption]){
  viewOutletOptions(options: $options){
    _id
    name
    class
    icon
    description
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

## Update Outlet Option

```graphql
mutation updateOutletOption($data: OutletOptionInput){
  updateOutletOption(data: $data){
    _id
    name
    icon
    description
    class
    createdBy
    createdAt
  }
}
```

```javascript
```

> The above code samples return a JSON structured like this:

```json
```

# Favourites

The users can save their own favourites resources of the API

<aside class="notice">
Remember — All favourite endpoints need to be authenticated.
</aside>


| Field             | Description                                                                     | Type
| ------------------|:-----------------------------------------:                                      | -----:
| id                | Name                                                                            | Text
| resourceId        | Id of the resource                                                              | Text
| resourceType      | Type of resource                                                                | Text (dataset, layer, widget)
| userId            | Id of the owner user                                                            | Text
| createdAt         | Creation date                                                                   | Date



## Create Favourite

To create a favourite, you need to define all next fields in the request body. The required fields that compose a favourite are:

| Field             | Description                                                                     | Type
| ------------------|:-----------------------------------------:                                      | -----:
| resourceId        | Id of the resource                                                              | Text
| resourceType      | Type of resource                                                                | Text (dataset, layer, widget)


> To create a favourite, you have to do a POST with the following body:


```shell
curl -X POST https://api.resourcewatch.org/v1/favourite \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
 '{
   "resourceType":"<resourceType>",
   "resourceId": "<resourceId>"
  }'
```

## Get favourites

This endpoint returns the favourites of the logged user.

> To get all favourite of the logged user, you have to do a GET:


```shell
curl -X GET https://api.resourcewatch.org/v1/favourite \
-H "Authorization: Bearer <your-token>"
```

## Get favourite by id

This endpoint returns the favourite with id of the param. If the favourite belongs to other user or not exist, the endpoint returns 400.

> To get the favourite by id, you have to do a GET:


```shell
curl -X GET https://api.resourcewatch.org/v1/favourite/:id \
-H "Authorization: Bearer <your-token>"
```

## Delete favourite

This endpoint deletes the favourite with id of the param. If the favourite belongs to other user or not exist, the endpoint returns 400.

> To delete the favourite by id, you have to do a DELETE:


```shell
curl -X DELETE https://api.resourcewatch.org/v1/favourite/:id \
-H "Authorization: Bearer <your-token>"
```


# Dataset

## What is a Dataset?

A data set represents the raw data. We support four dataset types with different providers. It's also possible to have the same dataset on different applications.

## Supported dataset sources

### Carto
***(connectorType: 'rest', provider: 'cartodb')***
<a href="https://www.carto.com" target="_blank"><img src="images/dataset/carto.png" class="logo-third"/></a>
CARTO is an open, powerful, and intuitive platform for discovering and predicting the key insights underlying the location data in our world.

### ArcGIS
**(connectorType: 'rest', provider: 'featureservice')**
<a href="https://www.arcgis.com/features/index.html" target="_blank"><img src="https://www.arcgis.com/features/img/logo-esri.png" class="logo-third"/></a>
ArcGIS Online is a Complete, Cloud-Based Mapping Platform

### Google Earth Engine
**(connectorType: 'rest', provider: 'gee')**
<a href="https://earthengine.google.com/" target="_blank"><img src="https://earthengine.google.com/static/images/GoogleEarthEngine_Grey_108.png" class="logo-third"/></a>
Google Earth Engine combines a multi-petabyte catalog of satellite imagery and geospatial datasets with planetary-scale analysis capabilities and makes it available for scientists, researchers, and developers to detect changes, map trends, and quantify differences on the Earth's surface.

### CSV
**(connectorType: 'document', provider: 'csv')**

### JSON
**(connectorType: 'json', provider: 'rwjson')**

### WMS
**(connectorType: 'wms', provider: 'wms')**

## How obtain all datasets

To obtain all datasets:

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset
```

<aside class="success">
Remember — the response is jsonapi format
</aside>

> Example response:

```json
{
   "data":[
      {
        "id": "06c44f9a-aae7-401e-874c-de13b7764959",
        "type": "dataset",
        "attributes": {
          "application": [
            "prep",
            "rw"
          ],
          "name": "Historical Precipitation -- U.S. (Puget Sound Lowlands)",
          "subtitle": null,
          "dataPath": null,
          "attributesPath": null,
          "connectorType": "document",
          "provider": "csv",
          "userId": null,
          "connectorUrl": "https://raw.githubusercontent.com/fgassert/PREP-washington-observed-data/master/observed_precip.csv",
          "tableName": "index_06c44f9aaae7401e874cde13b7764959",
          "topics": [],
          "tags": [
            "",
            "observed",
            "washington",
            "local",
            "puget sound",
            "climate-weather",
            "precipitation"
          ],
          "legend": {},
          "clonedHost": {
            "hostProvider": null,
            "hostUrl": null,
            "hostId": null,
            "hostType": null,
            "hostPath": null
          },
          "status": "saved",
          "overwrite": false
        }
      },
   ],
   "links":{
      "first":"https://api.resourcewatch.org/v1/dataset?page%5Bnumber%5D=1",
      "prev":"https://api.resourcewatch.org/v1/dsataset?page%5Bnumber%5D=1",
      "next":"https://api.resourcewatch.org/v1/dsataset?page%5Bnumber%5D=2&page%5Bsize%5D=10",
      "last":"https://api.resourcewatch.org/v1/dsataset?page%5Bnumber%5D=64&page%5Bsize%5D=10",
      "self":"https://api.resourcewatch.org/v1/dsataset?page%5Bnumber%5D=1&page%5Bsize%5D=10"
   }
}
```

### Filter params

Available filters:

| Field         | Description           | Type
| ------------- |:-------------:| -----:|
| ids           | Filter the datasets by dataset ids                              | Text
| name           | Filter the datasets by dataset name                              | Text
| connectorType| Filter the datasets by dataset type (rest,json,wms,document)    | Text
| sort          | Sort json response by specific attributes                       | Text
| status        | Filter datasets on status (pending, active, disabled, all)      | Text
| provider      | Filter datasets on provider (cartodb, json, etc..)              | Text
| app           | Filter datasets on application (For filter or -- prep,gfw,etc.. -- for filter and prep@gfw@prep@etc..) | Text
| includes      | Include relational resources (metadata,layer,widget,vocabulary) | Text


> Return the datasets filtered whose id contains d02df2f6-d80c-4274-bb6f-f062061655c4

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?ids=d02df2f6-d80c-4274-bb6f-f062061655c4
```

> Return the datasets filtered by connector_type

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?connector_type=wms
```

> Sort by name

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?sort=name
```

> Filter datasets by status

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?status=failed
```

> Return the datasets filtered whose applications contain prep

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?app=prep
```

> Return the datasets filtered whose provider contain rwjson

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?provider=rwjson
```

> Return the datasets including layer

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?includes=layer
```

> Return the datasets including all available relational resources

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?includes=layer,widget,metadata,vocabulary
```

### Pagination params

| Field           | Description                | Type
| -------------   |:-------------:| -----:|
| page[size]      | Number elements per page   | Number
| page[number]    | Number of page             | Number

> Return the datasets of the page 2 with 5 elements per page

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset?page[size]=5&page[number]=2
```

## How obtain a specific dataset

### Filter params

Available filters:

| Field         | Description           | Type
| ------------- |:-------------:| -----:|
| app           | Filter datasets on application (For filter or -- prep,gfw,etc.. -- for filter and prep@gfw@prep@etc..)               | Text
| includes      | Include relational resources (metadata,layer,widget,vocabulary) | Text

> To obtain the dataset:

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset/51943691-eebc-4cb4-bdfb-057ad4fc2145
```
> Example response:

```json
{
  "data": {
    "id": "51943691-eebc-4cb4-bdfb-057ad4fc2145",
    "type": "dataset",
    "attributes": {
      "application": [
        "forest-atlas"
      ],
      "name": "Timber Production RDC (test)",
      "subtitle": null,
      "dataPath": null,
      "attributesPath": null,
      "connectorType": "document",
      "provider": "csv",
      "userId": "58750a56dfc643722bdd02ab",
      "connectorUrl": "http://wri-forest-atlas.s3.amazonaws.com/COD/temp/annual%20timber%20production%20DRC%20%28test%29%20-%20Sheet1.csv",
      "tableName": "index_51943691eebc4cb4bdfb057ad4fc2145",
      "topics": [],
      "tags": [],
      "legend": {
        "lat": "",
        "date": [
          "year"
        ],
        "long": "",
        "region": [],
        "country": []
      },
      "clonedHost": {
        "hostProvider": null,
        "hostUrl": null,
        "hostId": null,
        "hostType": null,
        "hostPath": null
      },
      "status": "saved",
      "overwrite": false
    }
  },
  "meta": {
    "status": "saved",
    "overwrite": false,
    "updatedAt": "2017-01-25T21:48:28.675Z",
    "createdAt": "2017-01-25T21:48:27.535Z"
  }
}
```

> To obtain the dataset including specific relational resource:

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset/06c44f9a-aae7-401e-874c-de13b7764959?includes=metadata
```

> To obtain the dataset including specific relational resource on specific application:

```shell
curl -X GET https://api.resourcewatch.org/v1/dataset/06c44f9a-aae7-401e-874c-de13b7764959?includes=metadata&app=rw
```

<aside class="success">
Remember — the response is jsonapi format
</aside>

## Creating a Dataset
Important things first! In order to create a dataset, you need an authorization token. Follow the steps of this [guide](#generate-your-own-oauth-token) to generate it.

To create a dataset, you need to define all of the required fields in the request body. The fields that compose a dataset are:

| Field             | Description                                                   | Type   | Values                                          | Required |
| ------------------|:-------------------------------------------------------------:| ------:| -----------------------------------------------:|  -------:|
| name              | Name of the dataset                                           | Text   | Any Text                                        | Yes
| subtitle          | Subtitle of the dataset                                       | Text   | Any Text                                        | No
| connectorType     | Connector type                                                | Text   | rest, json, document, wms                       | Yes
| provider          | The provider of the connector                                 | Text   | rwjson, csv, cartodb, featureservice, gee, wms  | Yes
| connectorUrl      | Url of the data                                               | Url    | Any url                                         | Yes for rest - Yes for json if data not present
| dataPath          | Path to access data (In case that the data is not the root object, this param specifies with attribute contain the data in the source data)               | Text   | Any valid JSON key                              | Yes
| application       | Application to which the dataset belongs                      | Array  | gfw, forest-atlas, rw, prep, aqueduct, data4sdg | Yes
| data              | JSON DATA only for json connector if connectorUrl not present | Array  | [{},{},{}]                                      | Yes for json if connectorUrl not present
| dataAttributes    | Data fields - for json connector if data present              | Object | {"key1": {"type": "string"},... }               | No
| tableName         | Table name                                                    | Text   | Any valid table name                            | Yes for GEE
| legend            | Legend for dataset. Keys for special fields                   | Object | Example: "legend": {"long": "123", "lat": "123", "country": ["pais"], "region": ["barrio"], "date": ["startDate", "endDate"]}} | No
| dataOverwrite     | Allows to overwrite dataset's data                            | Boolean| default false                                   | No                                 | No
| vocabularies      | Cluster of tags                                | Object | {"vocabularyOne": {"tags": [<tags>]},"vocabularyTwo": {"tags": [<tags>]}} | No

There are some differences between datasets types.

### Carto datasets
> To create a Carto dataset, you have to do a POST with the following body:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
 '{
   "dataset": {
      "connectorType":"rest",
      "provider":"cartodb",
      "connectorUrl":"<cartoUrl>",
      "application":[
         "your", "apps"
      ],
      "name":"Example Carto Dataset",
      more attributes...
   }
}'
```

> A real example:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "dataset": {
      "connectorType":"rest",
      "provider":"cartodb",
      "connectorUrl":"https://wri-01.carto.com/tables/wdpa_protected_areas/table",
      "application":[
         "gfw", "forest-atlas"
      ],
      "name":"World Database on Protected Areas -- Global"
   }
}'
```

<aside class="notice">
	Remember that create dataset is an authenticated endpoint!
</aside>

### ArcGIS
> To create a ArcGIS dataset, you have to do a POST with the following body:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "dataset": {
      "connectorType":"rest",
      "provider":"featureservice",
      "connectorUrl":"https://services.arcgis.com/uDTUpUPbk8X8mXwl/arcgis/rest/services/Public_Schools_in_Onondaga_County/FeatureServer/0?f=json",
      "application":[
         "prep"
      ],
      "name":"Uncontrolled Public-Use Airports -- U.S.",
      more attributes...
   }
}'
```

<aside class="notice">
  Remember that create dataset is an authenticated endpoint!
</aside>

### CSV
At the moment the CSV dataset service supports only semicolon-delimited files -- TSV files are not supported.

The `connectorUrl` must be an accessible CSV file, non-compressed - zip, tar, tar.gz, etc are not supported.

CSV datasets support some optional fields on the creation process. They are:

| Field             | Description                               | Type  | Values | Required |
| -------------     |:-----------------------------------------:| -----:| -----:|  -----:|
| legend            |                                                   | Object|               | No
| -- lat            | Name of column with latitude value                | Text  | Any word      | No
| -- long           | Name of column with longitude value               | text  | Any word      | No
| -- date           | Name of columns with date value (ISO Format)      | Array | Any list word | No
| -- region         | Name of columns with region value (ISO3 code)     | Array | Any list word | No
| -- country        | Name of columns with country value (ISO3 code)    | Array | Any list word | No


```shell
curl -X POST https://api.resourcewatch.org/v1/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "dataset": {
      "connectorType":"document",
      "provider":"csv",
      "connectorUrl":"<csvUrl>",
      "application":[
         "your", "apps"
      ],
      "legend": {
          "lat": "lat-column",
          "long": "long-column",
          "date": ["date1Column", "date2Column"],
          "region": ["region1Column", "region2Column"],
          "country": ["country1Column", "country2Column"]
      }
      "name":"Example CSV Dataset",
      more attributes...
   }
}'
```

> Real example:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "dataset": {
      "connectorType":"document",
      "provider":"csv",
      "connectorUrl":"http://gfw2-data.s3.amazonaws.com/alerts-tsv/glad_headers.csv",
      "application":[
         "gfw"
      ],
      "legend": {
          "lat": "lat",
          "long": "lon"
      },
      "name":"Glad points"
   }
}'
```
<aside class="notice">
  Remember that create dataset is an authenticated endpoint!
</aside>

### JSON
The JSON dataset service supports data from external json file or data as json array send in request body

The `connectorUrl` must be an accessible JSON file

JSON datasets support some optional fields in the creation process. They are:

| Field             | Description                               | Type  | Values | Required |
| ---------------   |:-----------------------------------------:| -----:| -----:|  -----:|
| data              | JSON DATA only for json connector if connectorUrl not present | Array | [{},{},{}]    | Yes for json if connectorUrl not present
| legend            |                                                               | Object|               | No
| -- lat            | Name of column with latitude value                            | Text  | Any word      | No
| -- long           | Name of column with longitude value                           | text  | Any word      | No
| -- date           | Name of columns with date value (ISO Format)                  | Array | Any list word | No
| -- region         | Name of columns with region value (ISO3 code)                 | Array | Any list word | No
| -- country        | Name of columns with country value (ISO3 code)                | Array | Any list word | No

<aside class="notice">
Remember — create dataset is an authenticated endpoint!
</aside>

## Updating a Dataset
In order to modify the dataset, you can PATCH a request.
It accepts the same parameters as the _create dataset_ endpoint, and you will need an authentication token.

> An example update request:

```shell
curl -X PATCH https://api.resourcewatch.org/v1/dataset/<dataset-id> \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json" -d \
'{
	"dataset": {
		"name": "Another name for the dataset"
	}
}'
```
<aside class="notice">
Remember — update dataset is an authenticated endpoint!
</aside>

## Deleting a Dataset
You can delete a dataset! Just send a DELETE request to the endpoint:

```shell
curl -X DELETE https://api.resourcewatch.org/v1/dataset/<dataset-id> \
-H "Authorization: Bearer <your-token>"
-H "Content-Type: application/json"
```
<aside class="notice">
Remember — delete dataset is an authenticated endpoint!
</aside>

## Cloning a Dataset
You can clone a dataset! Just send a POST request to the endpoint:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset/5306fd54-df71-4e20-8b34-2ff464ab28be/clone \
-H "Authorization: Bearer <your-token>"
-H "Content-Type: application/json" -d \
'{
  "dataset": {
    "dataset_url": "/query/5306fd54-df71-4e20-8b34-2ff464ab28be?sql=select%20%2A%20from%20data%20limit%2010",
    "application": [
      "your",
      "apps"
    ]
  }
}'
```

<aside class="notice">
Remember — clone dataset is an authenticated endpoint!
</aside>

## Concatenate Data
You can add more data to a dataset only if the dataset option overwrite (data_overwrite) is set to true.

Just send a POST request to the endpoint:

> Concatenate data using external data source:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset/:dataset_id/concat \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "connectorUrl":"<csvUrl>",
   "dataPath": "data... etc"
}'
```
> Concatenate data using JSON array in post body:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset/:dataset_id/concat \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "data": [{},{}]
}'
```

<aside class="notice">
Remember — concatenate dataset is an authenticated endpoint!
</aside>

## Overwrite Data
You can overwrite data in a dataset only if the dataset option overwrite (data_overwrite) is set to true.

Just send a POST request to the endpoint:

> Overwrite data using external data source:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset/:dataset_id/data-overwrite \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "connectorUrl":"<url>",
   "dataPath": "data"
}'
```

> Overwrite data using JSON array in post body:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset/:dataset_id/data-overwrite \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "data": [{},{}]
}'
```

<aside class="notice">
Remember — overwrite dataset is an authenticated endpoint!
</aside>


## Overwrite specific Data
You can update data in a dataset only if the dataset option overwrite (data_overwrite) is set to true.

Just send a POST request to the endpoint:

```shell
curl -X POST https://api.resourcewatch.org/v1/dataset/:dataset_id/data/:data_id \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{
   "data_id":":data_id",
   "data": {"a": 1}
}'
```

<aside class="notice">
Remember — overwrite dataset is an authenticated endpoint!
</aside>

## Delete specific Data
You can delete data in a dataset only if the dataset option overwrite (data_overwrite) is set to true.

Just send a DELETE request to the endpoint:

```shell
curl -X DELETE https://api.resourcewatch.org/v1/dataset/:dataset_id/data/:data_id \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"
```

<aside class="notice">
Remember — delete dataset is an authenticated endpoint!
</aside>

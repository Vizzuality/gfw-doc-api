# Dataset

## What is a Dataset?

Lorem Ipsum
"Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit..."
"There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain..."

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Donec vulputate ultrices condimentum. Sed venenatis arcu lacus, sit amet scelerisque nunc ullamcorper in. Donec sagittis placerat dolor, in faucibus ligula dapibus quis. Mauris scelerisque, velit id suscipit feugiat, enim ipsum vehicula arcu, aliquet ornare ipsum odio ac lectus. Ut suscipit tortor mauris, in euismod neque lacinia sed. Nam a nisi lacinia, posuere enim in, gravida erat.

## Dataset types

### Carto
<a href="https://www.carto.com" target="_blank"><img src="images/dataset/carto.png" class="logo-third"/></a>
Lorem Ipsum “Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit…” “There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain…”

### ArcGIS
<a href="https://www.arcgis.com/features/index.html" target="_blank"><img src="https://www.arcgis.com/features/img/logo-esri.png" class="logo-third"/></a>
Lorem Ipsum “Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit…” “There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain…”

### CSV
Lorem Ipsum “Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit…” “There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain…”

### JSON
Lorem Ipsum “Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit…” “There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain…”

### WMS
Lorem Ipsum “Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit…” “There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain…”

### Google Earth Engine (Coming soon...)
<a href="https://earthengine.google.com/" target="_blank"><img src="https://earthengine.google.com/static/images/GoogleEarthEngine_Grey_108.png" class="logo-third"/></a>
Lorem Ipsum “Neque porro quisquam est qui dolorem ipsum quia dolor sit amet, consectetur, adipisci velit…” “There is no one who loves pain itself, who seeks after it and wants to have it, simply because it is pain…”


## How create a Dataset?
Important! In order to create a dataset, you need an authorization token. Follow the steps of this [guide](#generate-your-own-oauth-token) to generate it. 

To create a dataset, you need to define all of the required fields. The fields that compose the dataset are:

| Field             | Description                               | Type  | Values                                          | Required |
| ------------------|:-----------------------------------------:| -----:| ---------------------------------------:        |  -------:|
| name              | Name of the dataset                       | Text  | Any Text                                        | Yes
| connectorType     | Type of connector.                        | Text  | rest, json, document                            | Yes
| connectorProvider | Provider of connector                     | text  | rwjson, csv, carto, featureservice, wms         | Yes
| connectorUrl      | Url of the data                           | Url   | Any url                                         | Yes
| application       | Application to which the dataset belongs  | Array | gfw, forest-atlas, rw, prep, aqueduct, data4sdg | Yes

### Carto
#### Creating Carto datasets
To create a Carto dataset, you have to do a POST with the following body

```shell
curl -X POST http://api.resourcewatch.org/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
 '{  
   "dataset": {  
      "connectorType":"rest", 
      "connectorProvider":"cartodb", 
      "connectorUrl":"<cartoUrl>", 
      "application":[  
         "your", "apps" 
      ], 
      "name":"Example Carto Dataset" 
   } 
}'
```

> Real example:

```shell
curl -X POST http://api.resourcewatch.org/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{  
   "dataset": {  
      "connectorType":"rest",
      "connectorProvider":"cartodb",
      "connectorUrl":"https://wri-01.carto.com/tables/wdpa_protected_areas/table",
      "application":[  
         "gfw", "forest-atlas"
      ],
      "name":"World Database on Protected Areas -- Global"
   }
}'
```

<aside class="success">
Remember --create dataset is an authenticated endpoint!
</aside>

#### Checking the dataset
To check the just created dataset, you can GET the dataset with its id.
This is not an authenticated endpoint.

> Real example:

```shell
curl -X GET http://api.resourcewatch.org/dataset/<dataset-id> \
-H "Content-Type: application/json"  -d \
'{  
}'

```
#### Updating the dataset
In order to modify the dataset, you can PUT a request.
It accepts the same parameters as the _create dataset_ endpoint, and you will need an authentication token.

```shell
curl -X PUT http://api.resourcewatch.org/dataset/<dataset-id> \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json" -d \
'{__
	"dataset": {__
		"name": "Another name for the dataset"
	}
}'
```
## Deleting a dataset
You can delete a dataset! Just send a DELETE action to the endpoint:

```shell
curl -X DELETE http://api.resourcewatch.org/dataset/<dataset-id> \
-H "Authorization: Bearer <your-token>"
-H "Content-Type: application/json"
```




### ArcGIS
To create a ArcGIS dataset, you have to do a POST with the following body

```shell
curl -X POST http://api.resourcewatch.org/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{  
   "dataset": {  
      "connectorType":"rest", 
      "connectorProvider":"featureservice", 
      "connectorUrl":"<arcgisUrl>", 
      "application":[  
         "your", "apps" 
      ], 
      "name":"Example ArcGIS Dataset" 
   } 
}'
```

> Real example:

```shell
curl -X POST http://api.resourcewatch.org/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{  
   "dataset": {  
      "connectorType":"rest",
      "connectorProvider":"featureservice",
      "connectorUrl":"http://hsip.geoplatform.gov/arcgis/rest/services/HSIP_Public/TransportationAir/MapServer/1?f=pjson",
      "application":[  
         "prep"
      ],
      "name":"Uncontrolled Public-Use Airports -- U.S."
   }
}'
```

<aside class="success">
Remember — create dataset is an authenticated endpoint!
</aside>

### CSV
At the current moment CSV Dataset only supports files delimited with semicolons. TSV files are not supported.

The `connectorUrl` must be an accessible CSV file. Zip, tar, tar.zip, tsv not supported.

CSV Dataset has some optional fields in the creation process, that they are:

| Field             | Description                               | Type  | Values | Required |
| -------------     |:-----------------------------------------:| -----:| -----:|  -----:|
| legend            |                                                   | Object|  | No
| -- lat           | Name of column with latitude value                | Text  | Any word | No
| -- long          | Name of column with longitude value               | text  | Any word | No
| -- date          | Name of columns with date value (ISO Format)      | Array | Any list word | No
| -- country       | Name of columns with country value (ISO3 code)    | Array | Any list word | No



```shell
curl -X POST http://api.resourcewatch.org/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{  
   "dataset": {  
      "connectorType":"rest", 
      "connectorProvider":"featureservice", 
      "connectorUrl":"<csvUrl>", 
      "application":[  
         "your", "apps" 
      ], 
      "legend": {
          "lat": "lat-column",
          "long": "long-column",
          "date": ["date1Column", "date2Column"],
          "country": ["country1Column", "country2Column"]
      }
      "name":"Example CSV Dataset" 
   } 
}'
```

> Real example:

```shell
curl -X POST http://api.resourcewatch.org/dataset \
-H "Authorization: Bearer <your-token>" \
-H "Content-Type: application/json"  -d \
'{  
   "dataset": {  
      "connectorType":"document",
      "connectorProvider":"csv",
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

<aside class="success">
Remember — create dataset is an authenticated endpoint!
</aside>


# Widget


## What is a Widget?
Is a graphic representation of a Dataset's data. The most of them are defined with [Vega grammar](#what-is-vega).

Widget contains the next fields:

| Field         | Description           | Type
| ------------- |:-------------:| -----:|
| userId        | Id of the owner                                           | Text
| Application   | Application to which the dataset belongs                  | Array
| slug          | Unique identifier of the widget                           | Text
| name          | Name of the widget                                        | Url
| description   | Description of the widget                                 | Array
| source        | TODO                                                      | Text
| sourceUrl     | TODO                                                      | Url
| layerId       | Id of the relationship with layer                         | Array
| dataset       | Id of the dataset that the widget belongs                 | Text
| authors       | Name of the authors                                       | Text
| queryUrl      | Url with the data of the chart shows                      | Text
| widgetConfig  | Vega configuration                                        | Object
| template      | If it's a template (base schema to create other widgets)  | Boolean
| default       | If it's a default widget for the dataset that it belongs  | Boolean
| status        | Status of the Widget                                      | Text
| published     | If it's available to use                                  | Text
| verified      | If it's verified by other user                            | Text



### What is Vega?

Vega is a visualization grammar, a declarative format for creating, saving and sharing interactive visualization designs. This wiki contains documentation and learning materials for getting up and running with Vega.
[More info](https://github.com/vega/vega/wiki)

## How obtain all widgets

To obtain all widgets:

```shell
curl -X GET http://api.resourcewatch.org/widget
```

<aside class="success">
Remember — the response is jsonapi format
</aside>

> Example response:

```json
{  
   "data":[  
      {  
         "id":"8f67fadd-d8df-4a28-82dd-a22a337d71b9",
         "type":"widget",
         "attributes":{  
            "userId":"5858f37140621f11066fb2f7",
            "application":[  
               "aqueduct"
            ],
            "slug":"ercentage-of-country-s-population-is-at-high-risk-of-hunger",
            "name":"Percentage of country's population at high risk of hunger.",
            "description":"",
            "source":"",
            "sourceUrl":"",
            "layerId":null,
            "dataset":"f1d24950-c764-4f90-950a-4541f798eb95",
            "authors":"",
            "queryUrl":"query/f1d24950-c764-4f90-950a-4541f798eb95?sql=select * from crops",
            "widgetConfig":{  
                ...
            },
            "template":false,
            "default":true,
            "status":"saved",
            "published":true,
            "verified":false
         }
      }
   ],
   "links":{  
      "first":"http://api.resourcewatch.org/widget?page%5Bnumber%5D=1",
      "prev":"http://api.resourcewatch.org/widget?page%5Bnumber%5D=1",
      "next":"http://api.resourcewatch.org/widget?page%5Bnumber%5D=2&page%5Bsize%5D=10",
      "last":"http://api.resourcewatch.org/widget?page%5Bnumber%5D=64&page%5Bsize%5D=10",
      "self":"http://api.resourcewatch.org/widget?page%5Bnumber%5D=1&page%5Bsize%5D=10"
   }
}
```

### Filter params

The filters available are:

| Field         | Description           | Type
| ------------- |:-------------:| -----:|
| name          | Filter the widgets whose name contains the filter text    | Text


> Return the widgets filtered whose name contains glad

```shell
curl -X GET http://api.resourcewatch.org/widget?name=glad
```

### Pagination params

| Field           | Description                | Type
| -------------   |:-------------:| -----:|
| page[size]      | Number elements per page   | Number
| page[number]    | Number of page             | Number

> Return the widgets of the page 2 with 5 elements per page

```shell
curl -X GET http://api.resourcewatch.org/widget?page[size]=5&page[number]=2
```


## Create a Widget



## Update a Widget



## Delete a Widget


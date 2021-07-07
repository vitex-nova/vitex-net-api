
The Vitex.Net REST API is fully described in an OpenAPI 3.0 [compliant document](swagger.json).
OpenAPI is a standard specification for describing REST APIs. OpenAPI descriptions allow both humans and machines to discover the capabilities of an API without needing to first read documentation or understand the implementation.


#### API list

<details>
 <summary><code>GET</code> <code><b>/devices</b></code> <code>Retrieves a list of devices, registered in the organization</code></summary>

##### Parameters

> | Name      |  Type     | In               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | access-token |  string   | header (reuired)  | access token need for authentication (generated for organization) |
> | medium    |  string   | query (optional)  | Filter by device specialization  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`                | see example below
> | `400`         | `application/json`                | `{"code":"400","message":"Bad Request"}`                            |

##### OK Responce example
> ```json
> [
>   {
>     "locationId": 1001,
>     "serialNo": "805849116",
>     "address": "Pivovarov 23",
>     "model": "UAB „Axis Industries“",
>     "medium": "Heat",
>     "installTime": "2020-01-01T00:00:00",
>     "readTime": "2021-07-07T12:57:00.0754756+03:00"
>   }
> ] 
> ```

##### Example cURL

> ```javascript
>  curl -X 'GET' \ 
> 'https://localhost/Devices?medium=Heat' \
> -H 'accept: text/plain'
> ```

</details>

<details>
 <summary><code>GET</code> <code><b>/devices/values</b></code> <code>Retrieves a list of devices values</code></summary>

##### Parameters

> | Name      |  Type     | In               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | access-token |  string   | header (reuired)  | access token need for authentication (generated for organization). |
> | from |  $date-time | query (required)  | Initial time of the period for which events will be retrieved.  |
> | till |  $date-time | query (required)  | End time of the period for which events will be retrieved.  |
> | locationId  |  $int32   | query (optional)  | Location id of the specified device for which events will be retrieved.  |
> | serialNo    |  string   | query (optional)  | Serial number of the specified device for which events will be retrieved.  |
> | medium    |  string   | query (optional)  | Filter by device specialization  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`                | see example below
> | `400`         | `application/json`                | `{"code":"400","message":"Bad Request"}`                            |

##### OK Responce example
> ```json
> [
>   {
>     "locationId": 10032,
>     "serialNo": "8058491223",
>     "time": "2021-07-07T10:16:56.379Z",
>     "value": "1.33",
>     "type": "Volume"
>   }
> ]
> ```

##### Example cURL

> ```javascript
>  curl -X 'GET' \
>  'https://localhost:44388/Devices/values?from=2021-07-07&till=2021-07-07&medium=Water' \
>  -H 'accept: text/plain'
> ```

</details>


<details>
 <summary><code>GET</code> <code><b>/devices/events</b></code> <code>Retrieves a list of devices events</code></summary>

##### Parameters

> | Name      |  Type     | In               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | access-token |  string   | header (reuired)  | access token need for authentication (generated for organization). |
> | from |  $date-time | query (required)  | Initial time of the period for which events will be retrieved.  |
> | till |  $date-time | query (required)  | End time of the period for which events will be retrieved.  |
> | locationId  |  $int32   | query (optional)  | Location id of the specified device for which events will be retrieved.  |
> | serialNo    |  string   | query (optional)  | Serial number of the specified device for which events will be retrieved.  |
> | medium    |  string   | query (optional)  | Filter by device specialization  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`                | see example below
> | `400`         | `application/json`                | `{"code":"400","message":"Bad Request"}`                            |

##### OK Responce example
> ```json
> [
>   {
>     "locationId": 100033,
>      "serialNo": "123213",
>      "time": "2021-07-07T10:22:39.077Z",
>      "type": "LowBattery"
>    }
>  ]
> ```

##### Example cURL

> ```javascript
>  curl -X 'GET' \
>  'https://localhost:44388/Devices/values?from=2021-07-07&till=2021-07-07&medium=Water' \
>  -H 'accept: text/plain'
> ```

</details>


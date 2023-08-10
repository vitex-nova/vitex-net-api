
The Vitex.Net REST API.

#### API list

<details>
 <summary><code>POST</code> <code><b>/api/v1/company/getDevices</b></code> <code>Retrieves a list of devices, registered in the organization with values.</code></summary>

##### Parameters

> | Name      |  Type     | In               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | Authorization |  string   | header (reuired)  | JWT access token needed for authentication (see) getToken method |
> | date  |  string   | body | Date for which meter values are returned. If no date is specified, the latest values are returned   |

##### date specified argument example
> ```json
> 
>  {
>     "date": "2023-07-01"
>  } 
> ```

##### date unspecified argument example
> ```json
> 
>  {
>  } 
> ```



##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`                | see example below
> | `400`         | `application/json`                | `{"code":"400","message":"Bad Request"}`                            |


##### OK Responce example
> ```json
> [
>   {
>        "address": "Зарічна X, кв. 1",
>        "lastSyncTime": "2023-07-26 04:00:08",
>        "dataTime": "2023-07-01 20:00:01",
>        "values": {
>            "errorFlags": "0",
>            "serialNo": "01234567",
>            "volume": "275"
>        }
>    },
>    {
>        "address": "Зарічна X, кв. 2",
>        "lastSyncTime": "2023-07-26 04:00:08",
>        "dataTime": "2023-07-01 20:00:01.00",
>        "values": {
>            "errorFlags": "0",
>            "serialNo": "01234568",
>            "volume": "550"
>        }
>    },
>]
> ```

##### JSON tags description

> | Name      |  Type     | description                                                           |
> |-----------|-----------|-----------------------------------------------------------------------|
> | address |  string | Address where meter is located |
> | lastSyncTime  |  string | Time of last data from meter |
> | dataTime |  string | Time of a nearest data for specified date. If request Date is null, then dataTime will ewual lastSyncTime.  |
> | values | object | A list of values for specified meter.  |


##### Example cURL

> ```javascript
>  curl -X 'POST' \
>  --header 'Authorization: Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWUsImlhdCI6MTY5MTY1OTgwOCwiZXhwIjoxNjkxNjYzNDA4fQ.qTRFRswXpI6gAUjWD6oRsXfTilZhK7DLhxXp89tSLD4'
>  -H 'Content-Type: application/json'
>  -d '{ "date": "2023-07-01" }'
>  'https://automate.in.ua/api/v1/company/getDevices' \
>  -H 'Accept: application/json'
> ```

</details>

<details>
 <summary><code>POST</code> <code><b>/api/v1/company/getToken</b></code> <code>Retrieves a token for specified user login</code></summary>

##### Parameters

> | Name      |  Type     | In               | description                                                           |
> |-----------|-----------|-------------------------|-----------------------------------------------------------------------|
> | username | string | body  | Username registered in the automate.in.ua (Owner or Local admin).  |
> | password | string | body  | Username password.  |

##### Responses

> | http code     | content-type                      | response                                                            |
> |---------------|-----------------------------------|---------------------------------------------------------------------|
> | `200`         | `application/json`                | see example below
> | `400`         | `application/json`                | `{"code":"400","message":"Username or password is incorrect"}`                            |

##### OK Responce example
> ```json
> {
>    "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiYWRtaW4iOnRydWUsImlhdCI6MTY5MTY1OTgwOCwiZXhwIjoxNjkxNjYzNDA4fQ.qTRFRswXpI6gAUjWD6oRsXfTilZhK7DLhxXp89tSLD4"
> }
> ```

##### Example cURL

> ```javascript
>  curl -X 'POST' \
>  'https://automate.in.ua/api/v1/company/getToken' \
>  -H 'Content-Type: application/json'
>  -d '{ "username": "owner", "password": "*****" }'
>  -H 'Accept: application/json'
> ```

</details>

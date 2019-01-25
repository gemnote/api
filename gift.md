## Gift API
### Summary
* Retrieve gifts `GET /api/v1/gifts/`  
* Retrieve a specific gift `GET /api/v1/gifts/:gift_id`  

### Retrieve gifts API

Retrieve gifts `GET /api/v1/gifts/` => Retrieves all gifts

Options:  

* `page[number]`: integer  
* `page[size]`: integer

example: 
`GET https://api.gemnote.com/api/v1/gifts/?page[number]=1&page[size]=1`

response:
success with `200 OK`

```
{
    "data": [
        {
            "id": "1",
            "type": "gifts",
            "attributes": {
                "name": "Chocolate Chips"
            }
        }
    ],
    "links": {
        "self": "https://api.gemnote.com/api/v1/gifts/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "first": "https://api.gemnote.com/api/v1/gifts/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "prev": null,
        "next": "https://api.gemnote.com/api/v1/gifts/?page%5Bnumber%5D=2&page%5Bsize%5D=1",
        "last": "https://api.gemnote.com/api/v1/gifts/?page%5Bnumber%5D=3&page%5Bsize%5D=1"
    },
    "meta": {
        "totalPages": 3,
        "totalItems": 3
    }
}
```

### Retrieve a single gift API

`GET /api/v1/gifts/:gift_id`


example:
`GET https://api.gemnote.com/api/v1/gifts/1`

response:
success with `200 OK`

```
{
    "data": {
        "id": "1",
        "type": "gifts",
        "attributes": {
            "name": "Chocolate Chips"
        }
    }
}
```

## Postcard API
### Summary
* Retrieve postcards `GET /api/v1/postcards/`  
* Retrieve a specific postcard `GET /api/v1/postcards/:postcard_id`  

### Retrieve postcards API

Retrieve postcards `GET /api/v1/postcards/` => Retrieves all postcards

Options:  

* `page[number]`: integer  
* `page[size]`: integer

example: 
`GET https://api.gemnote.com/api/v1/postcards/?page[number]=1&page[size]=1`

response:
success with `200 OK`

```
{
    "data": [
        {
            "id": "2",
            "type": "postcards",
            "attributes": {
                "name": "Birthday Card"
            }
        }
    ],
    "links": {
        "self": "https://api.gemnote.com/api/v1/postcards/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "first": "https://api.gemnote.com/api/v1/postcards/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "prev": null,
        "next": "https://api.gemnote.com/api/v1/postcards/?page%5Bnumber%5D=2&page%5Bsize%5D=1",
        "last": "https://api.gemnote.com/api/v1/postcards/?page%5Bnumber%5D=3&page%5Bsize%5D=1"
    },
    "meta": {
        "totalPages": 3,
        "totalItems": 3
    }
}
```

### Retrieve a single postcard API

`GET /api/v1/postcards/:postcard_id`


example:
`GET https://api.gemnote.com/api/v1/postcards/2`

response:
success with `200 OK`

```
{
    "data": {
        "id": "2",
        "type": "postcards",
        "attributes": {
            "name": "Birthday Card"
        }
    }
}
```

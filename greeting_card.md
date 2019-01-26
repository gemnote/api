## GreetingCard API
### Summary
* Retrieve greeting cards `GET /api/v1/greeting_cards/`  
* Retrieve a specific greeting card `GET /api/v1/greeting_cards/:greeting_card_id`  

### Retrieve greeting cards

Retrieve greeting cards `GET /api/v1/greeting_cards/` => Retrieves all greeting cards

Options:  

* `page[number]`: integer  
* `page[size]`: integer

example: 
`GET https://api.gemnote.com/api/v1/greeting_cards/?page[number]=1&page[size]=1`

response:
success with `200 OK`

```
{
    "data": [
        {
            "id": "2",
            "type": "greeting_cards",
            "attributes": {
                "name": "Birthday Card"
            }
        }
    ],
    "links": {
        "self": "https://api.gemnote.com/api/v1/greeting_cards/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "first": "https://api.gemnote.com/api/v1/greeting_cards/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "prev": null,
        "next": "https://api.gemnote.com/api/v1/greeting_cards/?page%5Bnumber%5D=2&page%5Bsize%5D=1",
        "last": "https://api.gemnote.com/api/v1/greeting_cards/?page%5Bnumber%5D=3&page%5Bsize%5D=1"
    },
    "meta": {
        "totalPages": 3,
        "totalItems": 3
    }
}
```

### Retrieve a single greeting card

`GET /api/v1/greeting_cards/:greeting_card_id`


example:
`GET https://api.gemnote.com/api/v1/greeting_cards/2`

response:
success with `200 OK`

```
{
    "data": {
        "id": "2",
        "type": "greeting_cards",
        "attributes": {
            "name": "Birthday Card"
        }
    }
}
```

## Shipment API
### Summary
* Retrieve shipments `GET /api/v1/shipments/`  
* Retrieve a specific shipment `GET /api/v1/shipments/:shipment_id`  
* Create a new shipment `POST /api/v1/shipments/`  

### API domain
`https://api.gemnote.com/`

### Authentication
<!--We are using http authentication:   -->
Add to http header key `AUTHORIZATION` with the value `Token xxxxxxxxxxxxxxxxxx`  
Get this token from your Gemnote account manager.

### Retrieve shipments API

Retrieve shipments `GET /api/v1/shipments/` => Retrieves all shipments

Options:  

* `page[number]`: integer  
* `page[size]`: integer
* `include`: allow - `gift`, `postcard`
  * GET /shipments/?`include`=gift
  * GET /shipments/?`include`=gift,postcard

example: 
`GET https://api.gemnote.com/api/v1/shipments/?page[number]=1&page[size]=1`

response:
success with `200 OK`

```
{
    "data": [
        {
            "id": "12",
            "type": "shipments",
            "attributes": {
                "companyId": 3,
                "giftId": 1,
                "postcardId": 2,
                "qty": 1,
                "recipientName": "Andy Liu",
                "recipientCompany": "SingSing",
                "phone": "123321234565",
                "email": "andyliu@sing.com",
                "addressOne": "1234 Sing St",
                "addressTwo": "",
                "city": "Song ",
                "state": "CA",
                "zipcode": "94123",
                "country": "USA",
                "fromName": "Leo",
                "fromEmail": "leo@ggg.com",
                "message": "Sing gift",
                "messageLanguage": "EN",
                "createdAt": "2018-12-08T00:52:17.512Z",
                "stage": "accepted",
                "errorReason": null
            },
            "relationships": {
                "gift": {
                    "data": {
                        "id": "1",
                        "type": "gifts"
                    }
                },
                "postcard": {
                    "data": {
                        "id": "2",
                        "type": "postcards"
                    }
                }
            }
        }
    ],
    "links": {
        "self": "http://localhost:3001/api/v1/shipments/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "first": "http://localhost:3001/api/v1/shipments/?page%5Bnumber%5D=1&page%5Bsize%5D=1",
        "prev": null,
        "next": "http://localhost:3001/api/v1/shipments/?page%5Bnumber%5D=2&page%5Bsize%5D=1",
        "last": "http://localhost:3001/api/v1/shipments/?page%5Bnumber%5D=7&page%5Bsize%5D=1"
    },
    "meta": {
        "totalPages": 7,
        "totalItems": 7
    }
}
```

### Retrieve a single shipment API

`GET /api/v1/shipments/:shipment_id`

Options:  

* `include`: allow - `gift`, `postcard`
  * GET /shipments/1?`include`=gift
  * GET /shipments/1?`include`=gift,postcard


example:
`GET https://api.gemnote.com/api/v1/shipments/5?include=gift,postcard`

response:
success with `200 OK`

```
{
    "data": {
        "id": "5",
        "type": "shipments",
        "attributes": {
            "companyId": 3,
            "giftId": 1,
            "postcardId": 2,
            "qty": 1,
            "recipientName": "Alonso Deckow",
            "recipientCompany": "Roob, Upton and Towne",
            "phone": "(348)743-2463 x0261",
            "email": "rory@fritschlittle.biz",
            "addressOne": "579 Trantow Tunnel",
            "addressTwo": "Suite 043",
            "city": "Port Floyd",
            "state": "Illinois",
            "zipcode": "51346-6079",
            "country": "Cayman Islands",
            "fromName": "Inga Willms",
            "fromEmail": "brent.strosin@langoshpouros.biz",
            "message": "Iusto sint laudantium omnis unde sed quaerat cupiditate. Aut similique dolores aut dolor ut. Eum nobis est provident porro temporibus autem. Suscipit atque ipsum est quam quo.",
            "messageLanguage": "Georgian",
            "createdAt": "2018-12-07T22:23:50.423Z",
            "stage": "accepted",
            "errorReason": null
        }
    },
    "relationships": {
            "gift": {
                "data": {
                    "id": "1",
                    "type": "gifts"
                }
            },
            "postcard": {
                "data": {
                    "id": "2",
                    "type": "postcards"
                }
            }
        }
    },
    "included": [
        {
            "id": "1",
            "type": "gifts",
            "attributes": {
                "name": "Chocolate Chips"
            }
        },
        {
            "id": "2",
            "type": "postcards",
            "attributes": {
                "name": "Birthday Card"
            }
        }
    ]
}
```

### Create a new shipment

`POST /api/v1/shipments/` 

Options:

* `giftId`:  required - the gift id
* `postcardId`: optional - will use default card if not given
* `qty`: required - quantity of the gift
* `recipientName`: required - the recipient name
* `recipientCompany`:  optional - the recipient company
* `phone`:  required (optional for USA shipments) - the recipient phone
* `email`: required - the recipient email
* `addressOne`:  required - the recipient address1
* `addressTwo`:  optional - the recipient address2
* `city`:  required - the recipient city
* `state`:  optional - the recipient state
* `zipcode`:  optional - the recipient zipcode
* `country`:  required - the recipient country, accpet ISO3166 country alpha2 or alpha3 or name
* `fromName`: optional - the sender's name
* `fromEmail`: optional - the sender's email
* `message`: optional - the gift's message
* `messageLanguage`: optional - the gift's message language

example:
`POST https://api.gemnote.com/api/v1/shipments/`

with `application/json` body
```
{
    "data": {
        "attributes": {
            "giftId": 1,
            "postcardId": 2,
            "qty": 2,
            "recipientName": "Eric Chow",
            "recipientCompany": "Asana",
            "phone": "(123)333-4567 x123",
            "email": "eric@asana.com",
            "addressOne": "123 ABC St",
            "addressTwo": "unit 2",
            "city": "Santa Clara",
            "state": "CA",
            "zipcode": "95050",
            "country": "United State",
            "fromName": "alex Chen",
            "fromEmail": "alex@gemnote.com",
            "message": "Gift for u",
            "messageLanguage": "en"
        }
    }
}
```

response:
success with `200 OK`

```
{
    "data": {
        "id": "13",
        "type": "shipments",
        "attributes": {
            "companyId": 3,
            "giftId": 1,
            "postcardId": 2,
            "qty": 2,
            "recipientName": "Eric Chow",
            "recipientCompany": "Asana",
            "phone": "(123)333-4567 x123",
            "email": "eric@asana.com",
            "addressOne": "123 ABC St",
            "addressTwo": "unit 2",
            "city": "Santa Clara",
            "state": "CA",
            "zipcode": "95050",
            "country": "United State",
            "fromName": "alex Chen",
            "fromEmail": "alex@gemnote.com",
            "message": "Gift for u",
            "messageLanguage": "en",
            "createdAt": "2018-12-10T21:43:14.917Z",
            "stage": "pending",
            "errorReason": null
        }
    },
    "relationships": {
            "gift": {
                "data": {
                    "id": "1",
                    "type": "gifts"
                }
            },
            "postcard": {
                "data": {
                    "id": "2",
                    "type": "postcards"
                }
            }
        }
    },
    "included": [
        {
            "id": "1",
            "type": "gifts",
            "attributes": {
                "name": "Chocolate Chips"
            }
        },
        {
            "id": "2",
            "type": "postcards",
            "attributes": {
                "name": "Birthday Card"
            }
        }
    ]
}
```

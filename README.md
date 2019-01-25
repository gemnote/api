## Gemnote API
### About
This is Gemnote's **BETA** API document.

### API domain
Production: `https://api.gemnote.com/`

Sandbox: `https://sandbox.gemnote.com/`

### Authentication
<!--We are using http authentication:   -->
Add to http header key `AUTHORIZATION` with the value `Token xxxxxxxxxxxxxxxxxx`  
Get this token from your Gemnote account manager.

### API token
* All sandbox key will start with `t_` prefix. e.g. `t_xxxxxxxxxxxxxxxxxxx`
* All production key will start with `p_` prefix. e.g. `p_xxxxxxxxxxxxxxxxxxx`

### Sandbox Environment 
All shipments on the sandbox server will leave the stage with `pending` and will not affect production data. 

### Retrieve resources from API
* [Shipment API](https://github.com/gemnote/api/blob/master/shipment.md)
* [Gift API](https://github.com/gemnote/api/blob/master/gift.md)
* [Postcard API](https://github.com/gemnote/api/blob/master/postcard.md)

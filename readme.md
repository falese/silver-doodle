
# Node Microservice Template

This is a stub microservice that can be cloned.

## Example Proxy

```javascript
var request = require('request');

const apiKey ="here lives an API key";
const zipCodeURL = 'https://www.zipcodeapi.com/rest/';

var distance = {
    find: function(req, res, next) {
      request(zipCodeURL + apiKey
        +'/distance.json/' + req.params.zipcode1 + '/'
        + req.params.zipcode2 + '/mile',
      function (error, response, body) {
        if (!error && response.statusCode == 200) {
          response=JSON.parse(body);
          res.send(response);

        } else {
          console.log(response.statusCode + response.body);
          res.send({distance: -1});
        }
      });
    }
};

module.exports = distance;

```

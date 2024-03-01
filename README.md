# ESTFEED

---
Release 16.02.2024

## How to split API description

Our goal is to move away from API descriptions on Github.
Short description how to rebundle global API to service specific API.

1. Install https://redocly.com/redocly-cli/ 


2. Download API json


3. Convert it to yml and save to file dh-public-test-api.yml


4. create directory for storing split stuff

    `mk unbundled`


5. run API splitter 

    `openapi split dh-public-test-api.yml --outDir unbundled/`


6. a result is openapi.yml which contains all endpoints

   `unbundled/openapi.yml`


7. create your own service specfic yml

   `cp unbundled/openapi.yml unbundled/customer.yml`


8. delete from `unbundled/customer.yml` unrelated paths so customer.yml will look like this


        `
        openapi: 3.0.1
        info: null
        title: Operational Platform
        version: 0.29.0
        servers:
        - url: 'http://host'
          description: Generated server url
          tags:
          - name: Customer
            description: 'API to create, read, and update customer information.'
            paths:
            /api/v1/customer:
            $ref: paths/api_v1_customer.yml
            /api/v1/customer/search:
            $ref: paths/api_v1_customer_search.yml
            /api/v1/customer/change:
            $ref: paths/api_v1_customer_change.yml
            components: null
            securitySchemes: null
            JWTAuth: null
            type: openIdConnect
            openIdConnectUrl: 'https://host/realms/myrealm/.well-known/openid-configuration
        `
9. Create directory for re-bundled API

    `mkdir bundled`    


10. Bundle new API

    `openapi bundle unbundled/customer.yml -o bundled/customer.yml`

Based on: https://www.wellshapedwords.com/posts/split-files-to-save-time/
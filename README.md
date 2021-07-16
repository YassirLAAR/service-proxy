# service-proxy
Proxy service, this project contain the configuration files of the following projects:

[company-service](https://github.com/YassirLAAR/company-service "company-service")
[service-config](https://github.com/YassirLAAR/service-config "service-config")
[service-register](https://github.com/YassirLAAR/service-register "service-config")

### How to run correctly

#### Create Configuration

Using Git Bash, run the following commands

```sh
$ cd ~
$ cd cloud-conf
$ touche cloud-conf\proxy-service.properties
``` 

Once the file created, Update it with this configuartion:

application.properties:

    zParam=7197
    

Then back to the Git Bash:
```sh
$ cd cloud-conf
$ git add . 
$ git commit -m "Proxy Config added"
```

#### Running the application

If you're using eclise, rerun **service-register** go to the class **ServiceProxyApplication** and run it as JavaApplication
Run **company-service** in differents ports by updating the file *boostrap.properties*

```sh
    spring.application.name=company-service
    spring.cloud.config.uri=http://localhost:8888/
    management.endpoints.web.exposure.include=*
    server.port=8082
```

#### Testing the application

In a browser, use this url to restor configurations:
* http://localhost:8080/companies
```json
    {
      "_embedded" : {
        "companies" : [ {
          "name" : "A",
          "price" : 694.3828765056754,
          "_links" : {
            "self" : {
              "href" : "http://localhost:8083/companies/1"
            },
            "company" : {
              "href" : "http://localhost:8083/companies/1"
            }
          }
        }, {
          "name" : "B",
          "price" : 631.3745911402394,
          "_links" : {
            "self" : {
              "href" : "http://localhost:8083/companies/2"
            },
            "company" : {
              "href" : "http://localhost:8083/companies/2"
            }
          }
        }, {
          "name" : "C",
          "price" : 637.6241517550166,
          "_links" : {
            "self" : {
              "href" : "http://localhost:8083/companies/3"
            },
            "company" : {
              "href" : "http://localhost:8083/companies/3"
            }
          }
        } ]
      },
      "_links" : {
        "self" : {
          "href" : "http://localhost:8083/companies"
        },
        "profile" : {
          "href" : "http://localhost:8083/profile/companies"
        }
      },
      "page" : {
        "size" : 20,
        "totalElements" : 3,
        "totalPages" : 1,
        "number" : 0
      }
    }
```


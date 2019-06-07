## Delete Endpoint

Ok, so now we've dynamically added in an endpoint...lets remove it by the SDS server's custom API and emptying out its hosts: []

```
curl -X PUT --header 'Content-Type: application/json' --header 'Accept: application/json' -d '{
  "hosts": [  ]
}' http://localhost:8080/edsservice/myservice
```{{execute T7}}

Now is you try to send a request to Envoy, you should see no healthy upstream message from envoy:

```curl -v http://localhost:10000```{{execute T7}}

```
HTTP/1.1 503 Service Unavailable
content-length: 19
content-type: text/plain
date: Fri, 07 Jun 2019 03:28:08 GMT
server: envoy

no healthy upstream$
```
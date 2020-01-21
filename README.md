

![Icone](https://camo.githubusercontent.com/94fc3fbc60e18868dc68c202da3c8223ff980f2b/687474703a2f2f7069736b656c2d696d6773746f72652d622e61707073706f742e636f6d2f696d672f64353830653936652d626438612d313165362d623135372d3939343963616434643630392e676966)



# API de Rastreamento de Encomendas dos Correios - Link&Track
### Serviço REST que retorna o JSON com os eventos de rastreamento de encomendas dos correios. 

# ÍNDICE
## [COMO USAR](#markdown-header-como-usar)
## [EXEMPLOS](#markdown-header-exemplos)





### COMO USAR

BASEURL: https://api.linketrack.com/track/json

PARAMS:
 - user: Nome de usuário
 - token: Token do usuário
 - codigo: Código de Rastreamento da Encomenda
 
> Os exemplos abaixo utilizam o usuário **teste**. Para solicitar um novo usuário e token envie e-mail para [api@linketrack.com](mailto://api@linketrack.com)


### EXEMPLOS

#### HTTP
```
GET https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR
```

#### NODEJS - HTTP NATIVE

```js
var https = require('follow-redirects').https;
var fs = require('fs');

var options = {
  'method': 'GET',
  'hostname': 'api.linketrack.com',
  'path': '/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR',
  'headers': {
  },
  'maxRedirects': 20
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

req.end();
```

#### NODEJS - USANDO REQUEST

```js
var request = require('request');
var options = {
  'method': 'GET',
  'url': 'https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR',
  'headers': {
  }
};
request(options, function (error, response) { 
  if (error) throw new Error(error);
  console.log(response.body);
});

```


#### NODEJS - USANDO UNIREST

```js
var unirest = require('unirest');
var req = unirest('GET', 'https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR')
  .end(function (res) { 
    if (res.error) throw new Error(res.error); 
    console.log(res.raw_body);
  });
```




#### C# USANDO RESTSHARP
```c#
var client = new RestClient("https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR");
client.Timeout = -1;
var request = new RestRequest(Method.GET);
IRestResponse response = client.Execute(request);
Console.WriteLine(response.Content);
```


#### JAVA USANDO UNIREST
```java
Unirest.setTimeouts(0, 0);
HttpResponse<String> response = Unirest.get("https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR")
  .asString();
```


#### JAVA USANDO OKHTTP
```java
OkHttpClient client = new OkHttpClient().newBuilder()
  .build();
Request request = new Request.Builder()
  .url("https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR")
  .method("GET", null)
  .build();
Response response = client.newCall(request).execute();
```

#### PHP cURL
```php
<?php

$curl = curl_init();

curl_setopt_array($curl, array(
  CURLOPT_URL => "https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR",
  CURLOPT_RETURNTRANSFER => true,
  CURLOPT_ENCODING => "",
  CURLOPT_MAXREDIRS => 10,
  CURLOPT_TIMEOUT => 0,
  CURLOPT_FOLLOWLOCATION => true,
  CURLOPT_HTTP_VERSION => CURL_HTTP_VERSION_1_1,
  CURLOPT_CUSTOMREQUEST => "GET",
));

$response = curl_exec($curl);

curl_close($curl);
echo $response;
```


#### PYTHON REQUESTS
```python
import requests

url = "https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR"

payload = {}
headers= {}

response = requests.request("GET", url, headers=headers, data = payload)

print(response.text.encode('utf8'))
```

#### RUBY 
```ruby
require "uri"
require "net/http"

url = URI("https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR")

https = Net::HTTP.new(url.host, url.port);
https.use_ssl = true

request = Net::HTTP::Get.new(url)

response = https.request(request)
puts response.read_body
```

#### SWIFT
```swift
import Foundation

var semaphore = DispatchSemaphore (value: 0)

var request = URLRequest(url: URL(string: "https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR")!,timeoutInterval: Double.infinity)
request.httpMethod = "GET"

let task = URLSession.shared.dataTask(with: request) { data, response, error in 
  guard let data = data else {
    print(String(describing: error))
    return
  }
  print(String(data: data, encoding: .utf8)!)
  semaphore.signal()
}

task.resume()
semaphore.wait()
```

#### GO
```go

package main

import (
  "fmt"
  "net/http"
  "io/ioutil"
)

func main() {

  url := "https://api.linketrack.com/track/json?user=teste&token=1abcd00b2731640e886fb41a8a9671ad1434c599dbaa0a0de9a5aa619f29a83f&codigo=LX002249507BR"
  method := "GET"

  client := &http.Client {
  }
  req, err := http.NewRequest(method, url, nil)

  if err != nil {
    fmt.Println(err)
  }
  res, err := client.Do(req)
  defer res.Body.Close()
  body, err := ioutil.ReadAll(res.Body)

  fmt.Println(string(body))
}
```




#### RESPOSTA JSON
*200 - OK*
    
```json
{
  "codigo": "LX002249507BR",
  "servico": "PAC - Encomenda Econômica",
  "host": "dw",
  "quantidade": 12,
  "eventos": [
    {
      "data": "24/10/2019",
      "hora": "10:40",
      "local": "CURITIBA/PR",
      "status": "Devolução autorizada pela Receita Federal",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "11/09/2019",
      "hora": "00:00",
      "local": "CURITIBA/PR",
      "status": "Pagamento não efetuado no prazo",
      "subStatus": [
        "Objeto em análise de destinação"
      ]
    },
    {
      "data": "15/08/2019",
      "hora": "13:37",
      "local": "CURITIBA/PR",
      "status": "Encaminhado para fiscalização aduaneira",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "13/08/2019",
      "hora": "16:53",
      "local": "CURITIBA/PR",
      "status": "Encaminhado para fiscalização aduaneira",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "13/08/2019",
      "hora": "16:13",
      "local": "CURITIBA/PR",
      "status": "Encaminhado para fiscalização aduaneira",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "13/08/2019",
      "hora": "14:34",
      "local": "CURITIBA/PR",
      "status": "Encaminhado para fiscalização aduaneira",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "09/08/2019",
      "hora": "18:11",
      "local": "CURITIBA/PR",
      "status": "Aguardando pagamento",
      "subStatus": [
        "<span class=\"minhasImportacoes\">Acesse o ambiente <a href=\"https://www.correios.com.br/encomendas-logistica/minhas-importacoes/minhas-importacoes\" target=\"_blank\">Minhas Importações</a></span>"
      ]
    },
    {
      "data": "09/08/2019",
      "hora": "15:23",
      "local": "CURITIBA/PR",
      "status": "Encaminhado para fiscalização aduaneira",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "09/08/2019",
      "hora": "12:22",
      "local": "CURITIBA/PR",
      "status": "Objeto encaminhado",
      "subStatus": [
        "de CENTRO INTERNACIONAL PR - CURITIBA/PR para Fiscalizacao Aduaneira - /BR"
      ]
    },
    {
      "data": "09/08/2019",
      "hora": "12:22",
      "local": "CURITIBA/PR",
      "status": "Encaminhado para fiscalização aduaneira",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "31/07/2019",
      "hora": "15:10",
      "local": "CURITIBA/PR",
      "status": "Informações prestadas pelo cliente em análise",
      "subStatus": [
        "Registrado por CENTRO INTERNACIONAL PR - CURITIBA/PR"
      ]
    },
    {
      "data": "31/07/2019",
      "hora": "14:15",
      "local": "CURITIBA/PR",
      "status": "Faltam informações. Sua ação é necessária",
      "subStatus": [
        "<span class=\"minhasImportacoes\">Acesse o ambiente <a href=\"https://www.correios.com.br/encomendas-logistica/minhas-importacoes/minhas-importacoes\" target=\"_blank\">Minhas Importações</a></span>"
      ]
    }
  ],
  "time": 1158.205951999873
}
```

### RESPOSTA 404 - NOT_FOUND*
```json
{
  "codigo": "AA123123123BR",
  "servico": "SEDEX - Encomenda Expressa",
  "host": "dw",
  "quantidade": 0,
  "eventos": [
    
  ],
  "time": 826.1034389999695
}
```

### Autor
Chipy Tux - <chipytux@gmail.com>
    
### License:
MIT

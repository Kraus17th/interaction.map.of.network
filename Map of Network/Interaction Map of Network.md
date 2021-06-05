# interaction.map.of.network


In OS:

![OS](https://github.com/Kraus17th/Interaction.Map.of.Network/blob/main/Map%20of%20Network/Assets/os.jpg)

Wireshark

![Wireshark](https://github.com/Kraus17th/Interaction.Map.of.Network/blob/main/Map%20of%20Network/Assets/wireshark.jpg)



1. Client (41028) > Server.1 (9001) (Request):

   ```http
   PUT http://localhost:9001/users HTTP/1.1
   Host: localhost:9001
   User-Agent: Go-http-client/1.1
   Content-Length: 26
   Content-Type: application/x-www-form-urlencoded
   Accept-Encoding: gzip
   {"login":"user",
   "password":"111111"}
   ```

2. Server.1 (9001) > Client (41028) (Response):

   ```http
   HTTP/1.1 200 OK
   Content-Type: application/json
   Date: Wed, 02 Jun 2021 09:24:41 GMT
   Content-Length: 496
   {"token":"eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjIsImxvZ2luIjoidXNlciIsInJvbGVzIjpbIlVTRVIiXSwiaWF0IjoxNjIyNjI1ODgxLCJleHAiOjE2MjI2Mjk0ODF9.JbsL4MqT3q4bRVhjR8dg8KDvzKuQ9jFY8zoYzYqR_tztXP9kGm8hT2Ryxfi0G-CyJdnDfP5wEmzsyEAxg1QBieE_4z8rl74cXF3jP6DDk_6TvRR46ew-RhcwVYSIS49njAaXZ8vHzF16dw66yP04ov6D27kKwpfgQ7PyniC_jqlIlKwRhjsKwj-dUhRsP8k1ao2GEbZ8YCR9MN0pIR0dTQlH55fMeG_TenR1s6JKqHTIQp-Yi8Z_q9SV_uJi-9svPYHndgniXoKV1oaONs24xilvC374Kd-ypUVnZchxTw0DSEPFvcYvMnYFqXhdlXQzv9jg0u9AXIS7Lnx6yhAbLA"}
   ```

3. Client (39916) > Server.2 (9002) (Request):

   ```http
   GET /api/transactions HTTP/1.1
   Host: localhost:9002
   User-Agent: Go-http-client/1.1
   Authorization: eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjIsImxvZ2luIjoidXNlciIsInJvbGVzIjpbIlVTRVIiXSwiaWF0IjoxNjIyNjI1ODgxLCJleHAiOjE2MjI2Mjk0ODF9.JbsL4MqT3q4bRVhjR8dg8KDvzKuQ9jFY8zoYzYqR_tztXP9kGm8hT2Ryxfi0G-CyJdnDfP5wEmzsyEAxg1QBieE_4z8rl74cXF3jP6DDk_6TvRR46ew-RhcwVYSIS49njAaXZ8vHzF16dw66yP04ov6D27kKwpfgQ7PyniC_jqlIlKwRhjsKwj-dUhRsP8k1ao2GEbZ8YCR9MN0pIR0dTQlH55fMeG_TenR1s6JKqHTIQp-Yi8Z_q9SV_uJi-9svPYHndgniXoKV1oaONs24xilvC374Kd-ypUVnZchxTw0DSEPFvcYvMnYFqXhdlXQzv9jg0u9AXIS7Lnx6yhAbLA
   Accept-Encoding: gzip
   ```

4. Server.2 (40048) > Server.3 (9003) (Request):

   ```http
   GET /api/transactions HTTP/1.1
   Host: localhost:9003
   User-Agent: Go-http-client/1.1
   X-Userid: 2
   Accept-Encoding: gzip
   ```

5. Server.3 (54578) > Server.4 (9004) (Request):

   ```http
   GET /api/transactions HTTP/1.1
   Host: localhost:9004
   User-Agent: Go-http-client/1.1
   X-Userid: 2
   Accept-Encoding: gzip
   ```

6. Server.4 (9004) > Server.3 (54578) (Response):

   ```http
   HTTP/1.1 200 OK
   Content-Type: application/json
   Date: Wed, 02 Jun 2021 09:24:41 GMT
   Content-Length: 227
   
   [{"id":1,"userId":2,"category":"auto","amount":1000000,"created":1622625845},{"id":2,"userId":2,"category":"auto","amount":100000,"created":1622625845},{"id":3,"userId":2,"category":"food","amount":100000,"created":1622625845}]
   ```

7. Server.3 (9003) > Server.2 (40048) (Response):

   ```http
   HTTP/1.1 200 OK
   Content-Type: application/json
   Date: Wed, 02 Jun 2021 09:24:41 GMT
   Content-Length: 291
   
   {"transactions":[{"id":1,"userId":2,"category":"auto","amount":1000000,"created":1622625845},{"id":2,"userId":2,"category":"auto","amount":100000,"created":1622625845},{"id":3,"userId":2,"category":"food","amount":100000,"created":1622625845}],"categoryStats":{"auto":1100000,"food":100000}}
   ```

8. Server.2 (9002) > Client (39916) (Response):

   ```http
   HTTP/1.1 200 OK
   Content-Type: application/json
   Date: Wed, 02 Jun 2021 09:24:41 GMT
   Content-Length: 291
   
   {"transactions":[{"id":1,"userId":2,"category":"auto","amount":1000000,"created":1622625845},{"id":2,"userId":2,"category":"auto","amount":100000,"created":1622625845},{"id":3,"userId":2,"category":"food","amount":100000,"created":1622625845}],"categoryStats":{"auto":1100000,"food":100000}}
   ```

# Token



## Server.1  (keys1.dir)

```asciiarmor
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxFv8lbJ+njQ1thnz25qZAsEQB0yRhz+Ri3X9r9+6M97dus80
BRdkRaQPHxJxNaAKQc1HylYqBITS3mMSGjwsJ6WtlIAoR8PBUY8fnidjVagTkLFO
dzZ+rEEOJtRB0zLUmeDxxDg2qMan2ijn2nksAshRhJQ8eNc84cdZ0pPdKz3ay774
Ccj3gHcYHmadICs6nIjcVuJ9S1z16sT7LBiOWR6hlVeV/lJ+1TYrhiTPW+j7CZaX
w/BbQZ+mKi/6QpY39tQntz73WIlqGO6uhLxpgUtFI+aZrcLXTHSWiSJLs9KAx++Q
5KMF86NOPu8poA+f1twa3jN1NM/lQQBwKhmXbQIDAQABAoIBAQCKbC5LeWE5NaUH
kpQOI5XqEx+xhZCxv2Zi4fLMoPMqzdmRb7BERpExZs4iIWYdX4zbhlMtmEBWnyvo
Cf8g73pRGMKdBRtgO+d0D2lCnJGyOKJSRiwCbjAuTk4joU4mDJdDQwgsQ1SE9kYt
zNhlczZLX9vXkohux4zrvRTdFc+8QsoojlKwRTpRUFoJW7V5yfU9BqrujTqhWdDm
m8VlcvWgPsX5djyDamgZuGr7aKjAMI4bXGahBIQdkWnpRnGu5e1gM1tCOqt/0WiR
iTRkew0P6tyLqaCzlTheOEOGil74d8IANfOBO3ePqObuGBuBtsFzr9OgJ7MreXH0
03CAsfUhAoGBAOpLN7hMNpw2wQp3DLXt9sn5MTyffEYVjK9IWeDErZNIDCKFXgwD
mwstTBSIXA0ORPs5YGJJ+ZbvRUnWsViMvT9tyKu365hrFTpDl28boXdSVSQ7D3ig
NmTF6HG5Yg+0v3cQD/dDcoi3YlJY7Bnw9KNMv6xemwzuq5A4Xv5RTndjAoGBANaN
Eh0gmmj+YaHhY+2MjO0TQFn1PMLxbwFvPJ/IfxbMg+ZZAXDV7fT8LlSWY4hnp44W
dZadlkdNZt1Dqs+xuiN0yE6HeLVa9rB1tpxhneKm3y+L2SThc+laQl7jnzkZaa//
HEQURfCmmLgJTZ0gtUc4Z9bN/rNC1gRdUD+wFfbvAoGBANqyN2KqkVcjrPGNyqmP
ZIuHNbR20lPBDb8X8/1g2PzfhaQ7hVwFiZXXRGruFa6CIVW3awaUMov28GBKLOSR
Cp3IZkYTubBeVEQ8j4BA9GkiyyK0lm5sbhmGusBc4PH0L7x9m8mcha6kLvza0Bgu
2MwNeeT1shlSN4a5d8JANtQtAoGAH09fAVksr33QCau2xYfpWP+iOH6Na3WIWZE+
K6M6yLz30rnSeAEAROw4Zqe7xsA5t4aXim9c6vLkvA2P89df7qSwRqWGfBDWR1Im
YBPu0pC/qVSjT7qHC9rcLLTTG6YVwlVcbqL2wfPN/a194hxP2CDnJnXRYZ+zU9e6
SlEMI4kCgYBa11Nlkt2YwHdpu0MAvTeA76983aQ20Tczx4qX17aOLdDdnVVQzoqr
tZWXbWOrRJohpU/kSJYxrcK3fFdPJ2ctwe7jqVTylEo3yfpdgLLd+5ZQRt/+4kt6
BTS1gNCQSJt8M2QznbIlNyWXi3jpjjKp7uyHJT/3r++5dfLmf5JE1g==
-----END RSA PRIVATE KEY-----
```

```asciiarmor
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxFv8lbJ+njQ1thnz25qZ
AsEQB0yRhz+Ri3X9r9+6M97dus80BRdkRaQPHxJxNaAKQc1HylYqBITS3mMSGjws
J6WtlIAoR8PBUY8fnidjVagTkLFOdzZ+rEEOJtRB0zLUmeDxxDg2qMan2ijn2nks
AshRhJQ8eNc84cdZ0pPdKz3ay774Ccj3gHcYHmadICs6nIjcVuJ9S1z16sT7LBiO
WR6hlVeV/lJ+1TYrhiTPW+j7CZaXw/BbQZ+mKi/6QpY39tQntz73WIlqGO6uhLxp
gUtFI+aZrcLXTHSWiSJLs9KAx++Q5KMF86NOPu8poA+f1twa3jN1NM/lQQBwKhmX
bQIDAQAB
-----END PUBLIC KEY-----
```

## Server.2 (keys2.dir)

```asciiarmor
-----BEGIN PUBLIC KEY-----
MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAxFv8lbJ+njQ1thnz25qZ
AsEQB0yRhz+Ri3X9r9+6M97dus80BRdkRaQPHxJxNaAKQc1HylYqBITS3mMSGjws
J6WtlIAoR8PBUY8fnidjVagTkLFOdzZ+rEEOJtRB0zLUmeDxxDg2qMan2ijn2nks
AshRhJQ8eNc84cdZ0pPdKz3ay774Ccj3gHcYHmadICs6nIjcVuJ9S1z16sT7LBiO
WR6hlVeV/lJ+1TYrhiTPW+j7CZaXw/BbQZ+mKi/6QpY39tQntz73WIlqGO6uhLxp
gUtFI+aZrcLXTHSWiSJLs9KAx++Q5KMF86NOPu8poA+f1twa3jN1NM/lQQBwKhmX
bQIDAQAB
-----END PUBLIC KEY-----
```

## Как работает token в данном сервисе?

Для того чтобы это понять нужно посмотреть на сам **token**. 

```json
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOjIsImxvZ2luIjoidXNlciIsInJvbGVzIjpbIlVTRVIiXSwiaWF0IjoxNjIyNjI1ODgxLCJleHAiOjE2MjI2Mjk0ODF9.JbsL4MqT3q4bRVhjR8dg8KDvzKuQ9jFY8zoYzYqR_tztXP9kGm8hT2Ryxfi0G-CyJdnDfP5wEmzsyEAxg1QBieE_4z8rl74cXF3jP6DDk_6TvRR46ew-RhcwVYSIS49njAaXZ8vHzF16dw66yP04ov6D27kKwpfgQ7PyniC_jqlIlKwRhjsKwj-dUhRsP8k1ao2GEbZ8YCR9MN0pIR0dTQlH55fMeG_TenR1s6JKqHTIQp-Yi8Z_q9SV_uJi-9svPYHndgniXoKV1oaONs24xilvC374Kd-ypUVnZchxTw0DSEPFvcYvMnYFqXhdlXQzv9jg0u9AXIS7Lnx6yhAbLA
```

Он состоит из 3 частей и разделён точками:

В первой части сразу узнаётся base64. Здесь содержится информация о типе всего шифрования token'а, это **"RS256"**.

```json
eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ9
```

```json
{
  "alg": "RS256",
  "typ": "JWT"
}
```

Вторую часть можно тоже расшифровать используя base64. Тут представлены **системные данные о клиенте**. 

```json
eyJ1c2VySWQiOjIsImxvZ2luIjoidXNlciIsInJvbGVzIjpbIlVTRVIiXSwiaWF0IjoxNjIyNjI1ODgxLCJleHAiOjE2MjI2Mjk0ODF9
```

```json
{
  "userId": 2,
  "login": "user",
  "roles": [
    "USER"
  ],
  "iat": 1622625881,
  "exp": 1622629481
}
```

Третья часть не поддалась так просто, поэтому нужно пришлось найти специальный ресурс для рассшифровки RS256. Оттуда я и узнал, что в последней части сообщения находиться **цифровая подпись первого сервера**.

```json
JbsL4MqT3q4bRVhjR8dg8KDvzKuQ9jFY8zoYzYqR_tztXP9kGm8hT2Ryxfi0G-CyJdnDfP5wEmzsyEAxg1QBieE_4z8rl74cXF3jP6DDk_6TvRR46ew-RhcwVYSIS49njAaXZ8vHzF16dw66yP04ov6D27kKwpfgQ7PyniC_jqlIlKwRhjsKwj-dUhRsP8k1ao2GEbZ8YCR9MN0pIR0dTQlH55fMeG_TenR1s6JKqHTIQp-Yi8Z_q9SV_uJi-9svPYHndgniXoKV1oaONs24xilvC374Kd-ypUVnZchxTw0DSEPFvcYvMnYFqXhdlXQzv9jg0u9AXIS7Lnx6yhAbLA
```

```json
RSASHA256(
  base64UrlEncode(header) + "." +
  base64UrlEncode(payload),
	Public Key or Certificate.
,
	Private Key. // Endoded //
)
```

- RS256 (подпись RSA с [SHA-256](https://en.wikipedia.org/wiki/SHA-256) ) - это [асимметричный алгоритм](https://en.wikipedia.org/wiki/Public-key_cryptography) , в котором используется пара открытого / закрытого ключей: поставщик удостоверений имеет закрытый (секретный) ключ, используемый для генерации подписи, а потребитель JWT получает открытый ключ. для проверки подписи. Поскольку открытый ключ, в отличие от закрытого, не требует защиты, большинство поставщиков удостоверений делают его легко доступным для получения и использования потребителями (обычно через URL-адрес метаданных).

### Для чего и на каком этапе используется каждый ключ из каталога `keys1`?

**Private.key (keys1.dir)** используется для **подписи сообщения** и присутствует в **защифрованном виде** в token'е.

**Public.key (keys1.dir)** добавляется для того, чтобы **любой мог верифицировать подпись.** 

### Для чего и на каком этапе используется ключ из каталога `keys2`?

**Public.key (keys2.dir)** используется для **верификации аутентификационных данных о клиенте** во второй части сообщения.

[JSON Web Token](https://ru.wikipedia.org/wiki/JSON_Web_Token)

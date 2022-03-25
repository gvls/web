## 2 login status
### 3  `session` 
rely on browser
after login, `server` create `session` and send `session id` to `client` 

* problem:
in high `并发` , it will use many memory of `server` 
in `分布式` or `集群` , `session` can't be `共享` 



### 3  `cookie` 
rely on browser
after login, `server` create `登录凭证` and `加密` and send **it** to `client` 
`client` send `cookie` in all `request` 

* problem:
all `request` of `client` need include `cookie` 
size of `cookie` have limit in browser
add use
not safe
can be forbidden
have limit on count



### 3  `JWT` | `JSON WEB TOKEN` 
not rely on browser
like `cookie` 
#### 4   consist of 
```go
// first part : header. use base64 
{
	'typ': 'JWT',	// type
	'alg': 'HS256'	// algorithm
}

// second part : payload. use base64
{
	// standard statement
	"iss":"jwt签发者",
	"sub":"jwt面向的用户",
	"aud":"接受jwt的一方",
	"exp":"jwt过期时间",
	"nbf":"jwt可用的开始时间",
	"iat":"jwt签发时间",
	"jti":"jwt唯一身份标识，一次性token",

	// public statement

	// private statement

}

// third part : signature. algorithm(header.payload + secret)
```

#### 4   use
```go
AddHead({
	'Authorization': 'Bearer ' + token

})
```

#### 4   process
1. client login by name and password
2. server create token and return 

3. client sent token to authentication
4. server response authentication success

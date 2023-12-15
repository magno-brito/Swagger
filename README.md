# Swagger
TESTANDO


### Security

- Security means what kind of authentication or authorization is required
- Authentication: the user has correct username and password
- Authorization: the user has access to this API and data

There are four types of security: None, API, Basic authentication and OAuth. 

- None: when you don't have security, you don't need to do anything.
- API key: add security key to each operation and then add security definition.

```
	security:
		- api_key:[]
		
	securityDefinitions:
		api_key:
			type: apiKey
			name: application-key
			in: header
		
```

- Base authentication add security key to an operation.

```
	security:
		- basic_auth: []
		
	securityDefinitions:
		basic_auth:
		type: basic
		

``` 

- OAuth: add security key to request, like before. However, now you add scopes in the array

```
	security:
		- oauth_example:
			- write:albums
			
	securityDefinitions:
		oauth_example:
			type: oauth2
			authorizationUrl: http://example.co/authenticate
			flow: implicit
			scopes:
				write:albums: modify albums in your account
				read:albums: read your albums
```


##### How security is indicated

 Each operation has a security key tha constains an array of security definition objects. In another part of the file we have security definitions.
 
#### Errors

Errors are simply different response codes. Often APIs return a special structure with errors. Example 401 (Unauthorized) code returned

```
	{"errorCode":13, "message": "Username not found"}

```

```
	responses:
		200:
			description: Successful response
		401:
			description: Unauthorized
			schem:
				$ref: '#/definitions/error'
				
	#Reference to the error
	error:
		properties:
			code:
				type: integer
			message:
				type: string

```













# Bearer Authorization

- Basic Authentication (where your username and password are transmitted to a server) 
- OAuth (where there is a cumbersome handshaking/authorization process)
- Returns a boolean decision as to the success of the attempt.
- The bearer token is then awarded so authentication doesnt need to happen for each request
- They are encoded JSON objects that “bear” or “contain” a valid token from a previously authentication Basic or OAuth. 
- The server can decode it, inspect the JSON object, look up account, and re-authenticate the user at once.
- Bearer Tokens are sent to the user/client after the initial signin process has completed.
- Clients must continue to use the same token.
- The server opens the token, does the re-authentication, and then grants or denies access

```
app.get('/somethingsecret', bearerToken, (req,res) => {
  res.status(200).send('secret sauce');
});

function bearerToken( req, res, next ) {
  let token = req.headers.authorization.split(' ').pop();
  try {
    if ( tokenIsValid(token) ) { next(); }
  }
  catch(e) { next("Invalid Token") }
}

function tokenIsValid(token) {
  let parsedToken = jwt.verify(token, SECRETKEY);
  return Users.find(parsedToken.id);
}
```

# JSON Web Tokens (JWT)

- An open standard self-contained to securely transmit between (servers, clients, etc) as a JSON object. 
- This information can be verified and trusted because it is digitally signed. 
- JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.
- Signed tokens can verify the integrity of the claims contained within it, while encrypted tokens hide those claims.
- Signing a token does not secure it’s contents be careful of the information in the JSON data. 

### Authorization 
- This is the most common scenario for using JWT. 
- Once the user is logged in, each subsequent request will include the JWT
- It will allow the user access to routes, services, and resources that are permitted with that token. 
- Single Sign On is a feature that widely uses JWT
- JSON Web Tokens are a good way of securely transmitting information between parties. 

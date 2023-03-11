## JSON Web Token (JWT)

1. Defines a compact and self-contained way for securely transmitting information between parties as a JSON object.
1. JWTs can be signed using a secret (with the HMAC algorithm) or a public/private key pair using RSA or ECDSA.
1. In its compact form, JSON Web Tokens consist of three parts separated by dots (.), which are:
  1. Header
    - consists of two parts:
      - the type of the token: JWT.
      - the signing algorithm being used: such as HMAC SHA256 or RSA.
    - Then, this JSON is Base64Url encoded to form the first part of the JWT.
  1. Payload
    - contains the claims
    - there are three types of claims: registered, public, and private claims.
      - registered claims: a set of predefined claims which are not mandatory but recommended. Such as iss (issuer), exp (expiration time), sub (subject), aud (audience).
      - public claims: defined at will by those using JWTs.
      - private claims: custom claims.
  1. Signature
    - To create the signature part you have to take the encoded header, the encoded payload, a secret, the algorithm specified in the header, and sign that.
    ```
    HMACSHA256(
      base64UrlEncode(header) + "." +
      base64UrlEncode(payload),
      secret)
    ```
1. Whenever the user wants to access a protected route or resource, the user agent should send the JWT, typically in the Authorization header using the Bearer schema.
1. Some servers don't accept more than 8 KB in headers. If you are trying to embed too much information in a JWT token, like by including all the user's permissions, you may need an alternative solution, like Auth0 Fine-Grained Authorization.
# CHAPTER 1

## API vs Managed API

A managed API has a life cyle from its creation to its retirement.

![Created -> Published -> Deprecated -> Retired](/assets/api_lifecyle.png)

### API vs Service

- An API is the interface
between two parties or two components.
- A service is a concrete implementation of an API using one of the technologies/standards available.

Today, the topic of API vs. service is debatable, because there are many overlapping areas. One popular definition
is that an API is external facing whereas a service is internal facing (see image below). An enterprise uses an API
whenever it wants to expose useful business functionality to the outside world through the firewall.

![API vs Service](/assets/apiVsService.jpg)

## A comprehensive API management platform needs to have at least three main components: a publisher, a store, and a gateway

![Comprehensive api](/assets/comprehensive_api.jpg)

# CHAPTER 2

## Security by Design

### Authentication

Authentication is the process of validating user-provided credentials to prove that users are who they claim to be.
It can be single factor or multifactor. Something you know, something you are, and something you have are the
well-known three factors of authentication. For multifactor authentication, a system should use a combination
of at least two factors. Combining two techniques that fall under the same category isn’t considered multifactor
authentication. For example, entering a username and a password and then a PIN number isn’t considered
multifactor authentication.

# CHAPTER 13

## JWT, JWS, and JWE

### JSON Web Token

JSON Web Token (JWT) defines a container to transport data between interested parties in JSON. The ongoing work of the JWT specification group under IETF is available at https://datatracker.ietf.org/doc/draft-ietf-oauth-json-web-token/. The OpenID Connect specification, discussed in Chapter 12, uses a JWT to represent the ID token.

Let’s examine the OpenID Connect ID token returned from the Google API:

```
eyJhbGciOiJSUzI1NiIsImtpZCI6Ijc4YjRjZjIzNjU2ZGMzOTUzNjRmMWI2YzAyOTA3
NjkxZjJjZGZmZTEifQ.eyJpc3MiOiJhY2NvdW50cy5nb29nbGUuY29tIiwic3ViIjoiMT
EwNTAyMjUxMTU4OTIwMTQ3NzMyIiwiYXpwIjoiODI1MjQ5ODM1NjU5LXRlOHF
nbDcwMWtnb25ub21ucDRzcXY3ZXJodTEyMTFzLmFwcHMuZ29vZ2xldXNlcmNvb
nRlbnQuY29tIiwiZW1haWwiOiJwcmFiYXRoQHdzbzIuY29tIiwiYXRfaGFzaCI6InpmO
DZ2TnVsc0xCOGdGYXFSd2R6WWciLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwiYXVkI
joiODI1MjQ5ODM1NjU5LXRlOHFnbDcwMWtnb25ub21ucDRzcXY3ZXJodTEyMTFz
LmFwcHMuZ29vZ2xldXNlcmNvbnRlbnQuY29tIiwiaGQiOiJ3c28yLmNvbSIsImlhdCI6
MTQwMTkwODI3MSwiZXhwIjoxNDAxOTEyMTcxfQ.TVKv-pdyvk2gW8sGsCbsnkq
srS0T-H00xnY6ETkIfgIxfotvFn5IwKm3xyBMpy0FFe0Rb5Ht8AEJV6PdWyxz8rMgX
2HROWqSo_RfEfUpBb4iOsq4W28KftW5H0IA44VmNZ6zU4YTqPSt4TPhyFC9fP2D
_Hg7JQozpQRUfbWTJI
```

This entire JWT is base64url-encoded. It’s divided into three sections. Each section is separated by a period (.).
Let’s identify each separate section. The first part is called the <i>JavaScript Object Signing and Encryption (JOSE)</i>
header. The <b>JOSE</b> header describes the cryptographic operations applied on the JWT claim set.

```
eyJhbGciOiJSUzI1NiIsImtpZCI6Ijc4YjRjZjIzNjU2ZGMzOTUzNjRmMWI2YzAyOTA3
NjkxZjJjZGZmZTEifQ
```

The following shows the base64url-decoded JOSE header:

```
{"alg":"RS256","kid":"78b4cf23656dc395364f1b6c02907691f2cdffe1"}
```

The second part is known as either the <i>JWT payload</i> or the JWT claim set. It carries the real business data. In the following example, it includes information about the authenticated user:

```
eyJpc3MiOiJhY2NvdW50cy5nb29nbGUuY29tIiwic3ViIjoiMTEwNTAyMjUxMTU4OT
IwMTQ3NzMyIiwiYXpwIjoiODI1MjQ5ODM1NjU5LXRlOHFnbDcwMWtnb25ub21uc
DRzcXY3ZXJodTEyMTFzLmFwcHMuZ29vZ2xldXNlcmNvbnRlbnQuY29tIiwiZW1ha
WwiOiJwcmFiYXRoQHdzbzIuY29tIiwiYXRfaGFzaCI6InpmODZ2TnVsc0xCOGdGYX
FSd2R6WWciLCJlbWFpbF92ZXJpZmllZCI6dHJ1ZSwiYXVkIjoiODI1MjQ5ODM1NjU
5LXRlOHFnbDcwMWtnb25ub21ucDRzcXY3ZXJodTEyMTFzLmFwcHMuZ29vZ2xld
XNlcmNvbnRlbnQuY29tIiwiaGQiOiJ3c28yLmNvbSIsImlhdCI6MTQwMTkwODI3MS
wiZXhwIjoxNDAxOTEyMTcxfQ
```
The following shows the base64url-decoded JWT claim set

```
{
"iss":"accounts.google.com",
"sub":"110502251158920147732",
"azp":"825249835659-te8qgl701kgonnomnp4sqv7erhu1211s.apps.googleusercontent.com",
"email":"prabath@wso2.com",
"at_hash":"zf86vNulsLB8gFaqRwdzYg",
"email_verified":true,
"aud":"825249835659-te8qgl701kgonnomnp4sqv7erhu1211s.apps.googleusercontent.com",
"hd":"wso2.com",
"iat":1401908271,
"exp":1401912171
}
```




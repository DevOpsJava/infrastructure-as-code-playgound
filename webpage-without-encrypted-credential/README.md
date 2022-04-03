# infrastructure-as-code-playgound

* Create a simple docker page
* add plain text credentials 

# webpage-with-plaintext-credential

```
docker build -t jansc/webpage-plaintext-credential:1.0 .
```

```
docker images
```

```
docker run -d --name webpage-plaintext-credential --publish 127.0.0.1:80:80/tcp jansc/webpage-plaintext-credential:1.0 
```

See http://localhost

```
docker kill webpage-plaintext-credential && docker rm webpage-plaintext-credential
```
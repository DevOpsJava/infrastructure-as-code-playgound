# infrastructure-as-code-playgound

* Create a simple docker page
* add plain encrypted credentials 

# webpage-with-encryped-credential
Creata a user: sammy
```
echo -n 'jansc:' > .htpasswd

```

Create encrypted password
```
$ openssl passwd --help
Usage: passwd [options] [passwords]
where options are
-crypt             standard Unix password algorithm (default)
-1                 MD5-based password algorithm
-apr1              MD5-based password algorithm, Apache variant
-salt string       use provided salt
-in file           read passwords from file
-stdin             read passwords from stdin
-noverify          never verify when reading password from terminal
-quiet             no warnings
-table             format output as table
-reverse           switch table columns
```

We use the MD5-based password algorithm, Apache variant that NGINX supports

```
openssl passwd -apr1 >> .htpasswd
```

```
docker build -t jansc/webpage-encrypted-credential:1.0 .
```

```
docker images
```

```
docker run -d --name webpage-encrypted-credential --publish 127.0.0.1:80:80/tcp jansc/webpage-encrypted-credential:1.0 
```

See http://localhost

```
docker kill webpage-encrypted-credential && docker rm webpage-encrypted-credential
```

##Links
https://www.digitalocean.com/community/tutorials/how-to-set-up-password-authentication-with-nginx-on-ubuntu-14-04
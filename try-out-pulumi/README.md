# infrastructure-as-code-playgound

* tryout pulumi - [here](https://www.pulumi.com/docs/get-started/azure/begin/) 
  


```
docker build -t jansc/pulumi:1.0 .
```

```
docker run -d --name acli -it --mount type=bind,source="$(pwd)",target=/source jansc/pulumi:1.0
```

Verify
```
docker exec -ti acli sh
az --version
pulumi about
go version
node -v
npm -v 
```


Create and install a template go project on azure
```
#create emtpy folder in mounted source
cd source
mkdir demo
cd demo

#Create template project based on go and select defaults. When region input northeurope
#https://github.com/pulumi/examples/tree/master/azure-go-static-website

git init
git remote add origin -f https://github.com/pulumi/examples/
git config core.sparseCheckout true
echo azure-go-static-website >> .git/info/sparse-checkout
echo azure-go-appservice-docker >> .git/info/sparse-checkout
git pull origin master
cd azure-go-appservice-docker
pulumi stack init dev
az login
pulumi config set azure-native:location northeurope
docker login
pulumi up
```

clean up 
```
pulumi destroy
pulumi stack rm dev
docker kill acli && docker rm acli
```
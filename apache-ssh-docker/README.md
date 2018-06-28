# Docker with SSH and Customize Apache Server

## Build 

```
docker build --tag vikas/apache-ssh .
```

## Save image 

```
docker save vikas/apache-ssh -o apache-ssh.tar
```

## Load image 

```
docker load --input=apache-ssh.tar
```

## Run

```
docker run -d -t -p 0.0.0.0:80:80 -p 0.0.0.0:543:22 -v /var/www/html:/var/www/html vikas/apache-ssh
```
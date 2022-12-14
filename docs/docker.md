# Run a Liberland Node with Docker   
 
 Prequirements:
 This guide assumes your running a Linux based operating system and have Docker already installed.  
 
 
## Download the docker image
```
$ docker pull laissezfaire/liberland-node:0.3.2
```

## Check that the image is downloaded
```
$ docker images -a
```

## Run node    
+ Forward ports 9933 and 9944 to local socket(-p)   
+ "-d", detach the docker image and run it as a daemon  
```
$ docker run -p 9933:9933 -p 9944:9944 -d -v /home/user/liberland/:/data laissezfaire/liberland-node:0.3.2 liberland_node
```

#### Check that node is running:   
```
$ docker ps
```

## Connect to your node with polkadot.js   
```

```


### Link to node docker image:    
https://hub.docker.com/r/laissezfaire/liberland-node   

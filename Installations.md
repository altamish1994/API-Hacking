# Postman
download Postman
tar -xnzf postman.tar.z
mv Postman /opt
sudo ln -s /opt Postman/Postman /usr/bin/postman

Now you can run postman from terminal just from using postman command

-------

# Docker

sudo apt-get install docker.io
sudo apt-get install docker-compose

# Common Issues

**Cleaning up your old containers**

> #!/bin/bash  
> sudo docker stop $(sudo docker ps -aq)  
> sudo docker rm $(sudo docker ps -aq)  
> sudo docker rmi $(sudo docker images -q)  
> sudo docker volume rm $(sudo docker volume ls -q)  
> sudo docker network rm $(sudo docker network ls -q)

**Lab troubleshooting**

If you get a general error with one of the labs, e.g. some functionality isn't working try:

- Restarting the lab
- Rebuilding the lab (sudo docker-compose up --build)
- Running the above cleanup script and then rebuilding the lab

If you're not sure what port the lab is running on:

- Check the docker-compose.yml file. You will see a line similar to "9000:80" so in this case, the lab will be running on http://localhost:9000.

If you get an error that says address already in use (e.g. 0.0.0.0:80: bind: address already in use):

- You need to make sure another container isn't already running
- You need to make sure a service like apache isn't using that port
![](https://cdn.fs.teachablecdn.com/ADNupMnWyR7kCWRvm76Laz/https://cdn.filestackcontent.com/gxsrE3X9StmZLojIPjLJ)  

# crAPI Update!

A lot of students are getting a 'container is unhealthy' error when running crAPI.

If you already ran `sudo docker-compose up` you'll need to run the cleanup script.

Next you can use the development branch until the main application is fixed. So instead of `sudo docker-compose up` you should run:

`VERSION=develop sudo docker-compose -f docker-compose.yml pull`

`VERSION=develop sudo docker-compose -f docker-compose.yml --compatibility up -d`

You can follow the issue here for updates: [https://github.com/OWASP/crAPI/issues/156](https://github.com/OWASP/crAPI/issues/156)

There is also a live version of the site hosted here if you prefer:

- [http://crapi.apisec.ai](http://crapi.apisec.ai) (main site)
- [http://crapi.apisec.ai](http://crapi.apisec.ai):8025/ (mailhog)

If it's still not working with the commands above and you don't want to use the alternative that's hosted, you can also try the build script provided with crAPI. The build script is found in `crAPI/deploy/docker`.

`./cleanup.sh`

`sudo ./build-all.sh`

`sudo VERSION=develop docker-compose -f docker-compose.yml --compatibility up`
# Docker Dev LAMP stack for PHP5.6

It comes bundled with IonCube Loader & Zend Guard Loader to run encrypted modules.  
I use it for OXID eShop projects.  

## Requirements
- docker (ofc)
- docker-compose

## Usage
Just spin it up:

    docker-compose up

and run it in your browser: http://127.0.0.1:8083  
you will see the phpinfo() output.  

To test mysql run: http://127.0.0.1:8083/mysql.php  

Put your code in the code folder.  
To add additional php-modules to the apachephp56 container edit the Dockerfile and rebuild the container:

    docker-compose build apachephp53 

Mysql is configured to accept connections from outside, so we can have a mysql admin from the host.  
I usually import inital data via Mysql Workbench.  
Find the IP of the mysql container:

    docker inspect --format '{{ .NetworkSettings.IPAddress }} {{ .Name }}' $(docker ps -q)

Add the IP as host and run Mysql Workbench.  
This is still a bit cumbersome because the IP can change everytime you fire up the container.  
So the host needs to be edited evertime anew.  
Any hints on this are welcome :)

### Debug
Xdebug is bundled.  
In PhpStorm create a Server and enter localhost as Host and 8083 as Port.  
Pathmappings should map *code* to */var/www/*.
Create a new PHP Remote Debugger, choose the Server enter XDEBUG_IDEA as key.  
Now Debugging should work.

## Todo
- log handling

## Credits
Also see: https://github.com/ivoba/docker-oxid-lamp53

## License

The MIT License (MIT)

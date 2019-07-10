# Docker-compose for PHP Development
Readme is to-do. Nonetheless, do note that the 'mac version' is merely changing to volumes using docker-sync.
When you first set up remember `docker network create dev-network`

Add VIRTUAL_HOST environment variable to any of the containers you want to add virtual hosts to for nginx-proxy to automatically configure it.

For xdebug you'll need a debugger bookmark. Get one here https://www.jetbrains.com/phpstorm/marklets/ there is currently no IDE key, but you can change that yourself in config/php/custom.ini
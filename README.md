# Laravel PHP-FPM Docker Images

These docker images are based on the docker images for Pimcore 
developed by [@dpfaffenbauer](https://github.com/dpfaffenbauer)
All credits go to him for developing such awesome images.
Some of the tools that are only needed by Pimcore has been removed to keep the images small. 


## Supported tags and respective Dockerfile links
 - PHP7.1 [PHP7.1/Dockerfile](PHP7.1/Dockerfile)
 - PHP7.0 [PHP7/Dockerfile](PHP7/Dockerfile)
 - PHP7.0-Apache [PHP7-apache/Dockerfile](PHP7-apache/Dockerfile)
 - PHP7.1-Apache [PHP7.1-apache/Dockerfile](PHP7.1-apache/Dockerfile)
 - PHP7.2-Apache [PHP7.2-apache/Dockerfile](PHP7.2-apache/Dockerfile)

> These images are supposed to be used for DEV only. Because they include and activate Xdebug by default!

## Apache Images
Images suffixed with apache have the apache and php-fpm in one container. This is due to easier fix of permission issues.
# react-docker

https://medium.com/@McMenemy/react-docker-for-development-and-production-6cb50a1218c5

## Notes
- All development is done in docker. You can run `npm install` to add modules locally but they are ignored. 

### DEV
* React app is in /frontend
* build dev image 
    * `docker build  -t react-docker-dev ./`
    * Rerun this command if you add modules to package.json via `npm install`
* To run dev you need to spin up the image into a container
    * get your dir via `pwd`
    * run this command to spin up the container and server. 
        * you have to provide an absolute path to the directory to mount the volume
        * `docker run -it -p 3000:3000 -v [put your path from (pwd) here]/frontend/src:/frontend/src react-docker-dev`
    * The dev server supports hot reload. 
    dev is visible at http://localhost:3000

### PROD
* build prod image
   * `docker build -t react-docker-prod ./ --build-arg app_env=production`
* spin up container
   * `docker run -i -t -p 3000:3000 react-docker-prod`
   * testing can be done at http://127.0.0.1:3000
   * code bundle is at http://127.0.0.1:3000/site.tar.gz

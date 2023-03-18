# SolarWinds Ruby APM Instrumentation - Redmine

Get the Redmine Docker image from https://hub.docker.com/_/redmine
```
docker pull redmine
```
Create a Dockerfile to Extend the base image to include SolarWinds Ruby APM Instrumentation steps
```
s
```
Build a New Image with Dockerfile
```
docker build -t redminenew .
```
Run the Container using New image
```
docker run -d -p 3000:3000 --name some-redmine redmine
```
docker ps
```
docker exec -it bf2b5a5ecafa bash
```
Generate Solarwinds agent file
```
bundle exec rails generate solarwinds_apm:install
```
Navigate to 
```
cd config/initializers/
vim solarwinds_apm.rb
```
Exit the container
```
exit
```
Restart the docker container
```
docker restart bf2b5a5ecafa
```
Generate traffic to see APM Data in SolarWinds. 

For RUM Monitoring
Start an interactive terminal session to go inside the container
```
docker exec -it bf2b5a5ecafa bash
```
Navigate to Application web page path and add javascript snippet before </body>. 
```
cd app/views/layouts/
vim base.html.erb
```
exit and restart the container. Generate traffic to see RUM data in SolarWinds. 


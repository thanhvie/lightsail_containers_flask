# Deployment
## Build your container image
1. `docker build -t flask-container .`
2. `docker run -p 5000:5000 flask-container`
## Create a container service
3. `aws lightsail create-container-service --service-name flask-service --power small --scale 1`
4. `aws lightsail push-container-image --service-name flask-service --label flask-container --image flask-container`
## Deploy the container
5. `aws lightsail create-container-service-deployment --service-name flask-service --containers file://containers.json --public-endpoint file://public-endpoint.json`

Use the get-container-services command to monitor the state of the container
`aws lightsail get-container-services --service-name flask-service`

## Cleanup
`aws lightsail delete-container-service --service-name flask-service`

Read AWS Documentation: https://aws.amazon.com/getting-started/hands-on/serve-a-flask-app/
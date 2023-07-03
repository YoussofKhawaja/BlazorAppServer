# BlazorAppServer
### Dotnet Build: 
This step sets up the .NET environment, restores dependencies, builds the project, and runs tests.

### Docker Build: 
This step builds a Docker image for the web application using the specified Dockerfile. It then saves the image as a TAR file and copies it to a remote server using SSH.

### Executing Remote SSH Commands: 
This step executes remote commands on the server using SSH. It loads the Docker image from the TAR file, removes the TAR file, kills any existing container with the same name, prunes unused Docker resources, and runs a new Docker container with the updated image.

### Nginx Setup: 
This step also uses SSH to execute remote commands on the server. It configures Nginx as a reverse proxy to forward requests to the Docker container. The Nginx configuration is stored in a file named web-blazorappserver.com under /etc/nginx/sites-available. If the file exists, it checks if the desired configuration is already present. If not, it updates the file and restarts Nginx. If the file does not exist, it creates it and restarts Nginx.

This workflow assumes that you have set up secrets for REMOTE_HOST, REMOTE_USER, and REMOTE_PASSWORD in your GitHub repository. These secrets contain the credentials and connection details for the remote server.
 

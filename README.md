# 14848-project


Driver App: https://hub.docker.com/r/malshahr92/homedriver port 80:80
Spark: https://hub.docker.com/r/bitnami/spark/ port 7077:7077
Sonarqube and scanner: https://hub.docker.com/r/petronetto/sonarqube-alpine port 9000:9000
jupyter: https://hub.docker.com/r/jupyter/scipy-notebook port 10000:10000
Hadoop: https://hub.docker.com/r/harisekhon/hadoop port 8088:8088



In order to get the application run on Kubernetes, some specs have to happen in order:
1. Pull all the images and put them in the container registry except Driver App
2. Deploy and expose all the containers using the ports listed above
3. For the deployment YAML file for the Jupyter notebook, add this lines:
 containers:
      - args:
        - --NotebookApp.password='sha1:ec3d557855df:11d9dc731a0493f8bf9709f20653c8a170f5587c'
        command:
        - start-notebook.sh
4. Take a note of all the exposed URLs for all the services 
5. Modify the HTML file by changing the URLs that used to be in there for the services
6. Build the HTML image and then push it to the docker hub.
7. Pull the Driver App you just pushed into the Google container registry.
8. Deploy and expose the driver image 
9. Navigate to the driver URL, and from there, you can use the hyperlinks to navigate to the microservices
but make sure to press the command key for Mac and control for windows when you click the hyperlinks to open in a new tap.


I uploaded only the Jupyter deployment YAML because it is the only one I modified to be accessed using "password" as a password.
And for the Sonarqube and scanner, the password and the user name are both the same "admin".

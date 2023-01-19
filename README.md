* If you want to run it on your local environment,

    1. Install [docker](https://www.docker.com/), download [postgreSQL](https://hub.docker.com/_/postgres), and run the following command to start a postgreSQL instance on docker:

    ```sh
    docker run --env=POSTGRES_USER=backstage --env=POSTGRES_PASSWORD=hunter2 -p 5432:5432 --restart=no --runtime=runc -d postgres
    ```

    2. Create a file named .env at the root folder with the following content to set the environment variables that'll be loaded against the configurations on backstage to connect to the postgreSQL instance running on docker:

    ```sh
    POSTGRES_SERVICE_HOST=localhost
    POSTGRES_SERVICE_PORT=5432
    POSTGRES_USER=backstage
    POSTGRES_PASSWORD=hunter2
    ```
    
    3. Open the app-config.yaml file at the root folder and replace the value in the following configuration with the personal accsss token generated from GitHub:

    ```sh
    integrations:
    github:
        - host: github.com
          token: YOUR TOKEN
    ```

    4. Run the following command to install packages the backstage app needs:

    ```sh
    yarn install
    ```

    5. Run the following command to start the backstage app:

    ```sh
    yarn dev
    ``` 
    
    6. Register a component
        * In the sidebar, choose create and click Register existing component
        * Use https://github.com/ChanningW2211/backstage/blob/master/backstage-demo.yaml for the repository URL
        * Follow along the wizard to register the sample component


* If you want to run it on minikube, follow the tutorial on https://backstage.io/docs/deployment/k8s. N.B. the tutorical is for mac users, so a couple of useful commands for windows users as below, 
    * To load the image built by the docker daemon to minikube

    ```sh
    minikube image load <image name>
    ```

    * Switch from the docker daemon to the minikube daemon

    ```sh
    @FOR /f "tokens=*" %i IN ('minikube -p minikube docker-env --shell cmd') DO @%i
    ```
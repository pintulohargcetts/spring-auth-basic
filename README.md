# Spring auth basic example

- #### Pre-requisite run , application.yml need to configure
    ```bash 
    datasource:
        driver-class-name: com.mysql.cj.jdbc.Driver
        url: jdbc:mysql://127.0.0.1:3306/testdb?verifyServerCertificate=false&useSSL=true&autoReconnect=true&serverTimezone=Asia/Seoul
        username: root
        password: Test.123!
    jpa:
        hibernate:
        ddl-auto: create
    ```

- #### Add an admin user and can access /product/all

    ```bash 
        curl --location 'http://localhost:8081/adduser' \
          --header 'Content-Type: application/json' \
          --data '{
          "name": "admin",
          "password": "admin",
          "role": "ROLE_ADMIN"
          }'
    ```


- #### Add a user as guest and can access /product/{id}

    ```bash 
        curl --location 'http://localhost:8081/adduser' \
          --header 'Content-Type: application/json' \
          --data '{
          "name": "guest",
          "password": "guest",
          "role": "ROLE_USER"
          }'
    ```

- #### APIs
    - http://localhost:8081/product/all (by admin)
    - http://localhost:8081/product/1  (by guest)
    - http://127.0.0.1:8081/hello (insecure endpoint)

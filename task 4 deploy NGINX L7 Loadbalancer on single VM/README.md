# NGINX L7 Load Balancer Configuration and Service Deployment

**Objective:**
Configuring an NGINX L7 Load Balancer using a single VM and deploying two services named `api.poridhi.io` and `fr.poridhi.io`.

**Steps:**

1. **Create VPC**

    ![image1](./image1.png)

    _Description: Creating the VPC on AWS from dashboard_

2. **Create Subnet**

    ![image2](./image2.png)

    ![image3](./image3.png)

    _Description: Setting up the Subnet_

3. **Create Internet Gateway and Attach to the VPC**

    ![image4](./image4.png)

    _Description: Establishing Internet Gateway_

4. **Add Route 0.0.0.0**

    ![image5](./image5.png)

    ![image6](./image6.png)

    ![image7](./image7.png)


    _Description: Setting up Routes_

5. **Create EC2 Instance**

    ![image9](./image9.png)

    ![image10](./image10.png)

    _Description: Spinning Up an EC2 Instance_

6. **Install NGINX on EC2 Instance**

7. **Install Node.js**

8. **Create svc1 and svc2 App**
Need to repeat this for svc1 and svc2 app directory.
    ```
    sudo npm init
    npm i express
    node server.js
    ```

    ![image11](./image11.png)

    _Description: Creating and Running svc1 and svc2 App_

9. **Configure NGINX**
    - nginx.conf file contains the configuration
    - Verify NGINX configuration:

        ```
        nginx -t -c /etc/nginx/nginx.conf
        ```

    - Reload NGINX:

        ```
        nginx -s reload
        ```

10. **Edit host:**
    - In the  `C:\Windows\System32\drivers\etc` directory open etc file in notepad and add two domains against single public ip like this. From terminal we can see that two domain response is coming using curl. 

    ![image8](./image8.png)

    _Description: Configuring NGINX for Load Balancing_

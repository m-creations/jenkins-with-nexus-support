# Inofficial tiny Jenkins image with Nexus support
This docker image extends mcreations/jenkins docker image, for more information please see here https://github.com/m-creations/docker-jenkins.

# Usage
There are following parameters to run this docker and all of them are mandatory:

* **NEXUS_NAME** the name of nexus creating maven profile and release and snapshot ids which its default value is nothing.
* **NEXUS_SSL_HOST** domain of nexus server which its default value is nothing.
* **NEXUS_SSL_PORT** secure SSL port of nexus server which its default value is **443**.
* **NEXUS_USER** the username with access to upload artifacts to Nexus which its default value is **jenkins**.
* **NEXUS_PASS** the password of user wich default value is empty
* **SCM_HOST** the host name of SCM server which its default value is nothing.
* **SCM_USER_EMAIL** the email of user of SCM server which its default value is nothing.
* **SCM_PASS** the id name of user of SCM server which its default value is nothing.
* **SCM_USER_ID** the id name of user of SCM server which its default value is **jenkins**.
* **SCM_USER_NAME** the complete name of user of SCM server which its default value is **Jenkins CI Administrator**.

This docker will extract the SSL certificate of nexus and it will import the extracted crt file into OS and JVM and with configure the .m2/setting.xml of jenkins user to use the given Nexus as default remote repository.

To run:

```
docker run -p 8080:8080 -p 50000:50000 \
        -e NEXUS_NAME=example \
        -e NEXUS_SSL_HOST=nexus.example.com \
        -e NEXUS_PASS=your-nx-pass \
        -e SCM_HOST=git.example.com \
        -e SCM_PASS=your-scm-pass \
        -e SCM_USER_EMAIL=jenkins@example.com \
        mcreations/jenkins-with-nexus-support
```

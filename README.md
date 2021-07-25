# Docker Deployment using Ansible playbook
## Description
This is a ansible playbook for install Docker, create container and also we're making up a website in the container.
Ansible provides a robust set of features and built-in modules for docker. Building a container with playbook will help to reproduce this again on another servers also.
## Pre-Requests
- Install Ansible on your Master Machine (localhost)
- Install pip, boto, boto3 and botocore
##### Ansible Modules used
- [yum](https://docs.ansible.com/ansible/2.9/modules/yum_module.html)
- [pip](https://docs.ansible.com/ansible/2.9/modules/pip_module.html)
- [service](https://docs.ansible.com/ansible/2.9/modules/service_module.html)
- [docker_image](https://docs.ansible.com/ansible/2.9/modules/docker_image_module.html)
- [get_url](https://docs.ansible.com/ansible/2.9/modules/get_url_module.html)
- [unarchive](https://docs.ansible.com/ansible/2.9/modules/unarchive_module.html)
- [docker_container](https://docs.ansible.com/ansible/2.9/modules/docker_container_module.html)
## Main Roles In Playbook
###### Install Docker
###### Service Docker start
###### Pull Image from Dockerhub
###### Download a website content for making up a site in container
###### Create container with the pulled image
###### Applied port mapping and Volume mapping

## Behind the Playbook
```
## pull image from docker hub
- name: "pull Httpd image"
        docker_image:
          name: httpd
          source: pull
## Create container from image
- name: "Launch container using httpd image"
        docker_container:
          name: mysite
          image: httpd:latest
          state: started
          ports: "80:80"  <---- port mapping
          volumes:
            - /root/2121_wave_cafe/:/usr/local/apache2/htdocs/ <--- volume mapping
```
          
        
## Conclusion
The above playbook will make up a simple site in container.

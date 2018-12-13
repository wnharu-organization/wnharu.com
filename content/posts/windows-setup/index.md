https://docs.docker.com/install/linux/docker-ce/ubuntu/
https://docs.docker.com/compose/install/#install-compose

https://nickjanetakis.com/blog/setting-up-docker-for-windows-and-wsl-to-work-flawlessly
echo "export DOCKER_HOST=tcp://localhost:2375" >> ~/.bashrc && source ~/.bashrc
```
sudo nano /etc/wsl.conf

# Now make it look like this and save the file when you're done:
[automount]
root = /
options = "metadata"
```

https://www.packer.io/docs/builders/amazon#aws_max_attempts
https://www.packer.io/docs/builders/amazon#aws_poll_delay_seconds
https://github.com/hashicorp/packer/issues/6536#issuecomment-407925535
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connection-prereqs.html

After: 

```shell script
# https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket
sudo usermod -aG docker ubuntu
sudo chown -R ubuntu ~/
# https://askubuntu.com/questions/57381/how-to-stop-mysql-from-running-at-boot-time
sudo systemctl disable mysql
```
 
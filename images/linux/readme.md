# Self hosted gh agent for aws

## Getting started

```shell script
cp variables.example.json variables.json  
vi variables.json # set your env vars  
bash build-ubuntu1804-aws-ami.sh   
```
> It takes about 1.5~2h to build ami  

## System requirements

1. To make the build process faster I used c5n.xlarge aws instance.
I you want you can make it different.
2. I've removed some dependencies from the list to make build faster and to decrease disk space: dotnetcore-sdk.sh, firefox.sh, google-chrome.sh, 
selenium.sh, sphinx.sh, android.sh. If needed you can put them back.
3. 86 gb of disk space.
4. 6~8 gb ram. The same amount will be needed for agent. 

## Tips

This block of code was deleted because it is not needed for aws build. 

```json
{
    "type": "shell",
    "inline": [
        "sleep 30",
        "/usr/sbin/waagent -force -deprovision+user && export HISTSIZE=0 && sync"
    ],
    "execute_command": "sudo sh -c '{{ .Vars }} {{ .Path }}'"
}
```
## Additional commands you need to run in the end of the build or at machine with agent: 

```shell script
# https://www.digitalocean.com/community/questions/how-to-fix-docker-got-permission-denied-while-trying-to-connect-to-the-docker-daemon-socket
sudo usermod -aG docker ubuntu
sudo chown -R ubuntu ~/
# https://askubuntu.com/questions/57381/how-to-stop-mysql-from-running-at-boot-time
sudo systemctl disable mysql
```

## Links

https://www.packer.io/docs/builders/amazon#aws_max_attempts
https://www.packer.io/docs/builders/amazon#aws_poll_delay_seconds
https://github.com/hashicorp/packer/issues/6536#issuecomment-407925535
https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/connection-prereqs.html

 
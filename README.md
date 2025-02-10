install python pip 

pip install -r requirements.txt

chmod +x ec2

sudo cp ec2 /usr/local/bin/

```
# Create a backup
ec2 backup i-1234567890abcdef0

# Restore from an AMI
ec2 restore ami-1234567890abcdef0 t2.micro

# Enable debug logging
ec2 --debug backup i-1234567890abcdef0
```

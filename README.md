# EC2 CLI Tool

A command-line interface tool for managing EC2 instance backups and restores. This tool provides simple commands to create AMIs from EC2 instances and launch new instances from AMIs.

## Features

- Create AMI backups from EC2 instances
- Restore EC2 instances from AMIs
- Input validation and error handling
- Progress indicators for long-running operations
- Detailed logging with debug mode
- JSON formatted output
- AWS resource tagging

## Prerequisites

- Python 3.8 or higher
- Python PIP installed
- AWS CLI configured with appropriate credentials
- AWS IAM permissions for EC2 operations

## Installation

1. Clone the repository:
```bash
git clone https://github.com/yourusername/ec2-cli-tool.git
cd ec2-cli-tool
```

2. Install the required dependencies:
```bash
pip install -r requirements.txt
```

3. Make the script executable:
```bash
chmod +x ec2
```

4. Move the script to your system's bin directory:
```bash
sudo cp ec2 /usr/local/bin/
```

## AWS Configuration

Ensure you have AWS credentials configured. You can do this by:

1. Using AWS CLI:
```bash
aws configure
```

2. Or by setting environment variables:
```bash
export AWS_ACCESS_KEY_ID="your_access_key"
export AWS_SECRET_ACCESS_KEY="your_secret_key"
export AWS_DEFAULT_REGION="your_region"
```

## Usage

### Create an AMI Backup

Create a backup of an EC2 instance:
```bash
ec2 backup i-1234567890abcdef0
```

The command will:
- Validate the instance ID
- Create an AMI with appropriate tags
- Wait for the AMI to be available
- Return the AMI ID in JSON format

### Restore from an AMI

Launch a new EC2 instance from an AMI:
```bash
ec2 restore ami-1234567890abcdef0 t2.micro
```

The command will:
- Validate the AMI ID and instance type
- Launch a new EC2 instance
- Add appropriate tags including a meaningful name
- Wait for the instance to be running
- Return the new instance ID in JSON format

### Debug Mode

Enable debug logging for more detailed output:
```bash
ec2 --debug backup i-1234567890abcdef0
```

## Output Format

The tool provides JSON-formatted output for successful operations:

```json
{
  "status": "success",
  "ami_id": "ami-1234567890abcdef0",
  "instance_id": "i-1234567890abcdef0",
  "timestamp": "2024-02-10T14:30:45"
}
```

## Error Handling

The tool includes comprehensive error handling:
- Input validation for instance IDs and AMI IDs
- AWS API error handling
- Clear error messages with debug information when needed
- Non-zero exit codes on failure

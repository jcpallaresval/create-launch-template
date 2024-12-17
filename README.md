# create-launch-template
Launch Template for ansible role

```yaml
create-launch-template/
├── README.md
├── tasks/
│   ├── main.yml
├── vars/
│   ├── main.yml
├── defaults/
│   ├── main.yml
├── meta/
│   ├── main.yml
├── files/
├── templates/
├── handlers/
│   ├── main.yml
├── tests/
│   ├── inventory
│   ├── test.yml
├── .gitignore
```

 Ansible Role: Launch Template

This role creates an AWS EC2 Launch Template using the `ec2_launch_template` module.

## Requirements
- boto3
- botocore
- AWS credentials with sufficient permissions

## Role Variables
- `launch_template_name`: Name of the launch template.
- `image_id`: AMI ID for the instances.
- `instance_type`: Type of the instance (e.g., `t2.micro`).
- `key_name`: (Optional) Key pair name.
- `security_group_ids`: List of security group IDs.
- `user_data`: (Optional) User data script to be included.

See `defaults/main.yml` and `vars/main.yml` for all options.

## Example Playbook
```yaml
- hosts: localhost
  roles:
    - ansible-launch-template
  vars:
    launch_template_name: "my-launch-template"
    image_id: "ami-0abcd1234efgh5678"
    instance_type: "t2.micro"
    security_group_ids:
      - "sg-0abcd1234efgh5678"
    user_data: |
      #!/bin/bash
      echo "Hello World!"
```
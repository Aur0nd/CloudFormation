  # CloudFormation

                                                  EXPLAIN:
         I've created these scripts for automating various IT - AWS tasks, feel free to commit changes





OPTIONAL: 1. mv {ScriptName}.sh /usr/bin/createuser && chmod +x /usr/bin/createuser
Deploy high. availability httpd 
 ""     Create AppLoadBalancer with a public IP(Hostname) Healthcheck :80
    Create ASG which deployes 4x t3 in the private subnet
    Launch Configuration
    Two servers in each Private subnet (4 in total)
      Specs: 4GB RAM, 2vCPU, 10GB Disk, Ubuntu 20
    IAM role for S3 pull
      # 1) Launch Config 1.1) Role for TargetGroup 1.2)Profile for Role  2)Security Group for Load Balancer 
        3)SecGroup for Instance 4)Target Group 5)LoadBalancer 6)ASG 
       7)Listener 



Step 1 - Deploy the Network
./CreateStack.sh {Stackname} NetworkBasics.yml NetworkBasics.json

Step 2 - Deploy Bastion
./CreateStack.sh {StackName} Bastion.yml Bastion.json

Step 3 - Deploy the infrastructure for hosting the instances 
./CreateStack.sh {StackName} ASG+LB+SRV.yml ASG+LB+SRV.json

Note: - You need to create a bucket and change the UserData for pointing to the specific file in the bucket
 - You need to configure & download AWS CLI
1) aws configure 
    -Add your aws credentials
    -Set Default region

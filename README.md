# servlet - Just an EC2 to run a specific job.
This is a simple EC2 creation using terraform with a simple userdata (copy data and script to process the data from s3 bucket and then run the script run.sh)

You need to update the vars.env, run the gen-vars.sh to generate tf files for terraform.

When a CI/CD job trigger to spawn an EC2 instance, it will pull down this servlet repository and run terraform apply --auto-approve to create ane EC2 instance.  Here is the major steps of this servlet repo:
*  git clone this repo
*  run terraform init and terraform apply --auto-approve
*  the userdata do the following:
   *  copy data (add.txt) and script (run.sh) to run from S3 bucket
   *  execute ./run.sh script (basicall add up all the numbers from the file) and put the total.txt to S3 bucket.

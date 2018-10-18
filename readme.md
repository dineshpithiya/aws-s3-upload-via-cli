## upload file on s3-bucket using cli interface
1. 	Create s3-bucket account
2.	Create IAM users
	- Create group
	- Attach policy
3.  Donwload IAM users credentials file

4.	Open linux/ubuntu terminal and install or verify aws cli
	To install:- 
	```
	apt install awscli
	```
5.	Type 
	```
	aws configure 
	```
	Enter the following when prompted:
	> AWS Access Key ID [None]: enter the Access Key Id from the credentials.csv file you downloaded in step 3
		Note: this should look something like AKIAPWINCOKAO3U4FWTN
	> AWS Secret Access Key [None]: enter the Secret Access Key from the credentials.csv file you downloaded in step 3
		Note: this should look something like 5dqQFBaGuPNf5z7NhFrgou4V5JJNaWPy1XFzBfX3
	> Default region name [None]:
	> Default output format [None]: json

6. 	Lists all buckets.
	```
	aws s3 ls
	```
7. 	Lists all objects and folders (prefixes. in a bucket
	```
	aws s3 ls s3://bucket-name
	```
8. 	Create bucket in s3 [if you not created yet]
	```
	aws s3 mb s3://bucket-name
	```
9. 	To remove bucket
	```
	aws s3 rb s3://bucket-name
	```
	To remove non-empty bucket
	```
	aws s3 rb s3://bucket-name --force
	```
10.	Upload file into the s3-bucket
	```
	aws s3 cp "folder-name\filename.ext" s3://bucket-name/
	```
11.	Upload multiple file
	```
	aws s3 cp s3://bucket-name/ --recursive
	```	

12.	Sync [It is better to sync your updated content only]
	```
	aws s3 sync /var/www/folder-name/ s3://bucket-name/
	```
13. To execute via crontab
	> Set cronjob and set path for the shell script
	```	
	* * * * * aws s3 sync /var/www/source-directory/ s3://bucket-name/
	```
Reference Link:- [Click](https://docs.aws.amazon.com/cli/latest/userguide/using-s3-commands.html.
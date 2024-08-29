# Mangaing-Blog-Website-Through-AWS-Linux


In this project, We can manage a blog website on aws ec2 linux server by using linux commands from our local command prompt.

Procedure :  

Step 1 :
Create ec2 linux server on aws.
go to aws ec2 -> click launch ec2->select ami as amazon linux2 ami ->select instance type as t2.micro->create new keypair to connect ec2->leave remaining by default and click launch.

Step 2 :
Connect ec2 instance from our local using ssh connection
open cmd in our local->cd downloads->ssh -i <pemfilename> ec2-user@<public dns of our ec2>
Now you can connect ec2 linux on our local.

Step 3:
Download a readymade static website template from your local computer.
I attached my website template in  this repo.

Step 4 :
Install nginx webserver to save your website template files.
open cmd in local->connect ec2 using ssh->sudo yum install nginx(to install nginx)->sudo systemctl status nginx(to check status of nginx)
Now go to your aws ec2 console. Copy public ipv4 dns of ec2 and paste it on new chrome tab. You can nginx server is running on ec2 linux server.

Step 5:
Move website template files from our local to nginx sevrer html folder on ec2.
(We need to delete nginx server html file and paste our website template files in that location.So tha our website will be run on nginx web server.)
Go to cmd->connect ec2->cd /usr/share/nginx/html(to move to nginx server html folder location) ->ls -> rm -r index.html(to delete ndex.html file)
Now open another cmd terminal without connecting ec2->cd downloads->scp -i <pemfilename> project.zip ec2-user@<public dns of our ec2> /home/ec2-user

scp                  --> for transfering files from local to remote
-i<pemfile name>     --> for secure transfering
project.zip          --> name of my downloaded website template
/home/ec2-user       --> path of remote ec2 server where you want to transfer your website template files

Go to cmd connect with ec2 ->cd /home/ec2-user->ls->unzip project.zip->cd project/->ls->sudo mv project/* /usr/share/nginx/html(moving website template files to nginx html folder location) -> cd /usr/share/nginx/html ->ls

Now ... Go to aws ec2 and copy public ipv4 dns and paste in chrome new tab.
Your website is successfully running on nginx server of ec2.

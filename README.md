# Project-Career-page
A career page created form flask framework hosted on AWS EC2 and saves uploaded resumes to S3 and uses self created tls certs for accessing through https

# Steps -
- Create 2 EC2 instances
  - Application server (Install dependencies and host application code on this from ([this repo](https://github.com/RayanAhmed2000/aws-live-project))
    - steps :
        - lauch ubuntu ec2
        - create a SG allowing HTTP/HTTPS/SSH/MYSQL
        - ssh into server
        - Clone the application code on server -  git clone https://github.com/RayanAhmed2000/aws-live-project.git
        - install dependencies
          ```
          sudo apt-get install python3
          sudo apt-get install python3-flask
          sudo apt-get install python3-pymysql
          sudo apt-get install python3-boto3
          ```
        -  Edit config file paste the creds of DB and Application server IP, region and S3 bucket name
  - Databse Server (Install mysql on this server and create a user grant him root privlidges)
    - steps
        - Update packages and install Database
          ```
          sudo apt-get update
          sudo apt-get install mysql-client
          sudo apt install mysql-server
          sudo mysql_secure_installation
          mysql -u root -p
          ```
        - Login in mysql and create a database and a table inside the database and then create a user and grant it root privilidges
          ```
          Create database applicant;
          use applicant;
          create table data( MobNo varchar(20), FirstName (20), LastName varchar(20), Skills varchar(40), Location varchar(40)); 
          ```
        - Create user and grant it root privlidges
          ```
          Create user 'rayan'@'%' IDENTIFIED by 'Admin@123';
          grant all privileges on *.* to 'rayan'@'%' with grant option;
          FLUSH PRIVILEGES;
          ```

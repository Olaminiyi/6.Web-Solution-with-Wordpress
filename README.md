# Web-Solution-with-Wordpress

In this project we will be tasked to prepare storage infrastructure on 2 `Linux servers` and implement a basic web solution using `WordPress`.

**WordPress** is a free and open-source content management system written in `PHP` and paired with `MySQL` or `MariaDB` as its backend Relational `Database Management System (RDBMS)`.

Project 6 consists of two parts:

- Configure storage subsystem for Web and Database servers based on Linux OS. The focus of this part is to give you practical experience of working with `disks`, `partitions` and `volumes` in Linux.

- Install WordPress and connect it to a remote MySQL database server. This part of the project will solidify your skills of deploying Web and DB tiers of Web solution.

**Three-tier Architecture**

Generally, web, or mobile solutions are implemented based on what is called the Three-tier Architecture.

Three-tier Architecture is a client-server software architecture pattern that comprise of 3 separate layers.

![alt text](images/6.1.png)

- **Presentation Layer (PL)**: This is the user interface such as the client server or browser on your laptop.
- **Business Layer (BL)**: This is the backend program that implements business logic. Application or Webserver.
- **Data Access or Management Layer (DAL)**: This is the layer for computer data storage and data access. Database Server or File System Server such as `FTP server`, or `NFS Server`.


In this project, we will showcase **Three-tier Architecture** while also ensuring that the disks used to store files on the Linux servers are adequately partitioned and managed through programs such as `gdisk` and `LVM` respectively.

**Our 3-Tier Setup**

- A Laptop or PC to serve as a client.
- An EC2 Linux Server as a web server (This is where you will install WordPress).
- An EC2 Linux server as a database (DB) server.

We will use **RedHat OS(centos)** for this project.

**LAUNCH AN EC2 INSTANCE THAT WILL SERVE AS “WEB SERVER”**.

After logging into our `Aws console`, we go to `EC2` and click on **"volume"** under **Elastic block store(EBS)**.

Learn How to Add `EBS Volume `to an EC2 instance [here](https://www.youtube.com/watch?v=HPXnXkBzIHw)

Click on **"create volume"**

![alt text](images/6.2.png)

then change size to **10GiB** and click on `create volume` afterwards.

![alt text](images/6.3.png)

We do the same process to create three EBS volumes.

![alt text](images/6.4.png)

Next, we create an EC2 instance that will serve as `web server`.

We set this up by doing the following:

- create an account on [AWS](https://aws.amazon.com/).
- we create an EC2 instance by selecting **“REDHAT ENTERPRISE LINUX 9”** from Amazon Machine Image(AMI)(free tier). We will select a Redhat AMI since we are using a centos and not ubuntu.
- we select “t2.micro(free tier eligible)”.
- Select our keypair.
- then go to the security group and select “a security group” review and launch.

How to create an aws free tier account. click [here](https://www.youtube.com/watch?v=xxKuB9kJoYM&list=PLtPuNR8I4TvkwU7Zu0l0G_uwtSUXLckvh&index=8)

This launches us into the instance as shown in the screenshot:

![alt text](images/6.5.png)

we then attach the EBS volumes we created to the webserver Ec2 instance.

![alt text](images/6.6.png)

then edit the **"instance info"** with the **"instance id"** and **"device name info"** to **"/dev/xvdf"**, **"/dev/xvdg"** and **"/dev/xvdh"** for the three volumes.

![alt text](images/6.7.png)


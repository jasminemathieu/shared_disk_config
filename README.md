# Data Disk Configuration & Provisioning

<div align="center">
  <img src="https://regroove.ca/stellark/wp-content/uploads/sites/3/2021/02/icon_1.0.1358.2031.png" height="240" alt="azure vm logo"  />
  <img width="72" />
  <img src="https://imgur.com/GiupieX.png" height="240" alt="azure data disk"  />
  <img width="72" />
</div>

## Introduction
This project delves into the configuration and provisioning of shared data disks in Azure. Azure shared data disks offer a cost-effective solution for various applications, particularly those requiring high availability, scalability, and efficient resource management. By enabling multiple virtual machines to access the same disk simultaneously, these shared disks facilitate seamless data sharing and collaboration, making them ideal for clustered applications, databases, and other critical workloads.

### Components used to complete this project:
- Azure
- Microsoft Virtual Machines
- Data Disk 

## 1. Azure Data Disk Setup

We start by accessing our Azure account and selecting the virtual machine to which we want to create a shared data disk.

![VMs](https://imgur.com/1UN3JPM.jpg) 

Navigate to the ‘Disks’ section under the settings tab of the selected virtual machine. As illustrated below, there are currently 'no data disks attached'.
![No data disk](https://imgur.com/ag3mxOq.jpg) 

Next, we create a new data disk to be shared with another machine in subsequent steps. Click on ‘Create and attach a new disk’, name it, and configure the data disk settings according to your requirements.

![Create dd](https://imgur.com/TX2lJ8M.jpg) 

![dd config2](https://imgur.com/b4seliH.jpg) 

Our data disk is now successfully set up.

![dd config](https://imgur.com/IzOSf24.jpg) 

## 2. Disk Configuration in Virtual Machine

At this stage, we can observe that there are only two drives on our 1st machine.

![only 2 drives](https://imgur.com/8zJ3rAU.jpg) 

Locate the disk manager dialog using the search box.

![locate disk mngr](https://imgur.com/KpBiw51.jpg) 

Upon opening the Disk Manager, if prompted, select either GPT or MBR to initialize disk.
Key:
 * GPT - allows multiple partitions on disk
 * MBR - limited partitions allowed on disk

![disk mngr scrn](https://imgur.com/FP4Sb23.jpg) 

Scroll to Disk 2 within the dialog box, right-click, and select ‘New Simple Volume’.

![disk 2 mnu](https://imgur.com/nIxywwK.jpg)  

![mnu box](https://imgur.com/NHr7iPU.jpg)  

For this project, we will use the default settings for the new data disk. However, you can customize these settings to suit your specific requirements.

![clck thru](https://imgur.com/N4WEGyQ.jpg) 

![mnu fin](https://imgur.com/r8buBth.jpg) 

After clicking 'Finish" we are able to see the E drive, representing our newly created data disk, which will be shared with our second machine.

![E drive appears](https://imgur.com/ECwqHPc.jpg) 

We then created a test folder within our newly configured E drive.

![flder crted](https://imgur.com/eBdKQGs.jpg) 

## 3. Provisioning Data Disk Access 

On our second machine, we initially do not have a data disk attached.

![no disk for ref](https://imgur.com/EXk3amS.jpg) 

In the image below, we attach the data disk to provision access for the second machine.

![adding disk to ref](https://imgur.com/mcgPae6.jpg) 

After remoting into our second machine, we successfully added the E drive. However, we were unable to view our test ‘shared folder’.

![test file not showing](https://imgur.com/zCbwlTF.jpg) 

To resolve this, we need to configure the shared disk in Azure to enable accessibility for other machines. Ensure all machines connected to the data disk are powered off, select ‘Yes’, and save the settings.

![dd config](https://imgur.com/0shl20T.jpg) 

We now have full access to the shared data disk on our second machine.

![success!](https://imgur.com/zKYEY4w.jpg) 

## Conclusion 
In this project, we successfully configured and provisioned access for a shared data disk. We faced a challenge with viewing folders and files on the provisioned disk, but after adjusting the configuration settings, we were able to access the shared data disk's contents. In conclusion, the configuration and provisioning of Azure shared data disks significantly enhance the efficiency and scalability of cloud-based applications. By allowing multiple virtual machines to access the same disk simultaneously, these shared disks provide a robust solution for high-availability environments and clustered applications. This project demonstrates the practical steps to set up and manage shared data disks, highlighting their benefits in terms of cost-effectiveness, resource optimization, and seamless data sharing. As organizations continue to leverage cloud technologies, Azure shared data disks will play a crucial role in supporting dynamic and resilient IT infrastructures.

## fin

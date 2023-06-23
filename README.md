# !!! WARNING !!!
because of forced push, i loosed all the screenshots... retaking and placing the screenshots is a lot of work


# Ways To Format Hard Drive On Linux


## Introduction:

If you're a Linux user, you already understand the significance of formatting a hard disk; otherwise, you wouldn't be here.
Whether you're installing a new operating system, erasing data on your hard drive, adding an additional disk, formatting pendrive, or even trying to exit Vim, knowing how to format a hard disk is essential.
In this article, we will delve into the process of formatting hard disks on Linux, equipping you with the necessary knowledge to confidently manage your storage needs.
Let's explore the ins and outs of formatting hard disks and enhance your Linux skills.


## List of Tools:
When it comes to formatting hard drives on Linux, you'll need to utilize two types of tools: partition managers and file system creators.
Let's explore each of these tools and their roles in the formatting process:

#### Partition Managers:
Partition managers allow you to create, modify, and delete partitions on a hard drive. They help you divide the disk into separate sections, each with its own designated file system.
Commonly used partition managers on Linux include
- fdisk
- parted
- gdisk

#### File System Creators:
File system creators (formatters), are responsible for setting up the file system within a partition.
These tools format the partition with a specific file system, determining how data is organized and stored.
Some examples of file system creators on Linux are
- mkfs (a general-purpose tool)
- mkfs.ext4 (for creating ext4 file systems)
- mkfs.xfs (for XFS file systems)
- mkfs.vfat (for FAT file systems)

By using partition managers, you can create the desired partition layout on your hard drive.
Once the partitions are set up, file system creators come into play to format the partitions with the appropriate file systems.
Remember, while these tools perform distinct functions, they work together to ensure your hard drive is properly formatted and ready for use.

## Wait, What?
To better understand this concept, let's draw an analogy using a house as an example.

##### Imagine Your Hard Disk as a House:
Think of your hard disk as a house with ample space to accommodate different activities and requirements.
Just like a house has various rooms, each designed for a specific purpose, your hard disk can be divided into partitions to serve different needs.
##### Creating Rooms in Your Hard Disk:
When you set up a house, you create rooms like a kitchen for cooking, a bedroom for sleeping, a living room for relaxation, and so on.
Similarly, with partition managers, you can divide your hard disk into separate partitions, each dedicated to fulfilling a specific purpose.
##### Assigning Functions to Partitions:
Each partition on your hard disk can be assigned a unique function, just like each room in a house serves a distinct purpose.
For instance, you can create a partition specifically for the operating system, another for your personal files, and yet another for multimedia storage.
##### Formatting the Partitions:
Once the partitions are created, file system creators step in to format each partition with a suitable file system.
This process is akin to furnishing and decorating each room in your house according to its intended purpose.
Each partition receives a file system that determines how data is stored, organized, and accessed within that space.


## Formattng usng ```fdisk``` and ```mkfs*```
To illustrate the process, let's walk through the steps of formatting a hard drive using the fdisk and mkfs commands.

### Step 1: Launch the Terminal
Open a terminal window on your Linux system. You can typically find the Terminal application in the "Utilities" or "Accessories" section of the application menu.
 ![2023-06-23_17-55](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/a4b65461-a96b-4ac4-8a84-bfc873573dcc)

### Step 2: Identify the Hard Drive (or any storage device):
Use the following command to list the available hard drives on your system:
```bash
lsblk
```
![2023-06-23_17-58](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/4e1d2f7a-ff5b-497d-9b3b-6cb9e497f93f)
Identify the hard drive you want to format. in our example, `sdc` is the pendrive we want to format. note that `sdc1` is a partiation present in `sdc`

### Step 3: Launch fdisk:
Enter the following command.
```bash
sudo fdisk /dev/sdc
```
![2023-06-23_18-35](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/9997db14-ca69-47a1-a122-091806cd086e)
Replace `/dev/sdc` with the appropriate device name of the hard drive you want to format. for example if your device name is`sdb` then command would be `sudo fdisk /dev/sdb`

### Step 4: Delete Existing Partitions (if applicable):
If there are existing partitions on the hard drive (`sdc1` in our case) that you want to remove. Use the `p` command to print all the avialbe partiations. Use the `d` command to delete each partition. Follow the on-screen prompts to select and delete the partitions.
![2023-06-23_18-44](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/7910d82b-548b-4386-a111-e87614319046)
![2023-06-23_18-47](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/3d440b7d-28e5-4977-ae2c-3d4adac426cd)

### Step 5: Create a New Partition:
To create a new partition, use the `n` command in fdisk. You can choose to create a primary partition or an extended partition. Follow the prompts to specify the partition size and type.
![2023-06-23_18-55](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/be8e88de-c829-48fd-b7b4-e40b4d856eda)

### Step 6: Set the Partition Type:
Use the `t` command in fdisk to set the partition type. Enter the appropriate partition type code (e.g., 83 for Linux).
![2023-06-23_20-49](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/8b772d3d-3989-43b1-9a96-db7702c6bf5a)
![2023-06-23_20-52](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/f3727c54-5262-4d98-a5c1-36dd0b9a74df)

### Step 7: Save the Changes:
After creating the partition(s) and setting the type, save the changes by using the w command in fdisk.
This will write the changes to the disk.
![2023-06-23_20-55](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/8548dade-7abc-4bdf-acd2-deb78c74bda6)

### Step 8: Format the Partition:
Now that the partition is created, you can format it with a file system using the `mkfs` command.
For example, to format the partition with the `ext4` file system, use the following command.
```bash
sudo mkfs.ext4 /dev/sdc1
sudo mkfs.ext4 /dev/sdc2
```
![2023-06-23_21-18](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/1620332e-c744-49a3-b302-252a13d8c0cd)

### Step 9: Confirmation:
Once the format process completes, you will receive a confirmation message. The partition is now formatted with the specified file system.

Congratulations! You have successfully formatted the hard drive using fdisk and mkfs.
The newly formatted partition is ready for use.
Repeat these steps if you want to create and format additional partitions on the same hard drive.
Remember to update the partition device names accordingly.


## Formattng using Gnome Disk (GUI)
GNOME Disks is a graphical user interface (GUI) utility in Linux that provides a user-friendly way to manage and format hard drives and storage devices. 
It offers a straightforward interface for tasks such as partitioning, formatting, and managing disk images.

### Step 1: Launch GNOME Disks:
Open the Activities Overview by clicking on the "Activities" button or pressing the Super key (Windows key).
Type "Disks" in the search bar and click on the "Disks" application icon to launch it.

### Step 2: Identify the Hard Drive:
In the GNOME Disks interface, you will see a list of available drives on the left-hand side.
Select the hard drive you want to format from the list. Be cautious to choose the correct drive as formatting will erase all data on it.
![2023-06-23_22-59](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/3a9de67f-2e0b-42d5-957e-a97c09ac2dca)

### Step 3: Unmount Partitions (if applicable):
If there are any partitions on the selected hard drive that are currently mounted (indicated by a "Stop" symbol), you need to unmount them before proceeding.
Select each mounted partition and click on the "Stop" button to unmount them.
![2023-06-23_23-05](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/e39e82f7-35c4-4e75-a529-37c20581dfd2)

### Step 4: Remove the Partitions (if applicable):
![2023-06-23_23-10](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/e57b8f7d-51c9-434f-8d99-3983a5d43464)

### Step 5 : Create Partition and format it
![2023-06-23_23-12](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/8b8749b5-04f7-4406-9a12-f5f1d67d7056)
![2023-06-23_23-16](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/838c8e9b-5d98-4f6d-beef-5079db9f2664)
![2023-06-23_23-19](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/05d43a93-c8d3-4ff4-a18e-aa61c3f51ce7)

### Or, format the exsiting partition
![2023-06-23_23-25](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/721cdc76-5b75-4682-b665-4e589821a4bd)
![2023-06-23_23-27](https://github.com/shaeinst/Ways-To-Format-Hard-Drive-On-Linux/assets/41078534/48cda65b-bc2c-4654-b722-7755b62a7bd4)


That's it! You have successfully formatted a hard drive using the GNOME Disks GUI. Remember to exercise caution and double-check your selections before proceeding to avoid any accidental data loss.


## Conclusion:

In conclusion, formatting a hard drive on Linux is an essential skill for any Linux user. We have explored various command-line tools commonly used for this purpose, such as partition managers and file system creators. These tools allow us to divide the disk into separate partitions and format them with the appropriate file systems.

By using partition managers like fdisk, parted, and gdisk, we can create, modify, and delete partitions on our hard drives. These partitions serve as distinct sections for different purposes, just like rooms in a house. File system creators, such as mkfs and mkfs.ext4, help us format the partitions with specific file systems, ensuring efficient data organization and access.

To format a hard drive using fdisk and mkfs, we follow a step-by-step process. First, we launch the terminal and identify the target hard drive. Then, we use fdisk to delete existing partitions if necessary and create a new partition. We set the partition type and save the changes. Finally, we format the partition using mkfs with the desired file system.

It is crucial to remember that formatting a hard drive erases all data, so it's essential to back up any important files before proceeding. Additionally, the choice of tool depends on individual requirements and preferences. Exploring and understanding the available command-line tools empowers Linux users to manage their storage needs effectively.

In conclusion, by mastering the art of formatting hard drives on Linux, you gain greater control over your storage resources and enhance your overall Linux skills. So, take the time to explore these tools and discover the best approach that fits your needs. Happy formatting!

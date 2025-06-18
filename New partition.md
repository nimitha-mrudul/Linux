## STEP 1: Create a New Partition
commands used to create a new partition:
1. sudo fdisk /dev/sda : enter into the Hard disk
2. n  :  Create a new partition:
3. +size(K,M,G,T,P) :  Set the size of the partition(eg +250M)
4. w  : to save the new partition

![image](https://github.com/user-attachments/assets/f6f0868c-6c6f-406c-b5f7-0ba98c7cdbfa)

## STEP 2 : File system format
commands
1.mkfs.ext3 /dev/sda4

![image](https://github.com/user-attachments/assets/bca6998d-a8aa-4da7-986f-952a184112a2)

## STEP 3 : Mount Point
commands
1. sudo mkdir -p /mnt/mypartition  : create a new diracory to mount.
2. mount /dev/sda4 /mnt/mypartition : to mount the partition in the diractory
3. cd /mnt/mypartition  : change diractory to add the file
4. vim address : add the content into "address"
5. cat address : to show the content in "address"
6. cd : change the diractory
7. reboot : reboot the mechine

![image](https://github.com/user-attachments/assets/147d2f6d-4e05-4c7a-b3fb-f9d6ff9d90f6)

## STEP 4 : Ensure Persistence After Reboot
1. vim /etc/fstab :  to edit the configuration file
2. add new partition

 format : file system - mount point -  type - options   -    dump - pass
 
3. :wq  : save and exit
4. mount -a : mount all

![image](https://github.com/user-attachments/assets/054700d5-aae3-4f48-9452-163c745fdc54)

## UUID

![image](https://github.com/user-attachments/assets/7784d0ec-5e0e-48f8-85f4-50769728ff03)

## Contents of the /etc/fstab file

![image](https://github.com/user-attachments/assets/55de7aad-4b42-4934-aa73-561667bfec7f)

## Output of ls /mnt/mypartition after reboot

![image](https://github.com/user-attachments/assets/0edd9c4e-134a-478e-8216-0567cc31b600)







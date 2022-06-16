



# Stack de dev REM (Rendez-vous en mairie)

Docker version 20.10.12, build 20.10.12-0ubuntu4
Docker Compose version v2.6.0

Node18-alpine
Mongo:latest
Redis:alpine


# Instalation virtual machine


## Process instalation for building environment

You have to download:

 - [Oracle VM latest](https://www.virtualbox.org/)

 - [Raidrive](https://www.raidrive.com/)

 - [Mongodb compass ](https://www.mongodb.com/products/compass)

 - [Another Redis Desktop manager](https://github.com/qishibo/AnotherRedisDesktopManager/releases)

 - [Ubuntu image ](https://mega.nz/file/QngyDChC#NNzsQjP7l0xhNqTCEQwUdlyYURr8Vt7bWE6cSrZk1kc)

## Instalation of Oracle VM

 - Open and execute Instalation file of Oracle VirtualBox then proceed to installation



![App Screenshot](https://support.academicsoftware.eu/hc/article_attachments/360007028497/image-0.png)



 - Choose option you want to apply for custom setup ( recommended all )


![App Screenshot](https://support.academicsoftware.eu/hc/article_attachments/360007111718/image-2.png)

 - If all things is ok youll get the Oracle VirtualBox open if not then fix review your pc config

![App Screenshot](https://support.academicsoftware.eu/hc/article_attachments/360007028717/image-8.png)


## Installation of Ubuntu 22 image to Oracle VM
- Unzip Docker U 22 zip file and get Docker U22.04-disk001.vmdk file

![App Screenshot](https://i.ibb.co/9GZxGsR/Capture-d-cran-2022-06-15-162609.png)
- you have to make sure tha virtualisation is enable in your pc by checking it in task manager:
![App Screenshot](https://i.stack.imgur.com/GkDPe.jpg)
- if your virtualisation is disabled then reboot waiting and go to bios to enable it
- if youre in lenovo this is an instruction to enable it:
 [Instriction of how enable virtualization for lenovo thinkpad ](https://pcsupport.lenovo.com/il/en/products/laptops-and-netbooks/thinkpad-p-series-laptops/thinkpad-p50/solutions/ht500006)

- Create a new virtual machine and configure it for the image file by folowing this link:
 [Instriction of how to install linux on virtual box ](https://brb.nci.nih.gov/seqtools/installUbuntu.html)



- Create A New virtual Machine with these config :



### system:

- RAM: >=4Go
- Processor: 2 core
### Network:
- Access by bridge

### Storage:
- Go to Controlleur: IDE and chose empty chos an disk file

- Choose  Docker U22.04-disk001.vmdk file
  ![App Screenshot](https://i.ibb.co/SxsJCzM/Capture-d-cran-2022-06-15-164509.png)

  



# Start the virtual Machine													
- You have to start your virtual machine now : richt click on the disk image and click on start

  ![start vm](https://i.ibb.co/qYsbVsx/Capture-d-cran-2022-06-16-100702.png)

- you have to follow this example for the ubuntu server starting  logi : https://codebots.com/docs/ubuntu-18-04-virtual-machine-setup

- your login must be like this :
| Parameter | value     | 
| :-------- | :------- | 
| `login` | `dev` | 
| `password` | `your choice` |


- the you have to log by insert your login and password, you will get same as this following screen :

  ![](https://db.tannercrook.com/wp-content/uploads/2020/03/Screenshot-from-2020-03-30-10-49-03.png)

  # set up the virtual host to the virtual machine 			
  - get your vitual machine ip : type `hostname - I` on the terminal then get the first ip adress given then copy your ip:

  

  ![](https://phoenixnap.com/kb/wp-content/uploads/2021/04/check-ip-address-linux.png)

  - Go to your physical machine and got to host file in `C:\Windows\System32\drivers\etc\` open hosts and edit it like this:

    your ip adress   rem.local

    your ip adress  www.rem.local

    ![](https://i.ibb.co/2nKZQTb/Capture-d-cran-2022-06-16-110830.png)
    
  - now your virtual host is configured
  

# config rail drive 
  - open rai drive  click  add -> NAS ->SFTP then config it like this:
| Parameter | value     | 
| :-------- | :------- | 
| `sftp://` | `rem.local` | 
| `port` | `22` |
| `path` | `/home/dev` |
| `account` | `dev` |
| `password` | `your choice` |

![](https://i.ibb.co/C6N1QPq/Capture-d-cran-2022-06-16-112144.png)



  - then click on connexion you ll get this on your screen if its ok:

![](https://docs.raidrive.com/images/en/WebDAV/webdav_disconnect.png)

  - click on the folder and you get an opening folder like this seems that you ve open your virtual machine in handle folder like a shared folder on network

![](https://i.ibb.co/kcqLphJ/Capture-d-cran-2022-06-16-113827.png)







# Get the project file
- go to your virtual machine and type

```
ssh-keygen -o -a 100 -t ed25519
```

it will create for you personal key , recommended to insert an specific passphrase

- go to your raidrive folder open then go to : .ssh open the .pub file with your editor





![](https://i.ibb.co/6yr6N76/Capture-d-cran-2022-06-16-114722.png)

![](https://i.ibb.co/TvZSgGt/Capture-d-cran-2022-06-16-115031.png)

- copy the key without the `dev@dev` 

![](https://i.ibb.co/D7w6WCX/Capture-d-cran-2022-06-16-115328.png)

- log to your digitaly account and insert it in to key ssh 

Go to : https://lab.digitaly.io/user/settings/keys

go to the rai drive open folder and make the following commande:

```
mkdir Git_Rdv_en_mairie && cd $_
git clone ssh://git@lab.digitaly.io:222/Infolocale/rdv_en_mairie.git .
cd Git_Rdv_en_mairie
./helper.sh setup
hh deploy

```

#### 

your output will be like this seems that all services are working:

![](https://i.ibb.co/KyQWvh7/Capture-d-cran-2022-06-16-142220.png)



# Set up another redis desktop

install and config redi like this: 
create a new connexion
Redis for Sessions:

| Parameter | value     |
| :-------- | :------- |
| Host | 127.0.0.1 |
| port | 6379 |
| Connection Name | VM - REM.local - Session (or your choice) |
| Separator | : |
| SSH | checked |
| Host | rem.local |
| Port | 22 |
| Username | dev |
| password | your login password |
| Timeout | 30 |

then create a new connection:
Redis for Data with the following config:
| Parameter | value     |
| :-------- | :------- |
| Host | 127.0.0.1 |
| port | 6380 |
| Connection Name | VM - REM.local - Data (or your choice) |
| Separator | : |
| SSH | checked |
| Host | rem.local |
| Port | 22 |
| Username | dev |
| password | your login password |
| Timeout | 30 |

your config will be like this :

![](https://i.ibb.co/278zsT7/Capture-d-cran-2022-06-16-143648.png)

then save and click on each connexion config,

youll get something like this if all this is ok if not error will appear

![](https://i.ibb.co/g6kWVPd/Capture-d-cran-2022-06-16-144708.png)

If both of your redis config is like this everithing is ok 

# Steup mongodb compass 
Now install your mongodb compass and configure it like this:

Create an new Connection

in Proxy/SSH:

| Parameter | value     |
| :-------- | :------- |
| SSH Hostname | rem.local |
| SSH Port | 22 |
| SSH Username | dev |
| SSH Password | your login password |

![](https://i.ibb.co/sj9w4zP/Capture-d-cran-2022-06-16-145510.png)

in General:

| Parameter | value     |
| :-------- | :------- |
| Host | localhost:27017 |

![](https://i.ibb.co/ZxH1Dpj/Capture-d-cran-2022-06-16-145705.png)

Verify that Direction Connection is checked

Click on `Connect` , you'll get something like this if everything is ok if not you have to fix connecition trouble: 

![](https://i.ibb.co/RpZGkCv/Capture-d-cran-2022-06-16-151032.png)

# 

your environment is already to buil the project

happy coding


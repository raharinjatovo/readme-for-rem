


#
# Stack de dev REM (Rendez-vous en mairie)
#
Docker version 20.10.12, build 20.10.12-0ubuntu4
Docker Compose version v2.6.0

Node18-alpine
Mongo:latest
Redis:alpine

#
# Instalation virtual machine
#

## Process instalation for building environment

You have to download:

 - [Oracle VM latest](https://www.virtualbox.org/)

 - [Raidrive](https://www.raidrive.com/)

 - [Mongodb compass ](https://www.mongodb.com/products/compass)

 - [Another Redis Desktop manager](https://github.com/qishibo/AnotherRedisDesktopManager/releases)

 - [Ubuntu image ](https://releases.ubuntu.com/20.04.4/ubuntu-20.04.4-live-server-amd64.iso)

## Instalation of Oracle VM

 - Open and execute Instalation file of Oracle VirtualBox then proceed to installation
 


![App Screenshot](https://support.academicsoftware.eu/hc/article_attachments/360007028497/image-0.png)

 - Dont specify config but just click on next

 - Choose option you want to apply for custom setup ( recommended all )


![App Screenshot](https://support.academicsoftware.eu/hc/article_attachments/360007111718/image-2.png)

 - If all things is ok youll get the Oracle VirtualBox open if not then fix review your pc config

![App Screenshot](https://support.academicsoftware.eu/hc/article_attachments/360007028717/image-8.png)


## Instalation of Ubuntu 22 image to Oracle VM
- Unzip DockerU 22 zip file and get Docker U22.04-disk001.vmdk file

![App Screenshot](https://i.ibb.co/9GZxGsR/Capture-d-cran-2022-06-15-162609.png)
- you have to make sure tha virtualisation is enable in your pc by checking it in task manager:
![App Screenshot](https://i.stack.imgur.com/GkDPe.jpg)


- Create a new virtual machine and configure it for the image file by folowing this link

 [Instriction of how to install linux on virtual box ](https://brb.nci.nih.gov/seqtools/installUbuntu.html)



- Create A New virtual Machine with these config :
### system:
- RAM: >=4Go
- Processor: 2 core
### Network
- Access by bridge

### Storage:
- Go to Controlleur: IDE and chose empty chos an disk file
- Choose  Docker U22.04-disk001.vmdk file
![App Screenshot](https://i.ibb.co/SxsJCzM/Capture-d-cran-2022-06-15-164509.png)

- Start 





```
ssh-keygen -o -a 100 -t ed25519
```

Go to : https://lab.digitaly.io/user/settings/keys

```
mkdir Git_Rdv_en_mairie && cd $_
git clone ssh://git@lab.digitaly.io:222/Infolocale/rdv_en_mairie.git .
./helper.sh deploy
```

#
# TODO
#


```javascript
console.log("bonjour")

```

## Usage

```python
import foobar

# returns 'words'
foobar.pluralize('word')

# returns 'geese'
foobar.pluralize('goose')

# returns 'phenomenon'
foobar.singularize('phenomena')
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

Please make sure to update tests as appropriate.

## License
[MIT](https://choosealicense.com/licenses/mit/)
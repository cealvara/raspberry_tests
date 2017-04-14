## connect using SSH

ssh pi@IP-ADDRESS -p 22222

# For digital ocean
## setting up digitalocean droplet (do this on command line from web)
$login with user root and pass (see email)

	adduser pi
	gpasswd -a USERNAME sudo (add user "username" to sudo group)

#ON LOCAL MACHINE>
ssh-keygen
ssh-copy-id demo@SERVER_IP_ADDRESS

#ON SERVER
	sudo nano /etc/ssh/sshd_config
		$change to> PermitRootLogin no
	sudo service ssh restart


#update apps
	sudo apt-get update

#configure time zone
	sudo dpkg-reconfigure tzdata
	sudo apt-get install tzdata (necessary to update timezone)

#Install fail2ban

	sudo apt-get install fail2ban
	sudo nano /etc/fail2ban/jail.conf
		change to
		 destemail = admin@example.com
		 action = %(action_mwl)s
	sudo service fail2ban stop
	sudo service fail2ban start

#Install pip3
	sudo apt-get install python3-pip

#set python3 as default // NOT NECESSARY
sudo rm /usr/bin/python
sudo ln -s /usr/bin/python3 /usr/bin/python


#manual installation of pip (change to python 3.4 first)
curl "https://bootstrap.pypa.io/get-pip.py" -o "get-pip.py"
python get-pip.py

#in opencloud:
sudo aptitude update
sudo aptitude install ...

#getting apps (do one by one)
sudo pip3 install pyexcel
sudo pip3 install pyexcel-xlsx
sudo pip3 install selenium

sudo apt-get install python3-dev libmysqlclient-dev
sudo pip3 install mysqlclient

sudo apt-get install phantomjs


#install phantomjs in Ubuntu (OLD INSTRUCTIONS)
sudo apt-get update
sudo apt-get install build-essential chrpath libssl-dev libxft-dev -y
sudo apt-get install libfreetype6 libfreetype6-dev -y
sudo apt-get install libfontconfig1 libfontconfig1-dev -y
cd ~
export PHANTOM_JS="phantomjs-2.1.1-linux-x86_64"
wget https://bitbucket.org/ariya/phantomjs/downloads/$PHANTOM_JS.tar.bz2
wget https://bitbucket.org/ariya/phantomjs/downloads/phantomjs-2.1.1-linux-x86_64.tar.bz2


sudo tar xvjf $PHANTOM_JS.tar.bz2
sudo mv $PHANTOM_JS /usr/local/share
sudo ln -sf /usr/local/share/$PHANTOM_JS/bin/phantomjs /usr/local/bin
phantomjs --version


#installing cron
sudo apt-get install cron -y

#CONFIG FOR AWS
--> To mount a file system (See https://docs.aws.amazon.com/efs/latest/ug/gs-step-three-connect-to-ec2-instance.html)

sudo apt-get install nfs-kernel-server
mkdir efs
sudo mount -t nfs4 -o vers=4.1 $(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone).file-system-ID.efs.aws-region.amazonaws.com:/ efs

sudo mount -t nfs4 -o vers=4.1 $(curl -s http://169.254.169.254/latest/meta-data/placement/availability-zone).fs-f5dd225c.efs.us-west-2.amazonaws.com:/ efs


Updating the /etc/fstab file in your EC2 instance
Connect to your EC2 instance, and open the /etc/fstab file in an editor.
Add the following line to the /etc/fstab file:

mount-target-DNS:/ /mnt/efs-mount-point nfs defaults,vers=4.1 0 0




#move files to server
$ add #!/usr/bin/python to main file


#editing crontab
crontab -e
#add this line
0 8 * * * python /root/rpjud/SCRAPE1.py >> /root/rpjud/out.txt



# for finding used ips in windows (cmd)
FOR /L %i IN (1,1,10) DO ping -n 1 192.168.0.%i | FIND /i "Reply"

#fixing "corrupt" keys
ssh-keygen -R "hostname"

#memory use
df -h

#to turn off
sudo shutdown -h now

#to reboot
sudo reboot

#to see output
tail -n 500 out.txt


#install phantomjs in Raspberry pi
cd /tmp
wget https://github.com/aeberhardo/phantomjs-linux-armv6l/archive/master.zip
sudo apt-get install unzip
unzip master.zip
cd phantomjs-linux-armv6l-master
bunzip2 *.bz2 && tar xf *.tar
sudo cp phantomjs-1.9.0-linux-armv6l/bin/phantomjs  /usr/bin



########## FOR RASPBERRY PI // NEW COMMANDS 2016-DIC

#note 1: add empty file to boot partition called "ssh"

1. Run raspi-config

2. Install python3
	sudo apt-get install tk-dev  ## is this necessary?
	sudo apt-get install python3-dev python3-distlib python3-setuptools python3-pip python3-wheel 

3. additional things for jupyter notebooks and geopandas (I did not install them this time..)
	sudo apt-get install libzmq-dev libgdal-dev

4. install git
	sudo apt-get install git

5. setting up git
Step 1: move to desired folder
Step 2: Run

	git init .
	touch empty.txt
	git add --all
	git config --global user.email "cealvara@gmail.com"
	git config --global user.name "Carlos (from Raspberry)"
	git config --global credential.helper cache
	git commit -m 'first empty commit' 
	git remote add origin REPOSITORY_URL
	git push origin master


TESSERACT

sudo apt-get install tesseract-ocr

sudo pip3 install pytesseract

sudo apt-get install python3-pil


FOR GEOPANDAS



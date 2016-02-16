# install

as root,

```shell
# install debian using [netinst](https://www.debian.org/CD/netinst/)

# update
aptitude update
aptitude upgrade -y
aptitude install -y git vim curl wget zip # dev
aptitude install -y make gcc g++ # build
aptitude install -y ntp ntpdate # time
aptitude install -y xinit # x11
aptitude install -y node npm libnotify4 gconf2 libnss3 # electron

# set time
mv /etc/localtime /etc/localtime.old
ln -s /usr/share/zoneinfo/Pacific/Auckland /etc/localtime
pkill ntpd
ntpdate pool.ntp.org
systemctl start ntp.service

# nodm display manager
aptitude install -y nodm
sed -i "s/NODM_ENABLED=false/NODM_ENABLED=true/" /etc/default/nodm
sed -i "s/NODM_USER=root/NODM_USER=${user}/" /etc/default/nodm
sed -i "s/NODM_XSESSION=\/etc\/X11\/Xsession/NODM_XSESSION=\/home\/${user}\/.xinitrc/" /etc/default/nodm
```

as the ${user},

```shell
# electron
mkdir $HOME/electron
cd $HOME/electron
wget https://github.com/atom/electron/releases/download/v0.36.7/electron-v0.36.7-linux-arm.zip
unzip electron-v0.36.7-linux-arm.zip
cd

# setup .xinitrc to boot electron app
echo "exec $HOME/electron/electron $HOME/boot" > $HOME/.xinitrc
chmod +x $HOME/.xinitrc

# install electron app
git clone git://github.com/ahdinosaur/bonetron $HOME/boot
```

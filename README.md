# erdaniels.com Setup

## Installation

### Clone this repo

```bash
git clone git@github.com:edaniels/erdanielsdotcom-config.git
git submodule update --init --recursive
```

### Install h2o (https://h2o.examp1e.net/install.html)

### Add www user and web group

```bash
sudo adduser www --disabled-login
sudo addgroup web
sudo usermod -a -G web www
sudo usermod -a -G web eric
```

### Setup logging
sudo mkdir -p /var/log/erdaniels.com
sudo chown -R www:web /var/log/erdaniels.com/


### Add upstart script

```bash
sudo cp etc/init/erdanielsdotcom.conf /etc/init/
sudo update-rc.d erdanielsdotcom defaults
```

### Setup site

```bash
sudo cp -r h2o /home/www/
sudo cp -r hugo /home/www/public_html
sudo chown -R www:web /home/www
```

### Start site

```bash
sudo start erdanielsdotcom
```

## Maintenance

### Update site
```bash
cd ~/erdanielsdotcom-config
cd hugo
git pull origin master
git checkout master
hugo
sudo rm -rf /home/www/public_html
sudo cp -r public /home/www/public_html
```

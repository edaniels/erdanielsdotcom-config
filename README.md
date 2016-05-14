# erdaniels.com Setup

## Installation

1. Clone this repo
```bash
git clone git@github.com:edaniels/erdanielsdotcom-config.git
git submodule update --init --recursive
```

2. Install h2o (https://h2o.examp1e.net/install.html)

3. Add www user and web group

```bash
sudo adduser www --disabled-login
sudo addgroup web
sudo usermod -a -G web www
sudo usermod -a -G web eric
```

4. Setup logging
sudo mkdir -p /var/log/erdaniels.com
sudo chown -R www:web /var/log/erdaniels.com/


5. Add upstart script

```bash
sudo cp etc/init/erdanielsdotcom.conf /etc/init/
sudo update-rc.d erdanielsdotcom defaults
```

6. Setup site
```bash
sudo cp -r h2o /home/www/
sudo cp -r hugo /home/www/public_html
sudo chown -R www:web /home/www
```

7. Start site
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

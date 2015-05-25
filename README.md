# erdaniels.com Setup

## Installation

### Clone this repo
```bash
git clone git@github.com:edaniels/erdanielsdotcom-config.git
git submodule update --init --recursive
```

### Install libressl
1. Get latest stable source
2. tar xf libressl-x.y.z.tar.gz
3. cd libressl-x.y.z
4. ./configure
5. make
6. sudo make install
7. sudo ldconfig

### Install H2O
1. Get latest stable source
2. cmake -DWITH_BUNDLED_SSL=on .
3. make
4. sudo make install

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
git pull
git submodule update --init --recursive
sudo rm -rf /home/www/public_html
sudo cp -r hugo /home/www/public_html
```
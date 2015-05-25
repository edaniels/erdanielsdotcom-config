Install libressl
1. Get latest stable source
2. tar xf libressl-x.y.z.tar.gz
3. cd libressl-x.y.z
4. ./configure
5. make
6. sudo make install
7. sudo ldconfig

Install H2O
1. Get latest stable source
2. cmake -DWITH_BUNDLED_SSL=on .
3. make
4. sudo make install

sudo apt-get install apache2-utils

sudo adduser www --disabled-login
sudo addgroup web
sudo usermod -a -G web www
sudo usermod -a -G web eric

sudo mkdir -p /var/log/erdaniels.com
sudo chown -R www:web /var/log/erdaniels.com/

sudo update-rc.d erdanielsdotcom defaults
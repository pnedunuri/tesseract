sudo yum update

## install git
sudo yum install git

## install redis
git clone https://gist.github.com/2776679.git<br/>
chmod 777 install-redis.sh<br/>
./install-redis.sh<br/>

## libraries required to compile tesseract
sudo yum install gcc-c++ make<br/>
sudo yum install openssl-devel<br/>
sudo yum install autoconf aclocal automake<br/>
sudo yum install libtool<br/>
sudo yum install libjpeg-devel libpng-devel libtiff-devel zlib-devel<br/>


## install nodejs for any future dependencies, for reference: https://github.com/nodejs/node/blob/master/BUILDING.md
cd ~<br/>
mkdir libs && cd libs<br/>
git clone https://github.com/nodejs/node.git<br/>
cd node<br/>
./configure<br/>
make -j4<br/>
sudo make install<br/>

## set path
sudo nano /etc/sudoers<br/>
Defaults secure_path = /sbin:/bin:/usr/sbin:/usr/bin:/usr/local/bin<br/>

## verify nodejs installation
node -v<br/>
npm -v<br/>

## leptonica
cd ~/libs<br/>
wget http://www.leptonica.com/source/leptonica-1.74.1.tar.gz<br/>
tar -zxvf leptonica-1.74.1.tar.gz<br/>
cd leptonica-1.74.1<br/>
./configure<br/>
make<br/>
sudo make install<br/>

## Tesseract
cd ~/libs<br/>
wget https://github.com/tesseract-ocr/tesseract/archive/3.05.00.tar.gz<br/>
tar -zxvf 3.05.00.tar.gz<br/>
cd tesseract3..<br/>
./autogen.sh<br/>
./configure<br/>
make<br/>
sudo make install<br/>
sudo ldconfig<br/>

## Tesseract Training data -- tessdata
cd /usr/local/share/tessdata<br/>
## tessdata for tesseract version < 4
sudo wget https://github.com/tesseract-ocr/tessdata/archive/3.04.00.zip<br/>
sudo unzip tessdata-3.04.00.zip<br/>
sudo mv tessdata-3.04.00/\*.\* .<br/>
sudo rm tessdata-3.04.00<br/>

## SET TESSDATA_PREFIX PATH
cd ~<br/>
sudo nano .bash_profile<br/>
export TESSDATA_PREFIX=/usr/local/share/<br/>
save and quit<br/>


credits to https://gist.github.com/shantanusingh/6526664

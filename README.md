# pwnagotchi-orange-pi-5
Commands and build scripts used to get pwnagotchi going on an Orange Pi 5 


sudo apt-get install golang-go
sudo apt-get install libusb-1.0
sudo apt-get install libpcap0.8-dev

wget https://github.com/bettercap/bettercap/archive/refs/tags/v2.26.1.zip
unzip v2.26.1.zip
cd bettercap-2.26.1/
sudo make install
sudo bettercap -eval "caplets.update; ui.update; quit"
cd ..

wget https://github.com/evilsocket/pwngrid/archive/refs/tags/v1.10.3.zip
unzip v1.10.3.zip
cd pwngrid-1.10.3/
make build
make install
sudo pwngrid -generate -keys /etc/pwnagotchi
cd ..

wget https://github.com/numpy/numpy/archive/refs/tags/v1.17.2.zip
unzip v1.17.2.zip
cd numpy-1.17.2
pip3 uninstall cython
pip3 install cython==0.29.34
python3 setup.py build -j 4 install --prefix $HOME/.local
cd ..

wget https://github.com/scipy/scipy/archive/refs/tags/v1.3.1.zip
unzip v1.3.1.zip 
cd scipy-1.3.1
nano pyproject.toml
                                                                                  
[build-system]
requires = [
    "wheel",
    "setuptools",
    "Cython==0.29.2",
    "numpy==1.17.2"
   ]

pip3 install . -v

wget "https://github.com/evilsocket/pwnagotchi/archive/v1.4.3.zip"
unzip v1.4.3.zip
cd pwnagotchi-1.4.3
nano requirements.txt # comment out numpy
sudo pip3 install -r requirements.txt
sudo pip3 install . 

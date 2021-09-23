#!/bin/bash

echo "***Systems getting update***"
sudo apt-get clean
sudo apt-get update

echo "***Downloading file***"
sudo mkdir /etc/mcafee
cd /etc/mcafee
sudo wget https://zeedrive.s3.amazonaws.com/public/software/mcafee/install.sh

echo "***Installing file***"

cd /etc/mcafee
chmod +x install.sh
sudo ./install.sh -i

function statuscheck {
mcafeestatus= 'ma status'
if [ ${mcafeestatus} == "ma status"];
then
echo "mcafee install successfully" ${mcafeestatus}
else
echo "not install"
exit 0
fi
}

echo "***Mcafee Status***"
cd
/etc/init.d/ma status

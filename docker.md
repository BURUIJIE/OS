# docker
docker build -t gcc .
docker run -it -p 22:22 -p 8080:8080 -p 4000:4000 -v /C/Users/brj/Documents:/mnt --name gcc1.0 gcc1.0  
docker run -it --network host -v /C/Users/brj/Documents:/mnt --name gcc1.0 gcc1.0  
docker ps -a
docker rm xxx
docker image ls
docker exec -it   /bin/bash
docker start  xx
docker restart
docker stop
docker attach  xxxxx
docker network ls
docker tag gcc1.3 ap1206/gcc1.3
ctrl + p + q退出attch

docker commit d5944567401a mssql-2019-with-cimb:1.0
docker save -o gcc.tar gcc

vim /root/.bashrc
pip3 install -r requirements.txt -i https://pypi.tuna.tsinghua.edu.cn/simple 
apt-get install -y gstreamer1.0-libav libnss3-tools libatk-bridge2.0-0 libcups2-dev libxkbcommon-x11-0 libxcomposite-dev libxrandr2 libgbm-dev libgtk-3-0
nc 127.0.0.1 4000


tcpdump -ni lo dst port 4000
tcpdump -ni eth0 portrange 80-9000
tcpdump -ni eth0 arp
tcpdump  -ni eth0 'tcp[20:2]=0x4745 or tcp[20:2]=0x4854'   抓http包
tcpdump -ni eth0 -c 10 dst host 192.168.1.200  src host 10.1.1.2抓10个包



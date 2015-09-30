# build docker images PTomo
sudo docker build -t zhc_web_ptomo .
sudo docker images

# forward the ports to 80
sudo iptables -A PREROUTING -t nat -i eth0 -p tcp --dport 80 -j REDIRECT --to-port 3011
sudo iptables -A INPUT -p tcp -m tcp --sport 80 -j ACCEPT
sudo iptables -A OUTPUT -p tcp -m tcp --dport 80 -j ACCEPT

# run docker images under demon
sudo docker run -ti --rm -p 3011:3011 zhc_web_ptomo



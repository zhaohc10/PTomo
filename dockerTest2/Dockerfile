FROM    centos:centos6

# Enable EPEL for Node.js
RUN     rpm -Uvh http://download.fedoraproject.org/pub/epel/6/i386/epel-release-6-8.noarch.rpm
# Install Node.js and npm
RUN     yum install -y npm

# Bundle app source
COPY . /src
# Install app dependencies
RUN cd /src; npm install

RUN npm install -g grunt-cli
RUN npm install -g grunt
RUN npm install -g forever
EXPOSE  3011
CMD ["forever", "/src/app/app.js"]

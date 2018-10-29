# amazon-kinesis-agent-deb

Pack amazon-kinesis-agent to deb package

# Note that this repo is under development and can be unstable or broken

Check releases page for pre-built packages

# How to build package with docker
- git clone https://github.com/NikonNLG/amazon-kinesis-agent-deb.git
- docker run -d -v amazon-kinesis-agent-deb:/build --name kinesis ubuntu:16.04 /bin/bash -c "while true; do date; sleep 60; done"
- docker exec -ti kinesis /bin/bash
- cd /build
- apt-get update
- apt-get -y install build-essential devscripts equivs wget
- wget https://github.com/awslabs/amazon-kinesis-agent/archive/1.1.3.tar.gz -O amazon-kinesis-agent_1.1.3.orig.tar.gz
- cd amazon-kinesis-agent-1.1.3/
- mk-build-deps -i
- dpkg-source -b .
- cd ..
- dpkg-source -x amazon-kinesis-agent_1.1.3-1.dsc
- cd amazon-kinesis-agent-1.1.3/
- debuild -b -uc -us

# DOCKER-VERSION 1.1.0

#inherit from the default container, which have all the needed script to launch tasks
FROM    ingi/inginious-c-default

# Add java 1.7
RUN     yum install -y java-1.7.0-openjdk java-1.7.0-openjdk-devel ant ant-junit bc enca

# Install Mozart2
RUN     yum -y install tcl tk boost

ADD     . /mozartRPM

RUN     rpm -ivh /mozartRPM/mozart2-2.0.0-alpha.0+build.4091.61fe075-dirty-x86_64-linux.rpm && \
        rpm -ivh /mozartRPM/python3-3.4.1-12.fc21.x86_64.rpm /mozartRPM/python3-libs-3.4.1-12.fc21.x86_64.rpm /mozartRPM/python3-setuptools-2.0-8.fc21.noarch.rpm /mozartRPM/python3-pip-1.5.6-2.fc21.noarch.rpm

# Environment variables
RUN     echo "export OZHOME=/opt/mozart2" >> /etc/profile.d/oz.sh && \
        echo "export PATH=/opt/mozart2/bin:$""PATH" >> /etc/profile.d/oz.sh

# Install ANTLR4
RUN     yum -y install wget && \
        wget -P /usr/local/lib/antlr-4.5.3-complete.jar http://www.antlr.org/download/antlr-4.5.3-complete.jar && \
        export CLASSPATH=".:/usr/local/lib/antlr-4.5.3-complete.jar:$CLASSPATH" && \
        alias antlr4='java -jar /usr/local/lib/antlr-4.5.3-complete.jar' && \
        alias grun='java org.antlr.v4.gui.TestRig'



# 基于centos:7 ,安装java1.8和anaconda开发环境，配置ssh连接
FROM centos:7

MAINTAINER Zhang jt <1562110671@qq.com>

ENV LANG=en_US.UTF-8
ENV CONDA_PATH=/opt/conda/bin
###############安装anaconda###############
# 安装网络工具使用ifconfig
RUN yum install -y net-tools
# 安装wget
RUN yum -y install wget
# 下载anaconda3;更改到家目录anaconda3.sh;
RUN wget --quiet https://repo.continuum.io/archive/Anaconda3-2023.07-0-Linux-x86_64.sh -O ~/anaconda3.sh && \
    /bin/bash ~/anaconda3.sh -b -p /opt/conda && rm ~/anaconda3.sh
RUN echo "export PATH=$CONDA_PATH:$PATH" >> /etc/profile && source /etc/profile


# 创建一个个人环境，可删除
# RUN conda create -p ~/my_python pip python=3.8 -y

#############安装java############
ENV JAVA_HOME=/opt/jdk1.8.0_131
ENV CLASSPATH=$JAVA_HOME/lib:$JAVA_HOME/jre/lib
ENV JAVA_PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin
RUN wget --no-check-certificate --no-cookies --header "Cookie: oraclelicense=accept-securebackup-cookie" \
    http://download.oracle.com/otn-pub/java/jdk/8u131-b11/d54c1d3a095b4ff2b6607d096fa80163/jdk-8u131-linux-x64.tar.gz \
    -O ~/jdk1.8.tar.gz && tar -zxvf ~/jdk1.8.tar.gz -C /opt && rm ~/jdk1.8.tar.gz && \
    echo "export CLASSPATH=$CLASSPATH" >> /ect/profile && \
    echo "export PATH=$JAVA_PATH:$PATH" >> /etc/profile && \
    source /ect/profile

RUN yum update -y

CMD echo $(conda --version) && echo $(java -version)

##############安装ssh#####################

RUN yum install passwd openssl openssh-server vim -y && \
    ssh-keygen -t rsa -f /etc/ssh/ssh_host_rsa_key -N '' && \
    ssh-keygen -t ecdsa -f /etc/ssh/ssh_host_ecdsa_key -N '' && \
    ssh-keygen -t ed25519 -f /etc/ssh/ssh_host_ed25519_key -N '' && \
    echo "1234" | passwd --stdin root && \
    /etc/init.d/sshd

EXPOSE 6666:22











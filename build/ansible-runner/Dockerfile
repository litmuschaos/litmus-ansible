FROM ubuntu:bionic

LABEL maintainer="LitmusChaos"

ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8

#Installing necessary ubuntu packages
RUN apt-get clean && \
    apt-get update --fix-missing || true && \
    apt-get install -y --no-install-recommends python3-minimal python3-pip netcat iproute2 jq sshpass vim \
    curl openssh-client python3-setuptools && rm -rf /var/lib/apt/lists/* 
RUN touch /mnt/parameters.yml

#Installing ansible and dependencies for k8s module
RUN pip3 install cryptography==3.3.2 ansible==4.2.0 ansible-base==2.10.14 openshift jmespath boto boto3 
RUN python3 -m pip install -U pip && python3 -m pip install -U setuptools && pip3 install ansible-lint==5.4.0
RUN ansible-galaxy collection install community.kubernetes


#Installing Kubectl
ENV KUBE_LATEST_VERSION="v1.22.2"
RUN curl -L https://storage.googleapis.com/kubernetes-release/release/${KUBE_LATEST_VERSION}/bin/linux/amd64/kubectl -o /usr/local/bin/kubectl && \
    chmod +x /usr/local/bin/kubectl
    
#Adding hosts entries and making ansible folders
RUN mkdir /etc/ansible/ /ansible && \
    echo "[local]" >> /etc/ansible/hosts && \
    echo "127.0.0.1" >> /etc/ansible/hosts && \
    echo "[defaults]" >> /etc/ansible/ansible.cfg && \
    echo "display_skipped_hosts = False" >> /etc/ansible/ansible.cfg && \ 
    echo "local_tmp = /tmp" >> /etc/ansible/ansible.cfg && \
    echo "remote_tmp = /tmp" >> /etc/ansible/ansible.cfg 

#Copying Necessary Files
COPY ./chaoslib ./chaoslib/
COPY ./hack/syntax-check ./hack/*.j2 ./
COPY ./utils ./utils/
COPY ./build/plugins/default.py /usr/local/lib/python3.6/dist-packages/ansible/plugins/callback/default.py
COPY ./build/utils/display.py /usr/local/lib/python3.6/dist-packages/ansible/utils/display.py
COPY experiments ./experiments
COPY ansiblelint ./ansiblelint

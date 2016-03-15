FROM opensuse:harlequin
MAINTAINER PillowSky <hyzgog@gmail.com>

# Install packages
RUN zypper -n refresh \
&&  zypper -n install openssh pwgen \
&&  sed -i "s/PermitRootLogin.*/PermitRootLogin yes/g" /etc/ssh/sshd_config \
&&  sshd-gen-keys-start \
&&  zypper clean

ADD set_root_pw.sh /set_root_pw.sh
ADD run.sh /run.sh
RUN chmod +x /*.sh

ENV AUTHORIZED_KEYS **None**

EXPOSE 22
CMD ["/run.sh"]

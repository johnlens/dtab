FROM centos:8
LABEL Samba envirenment for backups Win

RUN dnf install epel-release  -y
RUN dnf install dnf-plugins-core -y
RUN dnf  config-manager --set-enabled powertools

RUN dnf install  samba-client -y
RUN dnf install  cifs-utils -y
RUN dnf install  nmap -y
RUN dnf install  rsync -y
RUN dnf install  borgbackup -y
RUN cp /etc/samba/smb.conf /etc/samba/smb.conf.save
RUN sed '/\global\]/a\        client min protocol = NT1' /etc/samba/smb.conf.save >/etc/samba/smb.conf
COPY dt-auto-backup.tar.gz /dt-auto-backup.tar.gz
RUN tar -xzf  /dt-auto-backup.tar.gz && rm -f /dt-auto-backup.tar.gz

VOLUME /dt-auto-backup/backup
VOLUME /dt-auto-backup/run
VOLUME /dt-auto-backup/log
VOLUME /dt-auto-backup/reports
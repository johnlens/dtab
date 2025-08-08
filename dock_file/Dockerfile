FROM  debian:12
LABEL name="Samba envirenment for backups Win"


RUN apt update
RUN apt install  samba-client -y
RUN apt install  cifs-utils -y
RUN apt install  nmap -y
RUN apt install  rsync -y
RUN apt install  borgbackup -y
RUN apt install mc -y
RUN apt install iproute2 -y
RUN apt install procps -y
RUN cp /etc/samba/smb.conf /etc/samba/smb.conf.save


RUN sed '/\global\]/a\        client min protocol = NT1' /etc/samba/smb.conf.save >/etc/samba/smb.conf

COPY dt-auto-backup/ /dt-auto-backup/

VOLUME /dt-auto-backup/backup
VOLUME /dt-auto-backup/run
VOLUME /dt-auto-backup/log
VOLUME /dt-auto-backup/reports
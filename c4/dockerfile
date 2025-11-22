FROM ubuntu:24.04

RUN apt-get update && \
    apt-get install -y openssh-client openssh-server tcpdump && \
    useradd -m prueba && echo "prueba:prueba" | chpasswd && \
    mkdir /var/run/sshd

# Configuración mínima para reducir el tamaño del paquete KEXINIT
RUN echo "KexAlgorithms curve25519-sha256" >> /etc/ssh/sshd_config && \
    echo "HostKeyAlgorithms ssh-ed25519" >> /etc/ssh/sshd_config && \
    echo "Ciphers aes128-ctr" >> /etc/ssh/sshd_config && \
    echo "MACs hmac-sha2-256" >> /etc/ssh/sshd_config && \
    echo "Compression no" >> /etc/ssh/sshd_config

CMD ["/usr/sbin/sshd", "-D"]

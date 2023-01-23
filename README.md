# kerberos_with_openssh
#Kerberos is a protocol for authenticating service requests between trusted hosts across an untrusted network, 
such as the internet. Kerberos support is built in to all major computer operating systems, including Microsoft Windows, Apple macOS, FreeBSD and Linux.
# Using Kerberos with SSH
-problem:You want to authenticate to your SSH server via Kerberos-5. We assume you already have an MIT Kerberos-5 infrastructure.
-Solution
Suppose your SSH server and client machines are myserver and myclient, respectively:
1- Make sure your OpenSSH distribution is compiled with Kerberos-5 support on both myserver and myclient. The Red Hat OpenSSH distribution comes this way, but if you’re building your own, use:
$ ./configure --with-kerberos5 ...
-before building and installing OpenSSH.
2-Configure the SSH server on myserver:
  etc/ssh/sshd_config:
  KerberosAuthentication yes
  KerberosTicketCleanup yes

Decide whether you want sshd to fall back to ordinary password authentication if Kerberos authentication fails:
KerberosOrLocalPasswd [yes|no]
3-Restart the SSH server:
in kdc : **myserver# /etc/init.d/sshd restart**

I use two hosts one for kdc and other for client and you will see theses  in more details in theses files bellow

1-kdc
Kerberos runs as a third-party trusted server known as the Key Distribution Center (KDC). Each user and service on the network is a principal. The KDC has three main components: An authentication server that performs the initial authentication and issues ticket-granting tickets for users.

  this link contain kdc deployment step by step in several pictures :  https://mega.nz/fm/vqoV2Bpa
  
2-client
Kerberos is a computer network security protocol that authenticates service requests between two or more trusted hosts across an untrusted network, like the internet. It uses secret-key cryptography and a trusted third party for authenticating client-server applications and verifying users' identities.


 this link contain client kerberos configuration step by step in several pictures :  https://mega.nz/fm/zy4X3LhS
 
 









# sending-emails-through-CLI-
Email notifications are necessary to send details about the health of the system or to send any logs and much more. To send automatic mail through CLI follow the below steps:
There are various tools available in market to send emails such as 
- mailx
- ssmtp

We are using a GMAIL SSMTP to send emails.

#prerequisites
- You should have Linux as your operating system. 
- Turn on access to less secure apps [here](https://myaccount.google.com/lesssecureapps) 

Follow along with me 
```
  yum install ssmtp
  cd /etc/ssmtp
```
Now edit the ssmtp file present in this ssmtp directory. You can use any editor. For simplicity I am using vi editor here.

`vi ssmtp.conf`

Add these variables in this file.

```
mailhub=smtp.gmail.com:587
useSTARTTLS=YES
AuthUser=sender@gmail.com
AuthPass=password-here
TLS_CA_File=/etc/pki/tls/certs/ca-bundle.crt
```

Put the appropriate values for AuthUser and AuthPass
mailhub is the domain name of the third party service. If you want to use any other service you can replace this domain name. Here we have used gmail.

Now we have successfully configured. You can use various ways to send mails

1. ###A very easiest way to send mails

```
echo "Greetings from Terminal!!!" | sudo ssmtp receiver@gmail.com

```
2. You can use the same ssmtp to send mail from a shell script too. For that, open your preferred editor and create a shell script file with name saymail.shand copy-paste the below code:

  ```  
#!/bin/sh  
SUBJECT="Test Subject"
TO="crazy@yopmail.com"
MESSAGE="Hey There! This is a test mail"

echo $MESSAGE | sudo ssmtp $TO

  ```
Make sure you have set the right permission access to your script file. If not, here is the command to set the permission:

```
sudo chmod 755 mail.sh 

sudo ./mail.sh

```
Hope now you're able to send mails using the shell script too.

<! Happy Coding !>

Multi-Factor Authentication for Linux
================================
Secure Linux Desktop (**GDM**) and **SSH** Login Using Two Factor **Google Authenticator**

----------

First: Secure GDM in fedora (desktop)
-------------

*Steps*

- Install Google Authenticator in your smart Phone ([Android](https://play.google.com/store/apps/details?id=com.google.android.apps.authenticator2&hl=en)) ([iPhone](https://itunes.apple.com/us/app/google-authenticator/id388497605?mt=8))
- install Google Authenticator on your Linux machine 
 

**Fedora**
```sh
$ sudo dnf install google-authenticator
```
**centos**
```sh
$ sudo yum install google-authenticator
```

**Configure Google Authenticator on a Fedora Linux**
```sh
$ google-authenticator
Do you want authentication tokens to be time-based (y/n) y
Warning: pasting the following URL into your browser exposes the OTP secret to Google:
  https://www.google.com/chart?chs=200x200&chld=M|0&cht=qr&chl=otpauth://totp/mtayeh@tayeh.me%3Fsecret%3D6HFAKDHJBLE4YH3WURHDKR7YT4%26issuer%3Dtayeh.me
## the QR code will be here (see the screenshot 1.png                                                           
Your new secret key is: 6HFAKDHJBLE4YH3WURHDKR7YT4
Your verification code is 739326
Your emergency scratch codes are:
  25942286
  10987216
  68935574
  75891738
  97569979

Do you want me to update your "/home/mtayeh/.google_authenticator" file? (y/n) y               

Do you want to disallow multiple uses of the same authentication
token? This restricts you to one login about every 30s, but it increases
your chances to notice or even prevent man-in-the-middle attacks (y/n) y

By default, a new token is generated every 30 seconds by the mobile app.
In order to compensate for possible time-skew between the client and the server,
we allow an extra token before and after the current time. This allows for a
time skew of up to 30 seconds between authentication server and client. If you
experience problems with poor time synchronization, you can increase the window
from its default size of 3 permitted codes (one previous code, the current
code, the next code) to 17 permitted codes (the 8 previous codes, the current
code, and the 8 next codes). This will permit for a time skew of up to 4 minutes
between client and server.
Do you want to do so? (y/n) y

If the computer that you are logging into isn't hardened against brute-force
login attempts, you can enable rate-limiting for the authentication module.
By default, this limits attackers to no more than 3 login attempts every 30s.
Do you want to enable rate-limiting? (y/n) y
[mtayeh@tayeh ~]$ 

```
![](/screnshots/1.png)

- then scan the QR code using the app on your smart phone 
![](/screnshots/2.png)

- Finally, you need to add this line to gdm-password file:
```sh
$ sudo vim /etc/pam.d/gdm-password
auth required pam_google_authenticator.so
```

**now in your next login you should see a prompt for a verification code**
![](/screnshots/3.png)

--------------

Second: Secure SSH (OpenSSH server)
-------------
....
.....

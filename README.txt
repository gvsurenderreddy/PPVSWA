#############################################################################
				PPVSWA
	Public PPTP VPN Server Web Authorize system.    English Version
							 v0.9	2013/05/08
This program is a GPLv3 Free Software	copyleft avastms@ghostunix.org & s884812@gmail.com
You can visit this project at https://github.com/s884812/PPVSWA
#############################################################################

This Program is for PPTP VPN user management，based on PHP+MySQL，it needs a WebServer to operate.
'config.php'Is a config file, you must specify all variables listed inside.
'install.php' initialise the database. Once you process this file, you must remove this file from your server immediately.
This program collect registrations from 'form.php'
All information collected by 'form.php' will be sent to 'handler.php',which writes all information into MySQL database.
'admin.php' Is the main page for Administrations.
All actions taken from 'admin.php' will be sent to 'auth.php',which will apply all the changes.
'mailmaker.php'Is used for email editing。
'mailsender.php' Sends the email from 'mailmaker.php'.
'index.php' calls 'form.php'
'functions.php' is the function base, all functions were difiened here.
'selfservice.php' is for user self-activation and account status checking.
'selfauth.php' take actions to apply self-activation.
'checkstate.php' does the checking for users.
'viewkey.php' is for the administrator viewing unused activation keys.
'buildkey.php' is for key building, 5 keys at a time.
**'chap-secrets' is the user secret file of PPTP VPN server, which usually located at /etc/ppp/;  
**'chap-secrets.old' is a extra file which will be added at the end of chap-secrets, if you have a chap-secrets file existed before using this program ,rename it as 'chap-secrets.old' or specify it in 'config.php'
**'messages' is a system log file which usually located at /var/log/
**'sublog' is a file created by PPVSWA for log file analyzing.
**'analyzedlog' is the backed up system log file.
Note, sending email needs support from your server. 


=============================
Install Process    Note: Need PHP 5.2+ otherwise program will not work.
=============================
1.Unzip all files into your web dictionary
2.edit 'config.php',specify all variables.
3.open 'install.php' in your browser.
4.remove 'install.php'
5.If /etc/ppp/chap-secrets already exists，rename it as 'chap-secrets.old'                 // mv /etc/ppp/chap-secrets /etc/ppp/chap-secrets.old 
6.Change the privileges of the 'chap-secrets' into rw-rw--w-(662)                          // chmod +w /etc/ppp/chap-secrets 
7.Change the privileges of the 'sublog' into rw-rw-rw-(666)                                // chmod +rw ./sublog 
8.Change the privileges of the 'analyzedlog' into rw-rw-rw-(666)  			   // chmod +rw ./analyzedlog
8.Install compelete, peers can access 'index.php' for registration ,administrators access 'admin.php' for user management.



===============================
Release note
===============================
v0.9
add add user function.
change a little bit of the admin.php style. by using bootstrap navs and table.

v0.8
add delete user function.
fix some problem.
planning to upgrade UI in the future.

v0.7
The original author "avastmsx" abandon to maintain this project. After I asked him that let me keep maintain this great project, he said yes. So, you can visit this project at github now.(original hosted in googlecode)
You can visit this project at https://github.com/s884812/PPVSWA
what's new in this version:
1.fix a xss exploit. When member posts their register information, if attacker uses javascript, it will not be filtered.
2.using bootstrap.
3.add change password function.

v0.6+
Dropped Jquery . Improved analyzing algorithm, preventing server overload. Several bugfix.


v0.6
Used JQuery for ajax. Specified IPs for peers, 254 peers maximum. Made functions analyizing system log file, fetching peer's total usetime and bandwith usage information. Fixed a few bugs.
note: deletion of system log file will distroy everything.

v0.5
Made AJAX for Admin page. No need to refresh all the time. Used md5(md5(x)) for password encodeing, improved safety.


v0.4

Translated everything into English,fixing the encoding problem. Improved safety, no more possibility of SQL injection.

v0.3

Nearly everything got functionlised. Added new feature 'Activation Key','User Self Activation And Account Checking'.

v0.2

Integrated all features，Fixed bug (pptp vpn server name not specially defined)，made full online management（authorize/deauthorize），added new feature 'email to all peers','fuse old chap-secrets file into the new one'，'admin password'，  Improved safety，Slightly improved UI。

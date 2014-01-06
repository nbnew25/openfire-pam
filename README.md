openfire-pam
============
BUILD shaj-0.5.jar
+ sudo apt-get install ant
+ cp -rf shaj-master ~/
+ cd ~/shaj-master
+ ant dist
+ cp -rf shaj-master/build/shaj-0.5.jar /opt/openfire/lib/ 
============
BUILD libshaj.so
+ cd ~/shaj-master/src/c/
+ export JAVA_HOME=/usr/lib/jvm/java-7-oracle
+ make clean
+ make
+ cp -rf ~/shaj-master/src/c/libshaj.so /opt/openfire/lib/
+ cp -rf ~/shaj-master/src/c/libshaj.so /usr/lib/
+ sudo nano /etc/pam.d/openfire
 ---/etc/pam.d/openfire----------
  auth    required        pam_unix.so nullok_secure
 --------------------------------
============
CONFIG Openfire use NativeAuthProvider
Open Server->Server Manager->System Properties
+ nativeAuth.domain=openfire
+ provider.auth.className=org.jivesoftware.openfire.auth.NativeAuthProvider
+ provider.user.className=org.jivesoftware.openfire.user.NativeUserProvider
+ admin.authorizedJIDs=admin@mycompany
+ xmpp.domain=mycompany
=============

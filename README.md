IntelGalileoWifi
================

Best Known Working method to enable wifi with Intel Galileo

HERE IT IS.  The following step by step procedure is proven to work on Intel Galileo!!!

1. Send sketch as follows to galileo using Arduino IDE:

void setup() {
  // put your setup code here, to run once:
system("telnetd -l /bin/sh");
system("ifconfig eth0 169.254.1.1 netmask 255.255.0.0 up");
}

void loop() {
  // put your main code here, to run repeatedly: 
  
}

2. Unzip iwlwifi-6000g2b-ucode-18.168.6.1.tgz in windows folder of your preference.

3. Copy iwlwifi-6000g2b-6.ucode to folder lib/firmware using WinSCP.  SCP Protocol.  Host Name 169.254.1.1. Port number 22.  User Name: root

4. Connect to Galileo using putty.  Host Name: 169.254.1.1 Port: 22.  User: root

5. Type "wpa_passphrase MyWiFi << EOF > /etc/wpa_supplicant.conf" OJO --> MyWiFi = your router and hit enter

6. Type your router's password and hit enter

7. Type "EOF" and hit enter

8. Using WinSCP, go to the folder  /etc/network/ and open file "interfaces"

9. Add the following line "auto wlan0" after the "# Wireless interfaces" and save the file.

10. From putty, execute: "/etc/init.d/networking restart"

11. Turn off and turn back on your Galileo, it should connect to Wifi automatically

12. To turn off and on your Wifi manually use:
	- "ifdown wlan0" to turn off
	- "ifup wlan0" to turn on

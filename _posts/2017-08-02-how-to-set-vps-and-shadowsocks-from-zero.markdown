# How to set VPS and ShadowSocks from zero
This is a handbook for totally rookie guy who want to browsw Google, Youtube or other already-banned website or webservice in mainland, China.


## PART 0: BEFORE START
Before start, you need to check and prepare following items ready:
1. A VPS (Virtual Personal Server) running abroad.
2. A ShadowSocks account(server) link to your VPS host address.
If this two steps make you confused, just Google it, tons of guides already there.

*****PLUS: IF YOU ARE A GIRL WHO DATES WITH A GUY WHO KNOW “CS”, PLEASE JUMP TO PART 2 DIRECTLY :)*****

## PART 1: VPS
For lightweight apllication, The VPS service I recommend is “Bandwagon Host”, which is steady enough, user-friendly enough
and cheap enough for most application scenario.

After you order your Bandwagon VPS service successfully, you will obtain a access to Client Area, a host address(e.g 88.888.888.888),
and a SSH port to visit the host address.

So, sign in your Client Area and choose your service, then click the “KiwiVM Control Panel” button. Bingo! Now you are in the VM control panel.
The main page show some basic info about your VPS, such as Physical location(depends on the engine room you choose when order the service), IP address of your
VPS, SSH port, etc.

BUT! ALL this info are all useless if you only want to access banned interent service:) (Please notice that I never said they are useless if you want use this
VPS as your own blog’s server or for any other
high-level usage)

what we need here is on the very bottom of the control panel, “ShadowSocks Server”. Click the button and the content on this page offer a automation script to
deploy a ShadowSocks Server on your VM. BUT:) It only support CentOS 6.x, which is not the default OS of when you got your fresh VM. The good news is Bandwagon
allowed you unrestricted reinstall OS on your VM. So what we need to do is scan up the control panel and find the button “Install new OS”, and choose any CentOS
6.x system(personal recommendation: CentOS 6 x86_64 with bbr) and make sure our VM is NOT running(click the “stop” button in the main page). Now reinstal your OS
and enjoy a cup of coffee to wait the new OS installed.

Now, back to the ShadowSocks Server page and run the automation script. Be patient for a moment, then your ShadowSocks Server deployed automatically. Please
remember the 3 parameters on the screen: Shadowsocks server encryption, Shadowsocks server port, Shadowsocks server password.

## PART 2: ShadowSocks
After we deployed our ShadowSocks Server, the most difficult step to access the free internet is done. Now we need to download and install the ShadowSocks GUI
software on our PC or Mac from https://shadowsocks.org/en/download/clients.html It’s easy:)

Then run your GUI software, input your IP address, Shadowsocks server encryption, Shadowsocks server port, Shadowsocks server password(If you don’t know, ask
your server administrator), then fill in the Proxy Port field with 1080.

After click the “OK” button, choose “global mode” at first and click to start the ShadowSocks service, now type “Google.com” into your web browser’s nevigate
bar and snjoy the free internet access(Or you can choose “PAC mode” if you want to browse inside and outside website at the same time)

## PART 3: Using on iPhone
Install App “Wingy” from App Store(It is a ShadowSocks-like app, we use it to access our ShadowSocks Server while ShadowSocks APP can’t be approved in Chinese
mainland App Store and please choose the free version while the old paid app was develop for old iOS). Like operation on PC or Mac, add a new configuration and
type in host(IP address), Port(Shadowsocks server port), password(ShadowSocks server password), left other fields in default and save configuration.

Click the connect button on the main page and enjoy your web travel on your smartphone:)

***********************************************************************************************

**WELCOME TO VIEW MY GITHUB HOME PAGE https://github.com/ZexuanTHU and STAR THIS ATRICLE.**
SWipe is an application for reading magnetic stripe cards over an audio port.

## Requirements:
 - A hardware audio dongle to read the cards, such as those provided by Square
   for their payment service.
 - Qt 5.5 or later (including Qt Multimedia plugin)

It has been confirmed to run on Linux, Windows and OS X.


For your convenience, the binary for macOS High Sierra is Swipe.app. Just double-click to run it. However, if you want to make sure the code was not modified to save or transmit your credit card information, you should read the source code and build it from source yourself. You might also want to use an expired or defunct card for testing and security purposes. I should also follow my own advice.


## Building from source:

Easiest way to build Qt on Mac is using <a href="https://brew.sh/">Homebrew</a>:
```
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)" && brew install qt
```
Then do the following to make Qt build stuff:
```
echo 'export PATH="/usr/local/opt/qt/bin:$PATH"' >> ~/.bash_profile
export LIBCURL_CFLAGS=-I/usr/local/opt/curl/include
export LIBCURL_LIBS=-L/usr/local/opt/curl/lib
```
Then restart your terminal session.

To build on the terminal, simply run:
```
qmake && make
```
Then type ```open -a MagRead.app``` or double-click MagRead.app to run it.


You may also open the project file in Qt Creator to build.

http://blog.tehinterweb.com/


I forked this and modified it to build with Qt 5.10.1 on MacOS High Sierra.

This works on the S1 model of the Square card reader, which consists of a simple magnetometer connected to the GND and MIC pins of the TRRS connector, with the binary data on the magstripe transmitted as an analog signal with absolutely no encryption. You can get one of these on <a href="https://www.ebay.com/itm/Square-Credit-Card-Reader-for-iPhone-iPad-and-Android-8085036-Best-Price-FS/132609226022?epid=2212829997&hash=item1ee0203526%3Ag%3Af3QAAOSwqLpa5dg9">eBay</a> (it's the thick version with the smooth rounded surface on the back (not the thin flat back). This is the cheapest commodity card reader I know that works.


"Since demonstrating its first Square Reader device, the model S1, at the 2010 SXSW conference [7], Square has released three additional revisions of the device [8][9][10]. The Square Reader was criticized as insecure for lacking point-of-swipe encryption until the later S3 and S4 models [11]. <a href="https://www.blackhat.com/docs/us-15/materials/us-15-Mellen-Mobile-Point-Of-Scam-Attacking-The-Square-Reader-wp.pdf">https://www.blackhat.com/docs/us-15/materials/us-15-Mellen-Mobile-Point-Of-Scam-Attacking-The-Square-Reader-wp.pdf</a>

Read more: http://andybromberg.com/credit-cards/

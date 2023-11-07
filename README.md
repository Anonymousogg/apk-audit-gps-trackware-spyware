# APK Audit GPS Trackware Spyware
Android APK app audits for URL and hostname security. Reverse engineering just for fun only.

This project is for any app with gps location tracking. A GPS tracking app is dual use. It can be used for bad and good. I do not decide. I report all URL internals and let system administrators determine whether they want to put it in their blacklists.

## Why Audit?
App builders cannot be trusted to use best practice when handling private data. Hostnames and IP addresses can be used for system hardening via blacklist curations.

We audit the internal URLs so that; -
* we can check to see how strong the connection is
* we can check for any ad servers with bad connections
* black list curation

## Method
I only do this for fun in my spare time. I use a simple method in the below order.
* Install "App APK Extractor & Analyzer"
* Use the above to get the APK of your target
* Use d2j-dex2jar.sh to get the App.jar file
* Download and install jd-gui-1.6.6.deb into your system
* Use JD Gui to search for http:// and https:// 
* Use Shodan and other recon tools to check server security
* Use virus total to check server usage type
* Document and upload CSV to github

## Example CSV Scrape
```
cat <Appname>-URLs | grep AD, | cut -d , -f 3
```
Get only ad hostnames for ad blocker curation.

```
cat <Appname>-URLs | grep TLS1.2 | cut -d , f 3
```
Get hostnames with old TLS because we are strict.


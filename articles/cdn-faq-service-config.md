<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="Microsoft Azure Content Delivery Network FAQs: Azure feature guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, CDN FAQ, CDN FAQs, CDN acceleration, CDN service, configuring CNAME, CNAME, CNAME record, cache refresh, cache rules, CDN edge node, CDN technical documentation, CDN help files" description="Find answers to service configuration questions related to Microsoft Azure Content Delivery Network" metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="11/27/2015"
    />

#FAQs: Server configuration

### **Configure CNAME**
Go to the domain name management company and find the parsing manager for the domain name. Delete the A record for the domain, and add a CNAME record. We already gave you the domain name for CNAME.

### **How do I confirm that my CNAME record has taken effect?**
The time at which Domain Name System (DNS) changes take effect varies between regions, and depends on the time at which the original record corresponding to the domain name takes effect (time to live—TTL). If pinging (or digging) the domain name no longer resolves your source station IP, the CNAME record has already taken effect.

### **How do I ensure that content is synchronized with the source station after setting up Azure Content Delivery Network?**

- When you set cache rules, you should set different cache refresh rules for different content. You can set shorter cache times for frequently updated content, and longer cache times for content that is not regularly updated, to reduce pressure on the source station.
      
- If the cache refresh period that you set does not expire, but new content is published or some of the content is deleted, you can use the cache refresh features provided by the Content Delivery Network management platform to manually force it to refresh.

### **How do I change the source station server?**

First, make sure that the new source station server is working normally. Then go to the domain name management section in the Content Delivery Network advanced management platform, change the source station address to the new address, and save.

### **How do I set up cache refresh?**

- Setting cache rules: You can set different cache refresh rules for different content on the Content Delivery Network management platform. You should set shorter cache times for frequently updated content and longer cache times for content that is not regularly updated, to reduce pressure on the source station.
   
- Manual refresh: If the cache refresh period you set does not expire, but new content is published or some of the content is deleted, you can use the cache refresh features provided by the Content Delivery Network management platform to set a file refresh and directory refresh as required, to perform a manual refresh.

### **How do I obtain a visitor’s originating IP address from the source station log?**

Once a website is accelerated by using Content Delivery Network, the vast majority of visits will come from the network cache nodes. When Content Delivery Network returns to the source, it will enter the originating IP address in the HTTP Header **X-Forwarded-For**. The source station’s web server log configuration can be edited so that this information is recorded.

If we take NGINX as an example, you can add the following information to the configuration file:

log\_format logCDN '$remote\_addr forwarded for $http\_x\_forwarded\_for - $remote\_user [$time\_local] '

'"$request" $status $body\_bytes\_sent '

'"$http\_referer" "$http\_user\_agent"';
      
access\_log /var/log/nginx/access.log logCDN;

###**How do I bind Content Delivery Network edge nodes?**
 
After you have successfully created a CDN server for your source station _www.mydomain.com_ on the Content Delivery Network platform by using the customized domain name _cdn.mydomain.com_, you will receive the accelerated domain name _cdn.mydomain.com.mschcdn.com_. You can bind the host to perform basic troubleshooting. This is done by using the following procedure:

1. Ping cdn.mydomain.com.mschcdn.com to obtain the IP address of the edge node, for example, a.b.c.d.

2. Edit the local hosts file and add the record “a.b.c.d www.domain.com.”
     
Then visit _www.domain.com_ in a browser. If the website appears correctly, then there are no problems with the Content Delivery Network. If it is impossible to access the website, but the website can be successfully accessed after the IP address in the hosts file is changed to the IP address of the source station, then there is a problem with the Content Delivery Network server.

>**Note** that in Windows, the path for the hosts file is C:\\Windows\\System32\\drivers\\etc\\hosts. In UNIX-like operating systems such as Linux or BSD, the path for the hosts file is /etc/hosts. Administrator privileges are required to edit this file. Also note that, for the Azure Blob service and Cloud Services, you will get a 404 error message if you directly access the domain name. In such cases, you can troubleshoot by visiting a valid URI.



<!---HONumber=CDN_1201_2015-->

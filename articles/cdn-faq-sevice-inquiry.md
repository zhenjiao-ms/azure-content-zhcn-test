<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="Microsoft Azure CDN FAQs – Azure Feature Guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, CDN FAQ, CDN FAQS, origin traffic, ICP record number, CDN default cache rules, origin domain name, subscribe, CNAME, download acceleration, Web acceleration, website acceleration, live streaming acceleration, VOD acceleration, video on demand acceleration, CDN price, CDN fees, technical documentation, help files" description="Find answers to common service consulting questions or inquiries related to the Microsoft Azure CDN" metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service="" ms.date="" wacn.date="12/01/2015" />
#FAQs – Consulting

+ [Microsoft Azure CDN Service Consulting](#step1)
+ [Microsoft Azure CDN Price Consulting](#step2)

##**Service Consulting**<a id="step1"></a>

### **The Concept and Role of the CDN**

CDN stands for content delivery network. The CDN adds a new layer of network architecture to the existing Internet by caching the content of websites to the network “edge” nearest to the user, enabling the user to obtain the required content from a closer location, providing a high-bandwidth, low-latency user experience.

### **What is a CNAME？**

A CNAME (canonical name) record generally redirects to an alias. For example, if the user’s custom accelerated domain name is www.abc.com, the CDN service domain name given by website acceleration, once the user has configured it, would be www.abc.com.mschcdn.com. The user must have the domain name registration company delete the corresponding A record for www.abc.com and add www.abc.com.mschcdn.com as the CNAME record for the domain name. Then, when the user accesses www.abc.com, they will obtain the IP address record of the accelerated node parsed by www.abc.com.mschcdn.com.

### **The relationship between CDN traffic and return to source traffic**

- CDN traffic indicates cache hits.
    
- Return to source traffic indicates the missed portion.

### **How long is the domain name review period?**

The process of checking that supplied custom domain name and ICP number match and are valid takes no more than one business day to complete. If the details pass the ICP review, the CDN service will be registered within 60 minutes, so that it can be propagated by the CDN network. At the same time, you also need to configure the CNAME mapping details as indicated by the notifications in the interface, before the CDN cache content can finally be accessed via the custom domain name.

### **Why do you need to have a record number to use the CDN?**
 
The IP address parsed after using the CDN is the IP address of the CDN edge node. If the Ministry of Industry and Information Technology (MIIT) discovers that a record has not been filed, it will directly block the IP address. To avoid causing you more trouble in the future, we recommend that you do not use acceleration services for domain names that have no record on file, or for which the record number has been canceled, until the MIIT has finished checking the application. In terms of the specific ICP filing requirements, the only requirement is that the custom CDN acceleration domain name you are using has an ICP; there are no requirements for the source station itself, and source stations both inside and outside China are supported.

### **Do second-level domain names need to be filed?**

Second-level domain names do not need to be filed. For example, if sample.com has been filed, then images.sample.com does not need to be filed, and it is sufficient to provide the record number for sample.com when you create the CDN acceleration node.

### **Can I use the CDN if the domain name is redirected?**

Yes, but we suggest that you accelerate the domain name following the redirect, as it is not necessary to accelerate domain names before the redirect.

###**Is there a limit on the number of accelerated domain names you can add to a single account?**

The Microsoft Azure CDN has no limit on the number of accelerated domain names that can be added to each account.
    
### **What types of acceleration does the Microsoft Azure CDN support?**
  
At present, the CDN principally provides static acceleration, but also includes some dynamic acceleration technologies. Examples include returning to source using multi-line nodes and TCP optimization. Active webpage acceleration techniques such as PHP, ASP.NET and JSP are not supported, but more dynamic page acceleration methods will be gradually added in the future.

Acceleration types supported by the Microsoft Azure CDN include: Web acceleration, VOD acceleration, live streaming media (direct broadcast) acceleration, and HTTPS acceleration.
	
### **What are the specific differences between the “Web Acceleration”, “VOD Acceleration”, “Live Streaming Media Acceleration” and “HTTPS Acceleration” in the CDN acceleration type options?**

Different CDN acceleration types correspond to different usage scenarios:

1. Web Acceleration is for accelerating relatively small, static files such as webpages (HTML, CSS, images, JS).

2. Download Acceleration is generally for distributing large files of more than 20MB in size.

3. VOD Acceleration is for HTTP-based video on demand (VOD).

4. Live Streaming Media Acceleration is for live streaming media (direct broadcast).

5. HTTPS Acceleration is for situations with relatively high security requirements and is principally intended for use with smaller types of file.

The differences in terms of how these acceleration types work with the CDN back end is mainly that each type is powered by different CDN node equipment, but you do not need to perform any additional configuration.

### **What are the default cache rules for the Microsoft Azure CDN?**    

- **The system’s default cache rules for Web Acceleration are:**
  1. Dynamic files—such as those with the extensions PHP, ASPX, ASP, JSP, DO, DWR, CGI, FCGI, ACTION, ASHX, AXD and JSON—are not cached.
  2. Files with the extensions SHTML, HTML, HTM and JS are cached for half a day (720 minutes) by default. 
  3. All other static files are cached for one day (1,440 minutes) by default.

- **The system’s default cache rules for Download Acceleration are:**
  1. Dynamic files—such as those with the extensions PHP, ASPX, ASP, JSP and DO—are not cached.
  2. Files with the extensions 7Z, APK, WDF, CAB, DHP, EXE, FLV, GZ, IPA, ISO, MPK, MPQ, PBCV, PXL, QNP, R00, RAR, XY, XY2, ZIP and CAB are cached for one month.

- **The system’s default cache rules for VOD Acceleration are:**
  1. Dynamic files—such as those with the extensions PHP, ASPX, ASP, JSP and DO—are not cached.
  2. MP3 and WMA files are cached for 1 day.
  3. MWV, HTML, HTM, SHTML, HML, GIF, SWF, PNG, BMP and JS files are cached for 1 hour.
  4. Files with the extensions 7Z, APK, WDF, CAB, DHP, EXE, FLV, GZ, IPA, ISO, MPK, MPQ, PBCV, PXL, QNP, R00, RAR, XY, XY2, ZIP and CAB are cached for one month.

- **The system’s default cache rules for Live Streaming Media Acceleration are:**
  1. TS files are cached for 2 minutes.
  2. M3U8 files are cached for 2 seconds. 
	
**Cache rule logic:**

   1. If the user configured no-cache rules, then matches are assigned in order of priority. However, as matching also requires cache rules, the cache rules are matched from high to low.

   2. If a particular URL is not matched in either the cache or no-cache rules, the CDN’s default rules will be followed.

### **Can cache rules be configured for wildcard domain names?**

Can cache rules be configured for wildcard domain names? If you have created a wildcard domain name, the cache rules will be set up under the wildcard domain name. Wildcard domain names are mainly used for multiple domain names with the same configuration, in order to simply the creation process. They can be created at the same time as real domain names, with the configuration for the real domain name taking priority for matching. For example, if the rule for a1.example.com is different, the customer can create a new endpoint for a1.example.com and create cache rules there. In this situation, the configuration there would have priority over the configuration for *.example.com.

### **Are cache refresh operations supported if the custom domain name is a wildcard domain name?**

If the custom domain name is a wildcard domain name, the refresh URL must specific the sub-domain when the cache refresh is submitted. For example, if the custom domain name is *.domain.com and the customer wishes to refresh content under img.domain.com, the sub-domain img.domain.com should be specified in order to perform the cache refresh operation.

### **Can wildcard domain names be used with pre-loading?**

Pre-loading requires a sub-domain, and it must be possible to access the URL normally (the status code is 200).
	 
### **What is the difference between the “source station address (return to source address)” and the “return to source domain name (return to source host header)”?**	 

The return to source address indicates the actual, accessible address of the source station, which may be an IP address or a domain name. If it is a domain name, the CDN will perform address parsing for the domain name when returning to source, and it will then use the parsed IP address to access it.

The return to source domain name indicates the host field value in the HTTP request header when the CDN returns to source. This field value is generally a character string in the form of a domain name, which is used by the source station to identify whether it is the same as the domain name configured on the source station.

When you create the CDN in the Azure Management Portal, enter the return to source access host header accepted by your source station in the “origin host header”. Once you have entered the “Custom Domain”, the system will automatically fill in a default value based on the “Origin Domain Type” you selected. To be more specific, if your source station is on Azure, the default value will be the corresponding source station address. If your source station is not on Azure, the default value will be the “Custom Domain” that you entered. Of course, you can also modify this based on the actual configuration of your source station.

### **What are the differences between the standard and advanced versions of the CDN?**
     
First, the pricing is different. See [Pricing Details](http://www.windowsazure.cn/home/features/cdn/#price) for specifics. Second, the current version of the CDN only includes HTTPS acceleration services, although other advanced acceleration services will gradually be added in the future. If you wish to use CDN HTTPS acceleration services at this time, please use the support page to contact the Microsoft Azure support team to enable CDN HTTPS acceleration services.

### **If I use CDN acceleration with a Blob, do I directly use the Blob address, rather than the custom domain name? Do I need to apply for filing, and why?**
The CDN (content delivery network) is basically a group of network content caching nodes and is not equivalent to a customer’s source station. The caching nodes only incorporate the content that the user has set up for caching, and even this may expire.

The purpose of custom domain names is that they can be given a CNAME so that the source station cache hit is directly returned when source website content is accessed via the CDN using the custom domain name; otherwise, it may be returned to source. This is the principle of the CDN.

If the custom domain name and the origin domain name were the same, the result would be:

1. Return to source failure - because the acceleration node would be accessed again via CNS instead of the source station when returning to source;
2. Access failure - part of the source station content may not be on the acceleration nodes.

The law stipulates that custom domain names are subject to ICP record filing, but there are no requirements for source stations. However, if the second-level domain name for the custom domain name itself has already been filed, it is not necessary to file another application.

### **If there are multiple subscriptions, how do I switch between them?**
   
If you have multiple subscriptions, as shown in the diagram, you can click on the triangular dropdown list in the subscription ID area at the top right corner of the Management Portal website to select a suitable subscription ID.
    
 ![FAQ](./media/cdn-doc/FAQ.png)
    

##**Price Consulting**<a id="step2"></a>


### **Is all data transferred charged at a higher rate once the amount of data transferred each month exceeds 10TB?**

No. Usage that falls under each level will be charged at the rate for that level. For example, if you generate 50TB of standard version CDN data transfers in region 1, the first 10TB will be charged at ¥0.45/GB, and the remaining 40TB will be charged at ¥0.41/GB.

### **Do CDN fees include performing storage requests, i.e. the costs of retrieving data and transferring data from storage to the CDN location?**

No, this is not included. When the CDN receives a request for an object that is not located in an edge location, it sends Azure Storage a request to obtain the data. The operations to fetch data from storage and transfer data from storage to the CDN will be charged at standard data transfer rates.

### **How are CDN fees calculated?**

Fees for the Microsoft Azure CDN are currently calculated on the basis of traffic. Charging by peak bandwidth is not supported at the moment. For more specific information on pricing, please refer to [Pricing Details](http://www.windowsazure.cn/home/features/cdn/#price).

<!---HONumber=CDN_1201_2015-->
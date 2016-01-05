<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="Microsoft Azure Content Delivery Network FAQs: "Azure feature guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, cannot cache, cannot CNAME, origin rate high, cache refresh failed, CDN FAQ, CDN FAQS, CDN use failed, CDN service failure, CDN configuration error, speed slow, cannot open website, login exception, CNAME, CDN technical documentation, CDN help files" description="Find answers to common service consulting questions or inquiries related to the Microsoft Azure Content Delivery Network" metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="11/27/2015"
    />
#FAQs: Service issues

### **Why can’t I cache my URL?**

The inability to cache a URL is usually due to one of the following reasons:

1. The corresponding header for the URL on the source station includes the following information:
   - Set-Cookie (and the ignore Set-Cookie option has not been checked in the cache rules). Note: When Set-Cookie is used for user signin and identification, the ignore Set-Cookie option cannot be checked. Otherwise, it could cause problems with functions.
   - Cache-Control: No-store/no-cache/private (and the ignore Cache-Control) option has not been checked in the cache rules.
   - The Expires time is a time in the past. Expires sets the point in time when the cache expires. If this time is in the past, it makes it impossible to cache.
   - The value of Max-age is very small. Max-age sets the length of the caching time in seconds. If the value is too small, for example, less than two digits, it expires very quickly and makes it impossible to cache.

2. The cache rules are not configured or are configured with errors such that the URL cannot hit any buffer rules. For example, if the user accidentally enters the rule “[Any Character] (.gif|.jpg|.bmp) (.gif|.jpg|.bmp)”, then it is impossible to hit the rule even though the file is of the picture type, because the file extension is duplicated.
   
3. No users have so far accessed the URL, as some nodes cache the content only after it has been accessed.

### **Why are domain names resolved to the source station?**

If the acceleration region of a domain name CDN is Mainland China, overseas Internet users or Chinese Internet users who use non-Chinese Domain Name System (DNS) resolutions may be resolved to the source station. The Azure Content Delivery Network platform’s default configuration for such situations is to use Content Delivery Network nodes in China to serve overseas visits.

### **What does the “CNAME cannot be used for system prompts” message mean?**

Although we have not placed restrictions on accelerated domain names, it is possible that some domain name management companies do not allow the use of CNAME for domain names that include the host name. You can resolve this by either changing the accelerated domain name or changing your domain name management company.

### **Why is return-to-source traffic greater than Content Delivery Network traffic?**

In general, return-to-source traffic is less than or equal to Content Delivery Network traffic. But in certain circumstances, return-to-source traffic can also be greater than Content Delivery Network traffic, e.g., if the visitor sends a request for a relatively large file. For example, if a 100-MB file has not been cached by the nodes, the network nodes retrieve it from the source station, which for a file of this size inevitably takes some time. However, the visitor may not keep waiting at this time, with the result that the connection is disconnected. In such a situation, the network nodes still bring over the entire 100-MB file. By the time that the network nodes recognize that the visitor no longer wants the file, it no longer has any way to go back, so the return-to-source traffic reaches 100 MB, while the network traffic does not.

### **Why are opening speeds even slower since I started using Azure Content Delivery Network?**

A low cache hit rate can be caused by several factors:

- Cache configuration has issues.
     
- The HTTP header causes inability to cache.
     
- The Content Delivery Network acceleration node has only just been added, so the number of cached files is still small.
     
- The type of source station means that the amount of content that can be cached is small.
     
- Website visit numbers are low and the expiration time is short, so the number of files hit is small.

### **What causes a relatively high return-to-source rate?** 

1. Cache rule configuration has issues.
    
2. The amount of resources that can be cached is small.
    
3. The cache time is short.

### **Why can’t I open websites since I started using Content Delivery Network?** 

There are several possible reasons:
 
1. The source station malfunctions.
     
2. The source station has a firewall that is shielding the Content Delivery Network nodes.
    
3. The nodes are shielding the client IP.
     
4. If you have added a new domain name or the domain name status has changed and there is problem with the node configuration, you may need to wait for a while until the problem is resolved, typically around 60 minutes.
     
5. Equipment fails.
    
### **Why do I encounter issues when I sign in to the website since I started using Content Delivery Network?**

It is highly likely that resources that shouldn’t be cached have been set up in the cache rules. If so, you need to set the user back-end signin folder to not cache (e.g., /user or /admin). If it is a website with no signin or with user responses, then enable permission to ignore cookies in the cache rule configuration.

### **Why did my cache refresh fail?**

After a manual refresh is submitted, the system identifies the equipment that is working normally to allocate tasks. But if an anomaly occurs in a particular device during the allocation process, the system automatically detects and disables it. (Clients are not parsed to the relevant node after the service status has been closed, and it does not affect the acceleration service.) Other normal devices continue to be allocated tasks until they are complete, at which time, the interface displays “Refresh failed.” At the same time, customer service and operations and maintenance receive an email notification to deal with the issue as soon as possible, even if the refresh failure does not affect the Content Delivery Network service.

### **Why is Content Delivery Network traffic used up when I haven’t used CNAME for the network?**

If the accelerated domain name service status is enabled, then it is possible that our detection equipment will still detect source station and acceleration details even if you haven’t “CNAME-ed” to the Windows Azure Content Delivery Network. This is also why we recommend that you choose smaller files whenever possible when you select URL monitoring. If you do not want accelerated domain names with no CNAME to consume data traffic, you can switch the service to the disabled status.
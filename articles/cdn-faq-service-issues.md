<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="Microsoft Azure CDN FAQs – Azure Feature Guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, cannot cache, cannot CNAME, origin rate high, cache refresh failed, CDN FAQ, CDN FAQS, CDN use failed, CDN service failure, CDN configuration error, speed slow, cannot open website, login exception, CNAME, CDN technical documentation, CDN help files" description="Find answers to common service consulting questions or inquiries related to the Microsoft Azure CDN" metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="11/27/2015"
    />
# FAQs - Service Issues

### **Why can’t I cache my URL?**

The inability to cache a URL is usually due to one of the following reasons:

1. The corresponding header for the URL on the source station includes the following information:
   - Set-Cookie (and the ignore Set-Cookie option has not been checked in the cache rules). Note: When Set-Cookie is used for user login and identification, the ignore Set-Cookie option cannot be checked; otherwise, it could cause problems with functions.
   - Cache-Control: no-store/no-cache/private (and the ignore Cache-Control option has not been checked in the cache rules).
   - The Expires time is a time in the past; Expires sets the point in time when the cache expires, so if it is a time in the past, it will make it impossible to cache.
   - The value of Max-age is very small; Max-age sets the length of the caching time in seconds, so if the value is too small, for example less than two digits, it will expire very quickly and make it impossible to cache.

2. The cache rules are not configured or are configured with errors such that the URL cannot hit any buffer rules; for example, if the user accidentally enters the rule “[Any Character] (.gif|.jpg|.bmp) (.gif|.jpg|.bmp)”, then it will be impossible to hit the rule even the file is of the picture type, because the file extension is duplicated.
   
3. No users have so far accessed the URL, as some nodes will only cache the content after it has been accessed.

### **Why are domain names resolved to the source station?**

If the acceleration region of a domain name CDN is Mainland China, overseas Internet users or Chinese Internet users using non-Chinese DNS resolutions may be resolved to the source station. The Azure CDN platform’s default configuration for such situations is to use CDN nodes in China to serve overseas visits.

### **CNAME cannot be used for system prompts**

Although we have not placed restrictions on accelerated domain names, it is possible that some domain name management companies do not allow the use of CNAME for domain names that include the host name. However, there are better ways to deal with this: either change the accelerated domain name, or change your domain name management company.

### **Why is return to source traffic greater than CDN traffic?**

In general, return to source traffic is less than or equal to CDN traffic, but in certain circumstances, return to source traffic can also be greater than CDN traffic, e.g. if the visitor sends a request for a relatively large file. For example, if a 100MB file has not been cached by the nodes, the CDN nodes will retrieve it from the source station, which for a file of this size inevitably takes some time; however, the visitor may not keep waiting at this time, with the result that the connection is disconnected. In such a situation, the CDN nodes will still bring over the entire 100MB file. By the time that the CDN nodes realize that the visitor no longer wants the file, it no longer has any way to go back, so the return to source traffic will reach 100MB, while the CDN traffic will not.

### **Opening speeds are even slower since I started using the CDN**

The cache hit rate is low. The cache hit rate can be affected by several factors:

- Cache configuration issues.
     
- The HTTP header causes inability to cache.
     
- The CDN acceleration node has only just been added, so the number of cached files is still small.
     
- The type of source station means that the amount of content that can be cached is small.
     
- Website visit numbers are low and the expiration time is short, so the number of files hit is small.

### **The return to source rate is relatively high** 

1. Cache rule configuration issues
    
2. The amount of resources that can be cached is small
    
3. The cache time is short

### **Websites will not open since I started using the CDN** 

Possible reasons:
 
1. Source station malfunctions.
     
2. The source station has a firewall that is shielding the CDN nodes.
    
3. The nodes are shielding the client IP.
     
4. If you have added a new domain name or the domain name status has changed and there is problem with the node configuration, you may need to wait for a while until the problem is resolved, typically around 60 minutes.
     
5. Equipment failures
    
### **There are issues with logging in to the website since I started using the CDN**

It is highly likely that resources that shouldn’t be cached have been set up in the cache rules, in which case, you need to set the user back-end login folder to not cache (e.g. /user or /admin); if it is a website with no login or with user responses, then please enable permission to ignore cookies in the cache rule configuration.

### **Cache refresh failure**

After a manual refresh is submitted, the system will identify the equipment that is working normally to allocate tasks, but if an anomaly occurs in a particular device during the allocation process, the system will automatically detect and disable it (clients will not be parsed to the relevant node after the service status has been closed, and it will not affect the acceleration service). Other normal devices will continue to be allocated tasks until they are complete, at which time, the interface will display “Refresh failed.” At the same time, customer service and operations and maintenance will receive an email notification to deal with the issue as soon as possible, even if the refresh failure does not affect the CDN service.

### **Why is CDN traffic used up when I haven’t used CNAME for the Windows Azure CDN?**

If the accelerated domain name service status is enabled, then it is possible that our detection equipment will still detect source station and acceleration details even if you haven’t “CNAME-ed” to the Windows Azure CDN. This is also why we recommend that you choose smaller files whenever possible when selecting URL monitoring. If you do not want accelerated domain names with no CNAME to consume data traffic, you can switch the service to the disabled status.

<!---HONumber=CDN_1201_2015-->
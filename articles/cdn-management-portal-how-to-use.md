<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="How to use the Microsoft Azure Content Delivery Network portal advanced features - Azure feature guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, cache refresh, content prefetch, log download, cache rules, CDN help files, CDN technical documentation, CDN" description="Learn how to use the advanced features of the Microsoft Azure portal to manage Content Delivery Network endpoints" metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="12/04/2015"
    />

# Microsoft Azure Content Delivery Network portal user guide

The Microsoft Azure Content Delivery Network caches static content in storage blobs, cloud services, and websites on the Azure platform by using large numbers of physical nodes distributed across Mainland China. These nodes provide developers with a solution for delivering high-bandwidth content. This service also currently supports the use of source stations that have not been deployed on the Azure platform.

For more details and pricing for Content Delivery Network, see [Introduction to the Microsoft Azure Content Delivery Network service](http://www.windowsazure.cn/documentation/services/cdn/).

+ [Overview](#step1)
+ [Domain name management](#step2)
+ [Traffic reports](#step3)
+ [Bandwidth reports](#step4)
+ [Cache refresh](#step5)
+ [Content prefetch](#step6)
+ [Log download](#step7)
+ [Service check](#step8)

## **Overview of the Microsoft Azure Content Delivery Network management page**<a id="step1"></a>

This page shows basic information on your Content Delivery Network subscription account.

![][1]

### **Shared accelerated domain names**

Statistics on accelerated domain names that were already created under the current Azure subscriptions.

### **Accelerated domain names that are already enabled**

Statistics on accelerated domain names that are currently enabled under the current Azure subscriptions.

### **Total traffic for the current month**

Total traffic in megabytes (MB) that were used by all accelerated domain names under the current Azure subscriptions during the current month.

### **Traffic for the current month**

Details of traffic in MB for each day in the current month under the current Azure subscriptions. If you need more detailed traffic information, you can click “Traffic Reports” in the left navigation pane to go to the traffic statistics report page.


### **Bandwidth for the current month**
Details of the peak bandwidth in kilobytes per second (Kb/s) for each day in the current month. If you need more detailed bandwidth information, click “Bandwidth Reports” in the left navigation pane to go to the bandwidth statistics report page.

![][2]
## **Domain name management**<a id="step2"></a>

Clicking “Domain Name Management” in the left navigation pane displays a list view of all Content Delivery Network acceleration domain names that were created under the current Azure subscriptions. You can select different subscriptions from the subscriptions drop-down list to see details of acceleration domain names under different subscriptions. You can also perform operations including **“edit configuration”**, **“cache rule configuration”** and **“access control management”** on accelerated domain names.

### **Accelerated domain name list view**

![][3]

#### **The domain name list view includes:**

-   Accelerated domain names, which are used to access Content Delivery Network cached content. These domain names must be accompanied by the corresponding ICP record details.
-   Content Delivery Network domain names, which are provided by the Content Delivery Network platform and all end with **.mschcdn.com**.
-   Source station addresses, which are the origin domain for content cached on the Content Delivery Network.
-   Acceleration type, which includes the acceleration types that are currently supported: “website acceleration”, “download acceleration”, “HTTP VoD acceleration”, and “live streaming media acceleration”.
-   Status, which may be either enabled or disabled (including ICP approval, requires CNAME configuration, banned, and other **non-enabled** statuses).

>**Note** that you need to configure the CNAME mapping details for your accelerated domain name after the Content Delivery Network service takes effect (within 60 minutes). Then you can map it to the network domain name provided by Microsoft.

>**Note** that only domain names with an **enabled** status can use the network service normally.

#### **Cache rule configuration view**
 
![][4]

The system sets default rules based on the cache rules, as shown in the picture above. You can adjust these settings to your own requirements. User rules are given priority in matching. If there are no hits for user rules, the system default cache rules are implemented item by item.


#### **Cache rule configuration**

You can click “Cache rule configuration” and then set the required cache rules for domain names, including:

- Directory-based configuration.

	Directories must begin with “/”, for example, /pic, /doc, or /htdoc/data. The back end matches all files within the designated directory, **including subdirectories**.

- File extension-based configuration.

	The back end matches common file extensions, such as .jpg, .png, .gif, .txt, .m4v, or .mp3 **within all folders**.

- Full path-based configuration

	These are used to specify **a single file**, and must start with a forward slash (/). For example, "/sites/doc/example.doc". **Note**: If the path entered by the user is “/”, it will match the homepage.

>**Note** that the character strings entered by the user when configuring rules must not include special characters such as “{”, “}”, “(”, “)”, “[”, “]”, “.”, “?”, “*”, “\\”, “^”, or “$”.

>**Note** that entering a time of “0” means that caching is prohibited.

#### **Cache configuration order**

The system **performs matching item by item** on the basis of the order of configuration, with the rule configured first given the highest priority level. Once a rule is matched, subsequent rules are **no longer** matched.

#### **Custom templates**

Users can use “Apply a custom template” to quickly create cache configuration rules. The diagram above shows a rule created after the user goes into “Apply a custom template” and selects “Common files”. Users can edit the automatically created rules as required.

#### **Prohibiting cache setup**

If the user checks the “Set to caching prohibited” option, the accelerated domain name is not cached.

#### **Access control management**

You can use access control management to set up and configure referer blacklists and whitelists, and thereby implement an anti-theft chain.

![][5]

Once the anti theft chain is enabled, you can edit the external link rules. Each rule is made up of a path and a filename, for example, / *.png means all png files in the root directory.

Each rule is made up of a path and a filename, for example, / *.png means all png files in the root directory.

- If you set up a blacklist, access is denied if the referer is in the blacklist, but is otherwise permitted.
- If you set up a whitelist, access is permitted only if the referer is one of the domain names in the whitelist.

Once you have clicked “Submit” and waited for the operation to finish, the interface shows whether the operation was successful. If you click “Submit and close”, then the dialog box closes immediately. The next time you open the dialog box, you see the status of the last operation.

## **Traffic statistics reports**<a id="step3"></a>

Select the subscription (choose one), time range, and accelerated domain names (individual domain names or all of them) you wish to check, then click **Refresh**. The interface displays traffic statistics reports that meet the conditions you specified. Refer to the explanations on the actual interface page for data format details and implications.

![][6]

**Traffic statistics reports have the following functions:**

-   If you have multiple Azure subscriptions, you can check traffic statistics for individual subscriptions, as well as return-to-source traffic statistics.
-   If you have Azure subscriptions with multiple accelerated domain names, you can view individual accelerated domain name traffic (and return-to-source traffic) statistics results and summaries of all accelerated domain name traffic (and return-to-source traffic).
-   The highest level for queries is accurate to the hour.
-   Traffic statistics provide multiple time range types for queries. You can check traffic statistics for the last 24 hours, yesterday, today, the last 7 days, the last 15 days, the last 30 days, or the last month. You can also check traffic and return-to-source traffic for a specific time period, which cannot exceed 90 days.

## **Bandwidth statistics reports**<a id="step4"></a>

Select the subscription (choose one), time range, and accelerated domain names (individual domain names or all of them) you wish to check, then click **Refresh**. The interface displays bandwidth statistics reports that meet the conditions you specified. Refer to the explanations on the actual interface page for data format details and implications.

![][7]

**Bandwidth statistics reports have the following functions:**

-   If you have multiple Azure subscriptions, you can check bandwidth statistics for individual subscriptions, as well as return-to-source bandwidth statistics.
-   If you have Azure subscriptions with multiple accelerated domain names, you can view individual accelerated domain name bandwidth (and return-to-source traffic) statistics results and summaries of all accelerated domain name bandwidth (and return-to-source traffic) information.
-   The highest level for queries is accurate to the hour.
-   Bandwidth statistics display the time at which peak bandwidth levels occur.
-   Bandwidth statistics provide flexible time range options for queries. You can check bandwidth statistics for the last 24 hours, yesterday, today, the last 7 days, the last 15 days, the last 30 days, or the last month. You can also check bandwidth statistics for a specific time period, which cannot exceed 90 days.

## **Cache refresh**<a id="step5"></a>

Clicking “Cache Refresh” in the bottom-left navigation pane performs a manual refresh of the specified files or directories.

### **Cache refresh list view**

Select the subscription (choose one), status, time range, and accelerated domain name (choose one) you wish to check, then click **Check Refresh Results**. The interface displays cache refresh records that meet the conditions you specified. Refer to the explanations on the actual interface page for data format details and implications.

![][8]

#### **Cache refresh list view includes:**

-   Accelerated domain names, which are URLs that are used to access Content Delivery Network cache content.
-   Status (common statuses: successful, failed, or refreshing)
-   Submission time
-   Test time

If you successfully submitted the cache refresh rules, the status bar shows the word “Successful”. If you did not successfully submit them, you must check that the cache refresh rules were correct. If there are any problems, you must re-create and re-submit the cache refresh rules.

### **Cache refresh rule submission**

You can configure cache refresh rules for individual files or for all files within a directory.

#### **File cache refresh rule submission**

![][9]

This task includes the steps listed below:

1. Click “Submit File Refresh” to enter the file refresh view.
2. In the “File Refresh” dialog box, select the domain name you wish to configure from the list of accelerated domain names, and then enter the corresponding file path.
3. Click “+” to add a new rule or “x” to delete the corresponding file.
4. Click “Submit”.

The newly created file cache rules then appear in the cache refresh list view.

>**Note** that until the accelerated domain name has passed the ICP verification process, it is not possible to perform a file refresh operation and the accelerated domain name drop-down list appears empty. Wait until it has passed back-end verification.

#### **Directory cache refresh rule submission**

![][10]

This task includes the steps listed below:

1. click “Submit Directory Refresh” to enter the directory refresh view.
2. In the “Directory Refresh” dialog box, select the domain name you wish to configure from the list of accelerated domain names, and then enter the corresponding directory path.
3. Click “+” to add a new rule or “x” to delete the corresponding directory.
4. Click “Submit”.

The newly created directory cache rules then appear in the cache refresh list view.

## **Content prefetch**<a id="step6"></a>
Click “Content Prefetch” in the left navigation pane to perform content prefetch and prefetch progress query operations for specific files.

Content prefetch means caching the content of a designated URL from the source station to the Content Delivery Network nodes. This eliminates the waiting time the first time that you access the resource. Content prefetching is generally used in scenarios that involve the delivery of large files, where it can effectively improve the user access experience.

### **Content prefetch list view**

Select the subscription (choose one), status, time range, and accelerated domain name (choose one) you wish to check, and then click **Check Prefetch Results**. The interface displays precaching records that meet the conditions you specified. Refer to the explanations on the actual interface page for data format details and implications.

![][11]

#### **The content prefetch list view includes:**

-   Accelerated domain names, which are URLs that are used to access Content Delivery Network cache content.
-   Status (common statuses: successful, failed, or in progress)
-   Submission time


If you successfully submitted the precache rules, the status bar shows the word “Successful”. If you did not successfully submit them, you must check that the precache rules were correct. If there are any problems, you must re-create and re-submit the precache rules.

### **Precache rule submission**

You can configure precaching for individual files or multiple files.

![][12]

This task includes the steps listed below:

1. Click on “Submit Precache Loading” to enter the precache loading view.
2. In the “Precache Loading” dialog box, select the domain name you wish to configure from the list of accelerated domain names, and then enter the corresponding file path.
3. Click “+” to add a new rule or “x” to delete the corresponding file.
4. Click “Submit”.

The newly created precache loading rules then appear in the precache loading list view.

## **Log download**<a id="step7"></a>
Click “Log Download” in the left navigation pane to set Content Delivery Network raw log download parameters for specific domain names.

### **Log download view**
To download logs, you must first provide an Azure storage account that is used to save Content Delivery Network logs. Click “Download Settings” to set this up.

![][13]

### **Download settings view**

You can set the storage account and the domain names for which log downloads are required in the “Download Settings” view. Once the setup is complete, the system automatically saves the logs that it finds to the designated storage account. You can delete the storage account to cancel log downloads.

![][14]

### **Log format details**
Logs are saved in blob format with a container called "cdn-access-logs". Every blob consists of a .csv file that is compressed with GZip. The meaning of each column within the log is given below:

- c-ip: Client IP address
- timestamp: Access time
- cs-method: HTTP request actions, such as GET/HEAD
- cs-uri-stem: Requested URI 
- http-ver: HTTP protocol version number
- sc-status: HTTP status code 
- sc-bytes: Number of bytes sent to the client by the server
- c-referer: Client-side referer URI
- c-user-agent: Client user agent identification
- rs-duration (ms): Time taken to complete the request (in milliseconds)
- hit-miss: Content Delivery Network cache hit and miss identification
- s-ip: IP address of the Content Delivery Network edge node that generated the log

>**Note** that if the Content Delivery Network log does not contain content for a particular column, the corresponding record, for example the “c-referer” record, will be marked “-”. Also, depending on the edge node log configuration, the “rs-duration”, “hit-miss” and “s-ip” columns may also be empty.

>**Note** that once a website has been accelerated by the Content Delivery Network, the majority of its access records come from network edge nodes. When the network returns to the source, it enters the originating IP address in HTTP Header X-Forwarded-For, and the source station’s web server can edit the log to configure this information. If you need to find out the originating IP address of the client, you can refer to the information below.

>If we take NGINX as an example, you can add the following information to the configuration file:

>log\_format logCDN '$remote\_addr forwarded for $http\_x\_forwarded\_for - $remote\_user [$time\_local] ' '"$request" $status $body\_bytes\_sent ' '"$http\_referer" "$http\_user\_agent"';

>access\_log /var/log/nginx/access.log logCDN;

## **Service check**<a id="step8"></a>

Once you have created a Content Delivery Network service endpoint, you can perform some basic checks in the “Service Check” view. We strongly recommend that you perform service checks before you carry out CNAME operations.

![][15]

As shown in the view above, you must select the domain name to be checked, provide a resource that the source station can access, and then click “Check”.

1. Source station normal indicates that the resource provided can be accessed.
2. Content Delivery Network deployment complete indicates that the network services corresponding to the domain name have been deployed.
3. Content Delivery Network cache normal indicates that the content that was accessed via the source station is consistent with the content that was accessed via Content Delivery Network (by comparing HTTP headers: HTTP Status Code, Last Modified Time, and Content Length).

>**Note** that using the service check function does not guarantee that there are no anomalies in any of the network edge servers where the domain name is located.

 

[1]: ./media/cdn-unified-portal/001.png
[2]: ./media/cdn-unified-portal/002.png
[3]: ./media/cdn-unified-portal/003.png
[4]: ./media/cdn-unified-portal/cache-policy-2.png
[5]: ./media/cdn-unified-portal/access-control.png
[6]: ./media/cdn-unified-portal/004.png
[7]: ./media/cdn-unified-portal/005.png
[8]: ./media/cdn-unified-portal/006.png
[9]: ./media/cdn-unified-portal/007.png
[10]: ./media/cdn-unified-portal/008.png
[11]: ./media/cdn-unified-portal/prefetch-1.png
[12]: ./media/cdn-unified-portal/prefetch-2.png
[13]: ./media/cdn-unified-portal/log-download-1.png
[14]: ./media/cdn-unified-portal/log-download-2.png
[15]: ./media/cdn-unified-portal/service-check.png
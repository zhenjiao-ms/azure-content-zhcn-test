<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="How to Use Microsoft Azure CDN Management Portal Advanced Features - Azure Feature Guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, cache refresh, content prefetch, log download, cache rules, CDN help files, CDN technical documentation, CDN" description="Learn how to use advanced features of Microsoft Azure CDN Management Portal to manage CDN endpoints" metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="12/04/2015"
    />

# Microsoft Azure CDN Management Portal User Guide

The Microsoft Azure content delivery network (CDN) caches static content in Storage Blobs, Cloud Services, and websites on the Azure platform using large numbers of physical nodes distributed across Mainland China, in order to provide developers with a solution for delivering high-bandwidth content. This CDN service also currently supports the use of source stations that have not been deployed on the Azure platform.

For more details and pricing for Microsoft Azure CDN, see [Introduction to the Microsoft Azure CDN Service](http://www.windowsazure.cn/documentation/services/cdn/).

+ [Overview](#step1)
+ [Domain Name Management](#step2)
+ [Traffic Reports](#step3)
+ [Bandwidth Reports](#step4)
+ [Cache Refresh](#step5)
+ [Content Prefetch](#step6)
+ [Log Download](#step7)
+ [Service Check](#step8)

## **Overview of the Microsoft Azure CDN Management Page**<a id="step1"></a>

This page shows basic information on your CDN subscription account.

![][1]

### **Shared accelerated domain names**

Statistics on accelerated domain names already created under the current Azure subscriptions.

### **Accelerated domain names that are already enabled**

Statistics on accelerated domain names that are currently enabled under the current Azure subscriptions.

### **Total traffic for the current month**

Total traffic in megabytes (MB) used by all accelerated domain names under the current Azure subscriptions during the current month.

### **Traffic for the current month**

Details of traffic in megabytes (MB) for each day in the current month under the current Azure subscriptions. If you need more detailed traffic information, you can single-click on “Traffic Reports” in the left navigation pane to go into the traffic statistics report page.


### **Bandwidth for the current month**
Details of the peak bandwidth in Kb/s for each day in the current month. If you need more detailed bandwidth information, you can single-click on “Bandwidth Reports” in the left navigation pane to go into the bandwidth statistics report page.

![][2]
## **Domain Name Management**<a id="step2"></a>

Single-clicking on “Domain Name Management” in the left navigation pane will display a list view of all CDN acceleration domain names created under the current Azure subscriptions. You can select different subscriptions from the Azure subscriptions drop-down list to see details of CDN acceleration domain names under different subscriptions. You can also perform operations including **“Edit Configuration”**, **“Cache Rule Configuration”** and **“Access Control Management”** on accelerated domain names.

### **Accelerated domain name list view**

![][3]

#### **The domain name list view includes:**

-   Accelerated domain names, i.e. domain names used to access CDN cached content; these domain names must be accompanied by the corresponding ICP record details.
-   CDN domain names, which are provided by the Microsoft Azure CDN platform and all end with **.mschcdn.com**.
-   Source station addresses, i.e. the origin domain for content cached on the CDN.
-   Acceleration type (the acceleration types currently supported are “Website Acceleration”, “Download Acceleration”, “HTTP VOD Acceleration”, and “Live Streaming Media Acceleration”).
-   Status, which may be either enabled or disabled (including ICP approval, requires CNAME configuration, banned, and other **non-enabled** statuses).

>**Note** that you need to configure the CNAME mapping details for your accelerated domain name after the CDN service takes effect (within 60 minutes), in order to map it to the CDN domain name provided by Microsoft.

>**Note** that only domain names with an **enabled** status can use the CDN service normally.

#### **Cache rule configuration view**
 
![][4]

The system will set default rules based on the cache rules, as shown in the picture above. Users can adjust these settings to their own requirements. User rules are given priority in matching, and if there are no hits for user rules, the system default cache rules will be implemented item by item.


#### **Cache rule configuration**

Users can click on “Cache rule configuration” and then set the required cache rules for domain names, including:

- Directory-based configuration

	Directories must begin with “/”, for example "/pic", "/doc" or "/htdoc/data". The back-end will match all files within the designated directory, **including subdirectories**.

- File extension-based configuration.

	Common file extension, such as "jpg", "png", "gif", "txt", "m4v" or "mp3". The back-end will match the specified file extension **within all folders**.

- Full path-based configuration

	Used to specify **a single file**, must start with "/". For example "/sites/doc/example.doc". **Note**: If the path entered by the user is “/”, it will match the homepage.

>**Note** that the character strings entered by the user when configuring rules must not include special characters such as “{”, “}”, “(”, “)”, “[”, “]”, “.”, “?", “*”, “\\”, “^”, “$”.

>**Note** that entering a time of “0” means that caching is prohibited.

#### **Cache configuration order**

The system will **perform matching item by item** on the basis of the order of configuration, with the rule configured first given the highest priority level. Once a rule is matched, subsequent rules will **no longer** be matched.

#### **Custom templates**

Users can use “Apply a custom template” to quickly create cache configuration rules. The diagram above shows a rule created after the user goes into “Apply a custom template” and selects “Common files”. Users can edit the automatically created rules as required.

#### **Prohibiting cache setup**

If the user checks the “Set to caching prohibited” option, the accelerated domain name will not be cached.

#### **Access control management**

Users can use access control management to set up and configure referer blacklists/whitelists, and thereby implement an anti-theft chain.

![][5]

Once the anti-theft chain is enabled, you can edit the external link rules. Each rule is made up of a path and a filename. For example, / *.png means all png files in the root directory.

Each rule is made up of a path and a filename. For example, / *.png means all png files in the root directory.

- If you set up a blacklist, access will be denied if the referer is in the blacklist, but will otherwise be permitted.
- If you set up a whitelist, access will only be permitted if the referer is one of the domain names in the whitelist.

Once you have clicked on the “Submit” button and waited for the operation to finish, the interface will show whether the operation was successful. If you click on the “Submit and close” button, then the dialog box will close immediately. The next time the user opens the dialog box, it will show the status of the last operation.

## **Traffic Statistics Reports**<a id="step3"></a>

Select the subscription (choose one), time range and accelerated domain names (individual domain names or all of them) you wish to check, then single-click on the **Refresh** button. The interface will display traffic statistics reports that meet the conditions you specified. Please refer to the explanations on the actual interface page for data format details and implications.

![][6]

**Traffic statistics reports have the following functions:**

-   Users with multiple Azure subscriptions can check traffic statistics for individual subscriptions, as well as return to source traffic statistics.
-   If you have Azure subscriptions with multiple accelerated domain names, you can view individual accelerated domain name traffic (and return to source traffic) statistics results and summaries of all accelerated domain name traffic (and return to source traffic).
-   The highest level for queries is accurate to the hour.
-   Provides multiple time range types for queries. Users can check traffic statistics for the last 24 hours, yesterday, today, the last 7 days, the last 15 days, the last 30 days, or last month. Users can also check traffic and return to source traffic for a specific time period (the time range for statistics cannot exceed 90 days).

## **Bandwidth Statistics Reports**<a id="step4"></a>

Select the subscription (choose one), time range and accelerated domain names (individual domain names or all of them) you wish to check, then single-click on the **Refresh** button. The interface will display bandwidth statistics reports that meet the conditions you specified. Please refer to the explanations on the actual interface page for data format details and implications.

![][7]

**Bandwidth statistics reports have the following functions:**

-   Users with multiple Azure subscriptions can check bandwidth statistics for individual subscriptions, as well as return to source bandwidth statistics.
-   If you have Azure subscriptions with multiple accelerated domain names, you can view individual accelerated domain name bandwidth (and return to source traffic) statistics results and summaries of all accelerated domain name bandwidth (and return to source traffic) information.
-   The highest level for queries is accurate to the hour.
-   Displays the time at which peak bandwidth levels occur.
-   Provides flexible time range options for queries. You can check bandwidth statistics for the last 24 hours, yesterday, today, the last 7 days, the last 15 days, the last 30 days, or last month. Users can also check bandwidth statistics for a specific time period (the time range for statistics cannot exceed 90 days).

## **Cache Refresh**<a id="step5"></a>

Single-clicking on “Cache Refresh” in the bottom left navigation pane performs a manual refresh of the specified files or directories.

### **Cache refresh list view**

Select the subscription (choose one), status, time range and accelerated domain name (choose one) you wish to check, then single-click on **Check Refresh Results**. The interface will display cache refresh records that meet the conditions you specified. Please refer to the explanations on the actual interface page for data format details and implications.

![][8]

#### **Cache refresh list view includes:**

-   Accelerated domain names, which are URLs used to access CDN cache content.
-   Status (common statuses: successful, failed, refreshing)
-   Submission time
-   Test time

If the cache refresh rules were successfully submitted, the status bar will show the word “Successful”. If they were not successfully submitted, you will need to check that the cache refresh rules were correct. If there are any problems, you will need to recreate and resubmit the cache refresh rules.

### **Cache refresh rule submission**

You can configure cache refresh rules for individual files, or for all files within a directory.

#### **File cache refresh rule submission**

![][9]

This task includes the steps listed below:

1. Single-click on the “Submit File Refresh” button to enter the file refresh view.
2. In the “File Refresh” dialog box, select the domain name you wish to configure from the list of accelerated domain names, and enter the corresponding file path.
3. You can single-click on “+” to add a new rule, or “x” to delete the corresponding file.
4. Single-click on “Submit”.

The newly-created file cache rules will then be displayed in the cache refresh list view.

>**Note** that until the accelerated domain name has passed the ICP verification process, it will not be possible to perform a file refresh operation, and the accelerated domain name drop-down list will appear empty. Please wait until it has passed back-end verification.

#### **Directory cache refresh rule submission**

![][10]

This task includes the steps listed below:

1. Single-click on the “Submit Directory Refresh” button to enter the directory refresh view.
2. In the “Directory Refresh” dialog box, select the domain name you wish to configure from the list of accelerated domain names, and enter the corresponding directory path.
3. You can single-click on “+” to add a new rule, or “x” to delete the corresponding directory.
4. Single-click on “Submit”.

The newly-created directory cache rules will then be displayed in the cache refresh list view.

## **Content Prefetch**<a id="step6"></a>
Single-click on “Content Prefetch” in the left navigation pane to perform content prefetch and prefetch progress query operations for specific files.

Content prefetch means caching the content of a designated URL from the source station to the CDN nodes, in order to eliminate the waiting time the first time that the user accesses the resource. Content prefetching is generally used in scenarios involving the delivery of large files, where it can effectively improve the user access experience.

### **Content prefetch list view**

Select the subscription (choose one), status, time range and accelerated domain name (choose one) you wish to check, then single-click on **Check Prefetch Results**. The interface will display pre-caching records that meet the conditions you specified. Please refer to the explanations on the actual interface page for data format details and implications.

![][11]

#### **The content prefetch list view includes:**

-   Accelerated domain names, which are URLs used to access CDN cache content.
-   Status (common statuses: successful, failed, in progress)
-   Submission time


If the pre-cache rules were successfully submitted, the status bar will show the word “Successful”. If they were not successfully submitted, you will need to check that the pre-cache rules were correct. If there are any problems, you will need to recreate and resubmit the pre-cache rules.

### **Pre-cache rule submission**

You can configure pre-caching for individual files or multiple files.

![][12]

This task includes the steps listed below:

1. Single-click on the “Submit Pre-cache Loading” button to enter the pre-cache loading view.
2. In the “Pre-cache Loading” dialog box, select the domain name you wish to configure from the list of accelerated domain names, and enter the corresponding file path.
3. You can single-click on “+” to add a new rule, or “x” to delete the corresponding file.
4. Single-click on “Submit”.

The newly-created pre-cache loading rules will then be displayed in the pre-cache loading list view.

## **Log Download**<a id="step7"></a>
Single-click on “Log Download” in the left navigation pane to set CDN raw log download parameters for specific domain names.

### **Log download view**
In order to download logs, the user must first provide an Azure Storage Account used to save CDN logs. Click on “Download Settings” to set this up.

![][13]

### **Download settings view**

Users can set the Storage Account and the domain names for which log downloads are required in the “Download Settings” view. Once the setup is complete, the system will automatically save the logs it finds to the designated Storage Account. 
Users can delete the Storage Account to cancel log downloads.

![][14]

### **Log format details**
Logs are saved in Blob format with a container called "cdn-access-logs". Every Blob consists of a CSV file compressed with GZip. The meaning of each column within the log is given below:

- c-ip: client IP address
- timestamp: access time
- cs-method: HTTP request actions, such as GET/HEAD
- cs-uri-stem: the requested URI 
- http-ver: the HTTP protocol version number
- sc-status: HTTP status code 
- sc-bytes: number of bytes sent to the client by the server
- c-referer: client-side referer URI
- c-user-agent: client user agent identification
- rs-duration (ms): time taken to complete the request (in milliseconds)
- hit-miss: CDN cache hit and miss identification
- s-ip: IP address of the CDN edge node generating the log

>**Note** that if the CDN log does not contain content for a particular column, the corresponding record, for example the “c-referer” record, will be marked “-”. Also, depending on the edge node log configuration, the “rs-duration”, “hit-miss” and “s-ip” columns may also be empty.

>**Note** that once a website has been accelerated by the CDN, the majority of its access records will come from CDN edge nodes. When the CDN goes back to the source, it will enter the originating IP address in HTTP Header X-Forwarded-For, and the source station’s web server can edit the log to configure this information. If you need to find out the originating IP address of the client, you can refer to the information below.

>If we take NGINX as an example, you can add the following information to the configuration file:

>log_format logCDN '$remote_addr forwarded for $http_x_forwarded_for - $remote_user [$time_local]  '
                  '"$request" $status $body_bytes_sent '
                  '"$http_referer" "$http_user_agent"';

>access_log /var/log/nginx/access.log logCDN;

## **Service Check**<a id="step8"></a>

Once you have created a CDN service endpoint, you can perform some basic checks in the “Service Check” view. We strongly recommend that users perform service checks before carrying out CNAME operations.

![][15]

As shown in the view above, the user must select the domain name to be checked, provide a resource that the source station can access, and then click on “Check”.

1. Source station normal - indicates that the resource provided can be accessed.
2. CDN deployment complete - indicates that the CDN services corresponding to the domain name have been deployed.
3. CDN cache normal - indicates that the content accessed via the source station is consistent with the content accessed via the CDN (by comparing HTTP headers: HTTP Status Code, Last Modified Time, Content Length).

>**Note** that using the Service Check function does not guarantee that there are no anomalies in any of the CDN edge servers where the domain name is located.

 

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

<!---HONumber=CDN_1201_2015-->
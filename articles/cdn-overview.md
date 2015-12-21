<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="Overview of Microsoft Azure CDN in China - Azure Feature Guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, CDN, CDN acceleration, CDN service, mainstream CDN, multi-scenario acceleration, free CDN, CDN website acceleration, website acceleration, webpage acceleration, static acceleration, download acceleration, VOD acceleration, streaming media webcast acceleration, cloud service,  storage account, cache refresh, return to origin, cloud acceleration, acceleration results, node, traffic, CNAME, bandwidth, network speed, anti-theft chain, https acceleration, low-cost bandwidth, access acceleration, small file acceleration, download acceleration, large file acceleration, streaming media acceleration, HTTPS secure acceleration, cache refresh, content pre-loading, anti-theft chain, log download, CDN technical documentation, CDN help files, CDN FAQs" description="Get an overview of Microsoft Azure CDN and its advantages, typical scenarios and key features." metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="12/4/2015"
    />

# Overview of Microsoft Azure CDN (Content Delivery Network)

The Microsoft Azure (content delivery network) caches static content in Storage Blobs, Cloud Services, and Websites on the Azure platform using large numbers of physical nodes distributed across Mainland China, providing media services with acceleration for streaming content delivery, and offering developers with solutions for delivering high-bandwidth content. This CDN service also currently supports the use of source stations that have not been deployed on the Azure platform.

For more details and pricing for Microsoft Azure CDN, see [Introduction to the Microsoft Azure CDN Service](http://www.windowsazure.cn/home/features/cdn/).

If you are an existing user of the Microsoft Azure CDN, please visit the [Microsoft Azure CDN Management Portal](https://manage.windowsazure.cn) to manage CDN acceleration domain names. See [Using Microsoft Azure CDN](http://www.windowsazure.cn/documentation/articles/cdn-how-to-use/) for a more specific user guide.

+ [What is a CDN?](#step1)
+ [Advantages of Microsoft Azure CDN](#step2)
+ [Features of Microsoft Azure CDN](#step3)

## What is a CDN?<a id="step1"></a>

CDN stands for content delivery network. Virtually all large-scale websites make use of this technology today, but the technology is by no means exclusive to large websites. The basic thinking behind CDNs is to avoid bottlenecks and other parts of the Internet that could affect data transfer rates and stability, in order to make content transfers faster and more stable. By placing node servers in different places across the network and building a more intelligent layer of virtual networks using the Internet as a foundation, CDN systems can redirect user requests in real time to the service node closest to the user based on the status of network traffic and node connections and loads, as well as overall information on distance to the user and response times.
 
Taking the Microsoft website as an example, Microsoft may be an American company, but its customers are distributed across the globe. This means that there are users in every part of the world who need to access the Microsoft website or download product updates from Microsoft Update. If the website servers were only deployed in a single location in the US, users in the areas around this location could undoubtedly achieve satisfactory speeds when accessing the website, as the distances involved would be small and network delays would also be minimal. However, if a user in China tried to download product updates from a server in this US location, this would require that all the data packets were transferred back and forth between China and the US. As the total length of the route extends to thousands of kilometers, this would cause enormous delays.

However, this problem can be solved by placing CDN nodes in China. The CDN nodes automatically cache data to data centers in the major cities throughout China, shortening the distance between users and content, and thereby reducing the time required to transfer data. Using CDN caching means that users can obtain content from a nearby location, resolving the issue of Internet network congestion, and increasing the response speed for users accessing websites and apps.


![][4]


## Advantages<a id="step2"></a>

### Built-in support for many types of Microsoft Azure services

Native support for a number of different Microsoft Azure services, including Storage Blobs, Cloud Services, websites and media services, is offered by default, providing the user with comprehensive, one-stop cloud service support.

![][1]


### Full self-service model

Traditional CDN services require a large amount of complex and tedious configuration processes. However, Microsoft Azure CDN users can accomplish every imaginable task themselves using the Microsoft Azure Management Portal and the dedicated CDN Management Portal, from creating CDN acceleration nodes to the subsequent management of the entire node life cycle, as well as checking a wide range of statistical reports, downloading raw access logs, and configuring various advanced functions (such as cache rule configuration, forced refreshing of cached content, content pre-loading, and anti-theft chains).

![][2]  

![][3]

### Dynamic optimization of all network nodes

The Microsoft Azure CDN service integrates mainstream CDN services from a number of China-based companies to provide comprehensive static webpage acceleration and acceleration for a range of service types, including download delivery for large files such as software installation packages, game clients, apps and videos, and VOD (video on demand) and streaming (direct-broadcast) targeted primarily at online video websites and online educational websites, thereby meeting the delivery needs of different types of resource. It also provides full network coverage spanning the entire region for mainstream telecoms carriers including China Telecom, China Unicom and China Mobile, as well as other ISPs, and allocates user requests to the optimal node using load balancing technology and intelligent dispatch strategies based on the real-time network status.


### Reduces costs

Microsoft Azure CDN leverages the advantages of cooperation between mainstream CDN services from several companies to provide all Azure users - including business clients and website payment users - with high-quality, low-cost CDN services. This allows even more users to enjoy the benefits that CDN services bring.

## Acceleration for multiple scenarios

The Microsoft Azure CDN service supports all the different acceleration scenarios described below, creating a comprehensive and multidimensional acceleration service for users.

![][8]

### Website and small file acceleration

One classic usage scenario for CDNs is providing acceleration for the so-called “small files” (e.g. HTML webpage files, image files, JavaScript files or CSS files) used by many websites, allowing the website to deliver a better user experience, and thereby increasing user visits and ultimately driving up revenues for the entire business. The typical user group would be small, medium and large enterprises providing website services for Internet users.

### Download delivery for large files

Another typical usage scenario for CDNs is to facilitate multi-node delivery of large file downloads, which ultimately ensures that the download experience proceeds smoothly. Without the use of CDN services, typical user scenarios such as operating system (OS) and firmware upgrades, publishing new games online (which require downloading client installation packages), and mobile app updates, would have a huge impact on source station bandwidth usage and could even cause the source station to stop working.

### Streaming media acceleration

As the range of online video and media services has grown over the last few years, increasing numbers of people have got used to using Internet platforms to watch videos and listen to audio content. Given the limitations on the Internet environment in China, this places huge demands on the final delivery of audio and video content. The typical user group is all types of media website and mobile app clients providing services to Internet users.

### HTTPS secure acceleration

Security will always be the issue that users are most concerned about. In terms of how this specifically relates to CDN services, the Microsoft Azure CDN not only provides comprehensive acceleration for HTTP access, but also offers a dedicated HTTPS acceleration service for users that need access via the HTTPS access protocol. In terms of usage scenarios, this service could be categorized as a small file acceleration service, but also provides certain dynamic routing access optimization services.


## Functions<a id="step3"></a>

### Full self-service creation and management of CDN acceleration nodes

The Microsoft Azure CDN provides extensive self-service management and configuration services for the entire life cycle of CDN acceleration nodes, including functions such as creating, deleting, enabling and banning CDN acceleration nodes, as well as editing source stations.

![][5]

### Visualized queries for traffic and bandwidth information

The dedicated Microsoft Azure CDN Management Portal allows for easy, quick and clear checking of traffic and bandwidth usage details for CDN acceleration domain names.

![][6]

![][7]


### Cache rule configuration

The system already provides default cache rules for various types of CDN acceleration. Users can also customize and edit rules according to their actual requirements, in order to achieve the goal of flexible control over content cache times.

![][9]

### Anti-theft chain

The Microsoft Azure CDN provides CDN content access control features to address the specific needs of users in China, including an anti-theft chain. Users can use these features to take better and more effective control over their accelerated content, in order to achieve the goal of keeping content protected.

![][10]


### Cache refreshing

Sometimes when users finish updating a particular file on the source station, they want to see the results of the update reflected on the CDN service nodes in real time. However, as the CDN has default or user-defined cache rules, the updated changes are not generally apparent on all CDN nodes in real time. It is at times like this that the “cache refresh” function really comes into its own, as the user can force a cache refresh for individual files or batches of files. The goal is to make the CDN service clear the file(s) designated by the user from all CDN nodes, so that the next time a user accesses one of these files they will obtain the updated file.

![][11]

### Content pre-loading

Content pre-loading means caching the content of a designated URL from the source station to the CDN nodes, in order to eliminate the waiting time the first time that the user accesses the resource. Content prefetching is generally used in scenarios involving the delivery of large files, where it can effectively improve the user access experience.

![][12]

### Log downloads

Users sometimes need to perform statistical analyses of CDN acceleration effectiveness or raw access information. In such situations, users can obtain such raw access information using the “log download” function. The user will need to provide an accessible Azure Storage account to use this feature, as the Microsoft Azure CDN will save the log access files for the corresponding customer(s) on this account.

![][13]

### Service checks

Once you have created a CDN service endpoint, you can use the “Service Check” view to see whether it is possible to access the source station, whether CDN deployment is complete, and whether CDN caching is working normally.

![][14]

<!--Image references-->
[1]: ./media/cdn-overview/overview01.png
[2]: ./media/cdn-overview/image005.png
[3]: ./media/cdn-overview/overview02.png
[4]: ./media/cdn-overview/overview03.png
[5]: ./media/cdn-overview/overview04.png
[6]: ./media/cdn-overview/overview05.png
[7]: ./media/cdn-overview/overview06.png
[8]: ./media/cdn-overview/overview07.png
[9]: ./media/cdn-overview/overview08.png
[10]: ./media/cdn-overview/overview09.png
[11]: ./media/cdn-overview/overview10.png
[12]: ./media/cdn-overview/overview11.png
[13]: ./media/cdn-overview/overview12.png
[14]: ./media/cdn-overview/overview13.png

<!---HONumber=CDN_1201_2015-->
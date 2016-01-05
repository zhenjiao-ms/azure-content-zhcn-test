<properties linkid="dev-net-common-tasks-cdn" urlDisplayName="CDN" pageTitle="Overview of Microsoft Azure Content Delivery Network in China: Azure feature guide" metaKeywords="Azure CDN, Azure CDN, Azure blobs, Azure caching, Azure add-ons, CDN, CDN acceleration, CDN service, mainstream CDN, multi-scenario acceleration, free CDN, CDN website acceleration, website acceleration, webpage acceleration, static acceleration, download acceleration, VOD acceleration, streaming media webcast acceleration, cloud service,  storage account, cache refresh, return to origin, cloud acceleration, acceleration results, node, traffic, CNAME, bandwidth, network speed, anti-theft chain, https acceleration, low-cost bandwidth, access acceleration, small file acceleration, download acceleration, large file acceleration, streaming media acceleration, HTTPS secure acceleration, cache refresh, content pre-loading, anti-theft chain, log download, CDN technical documentation, CDN help files, CDN FAQs" description="Get an overview of Microsoft Azure Content Delivery Network and its advantages, typical scenarios and key features." metaCanonical="" services="" documentationCenter=".NET" title="" authors="" solutions="" manager="" editor="" />
<tags ms.service=""
    ms.date=""
    wacn.date="12/4/2015"
    />

# Overview of Microsoft Azure Content Delivery Network

The Microsoft Azure Content Delivery Network caches static content in storage blobs, cloud services, and websites on the Azure platform by using large numbers of physical nodes distributed across Mainland China. This provides media services with acceleration for streaming content delivery and offers developers solutions for delivering high-bandwidth content. This service also currently supports the use of source stations that have not been deployed on the Azure platform.

For more details and pricing for Content Delivery Network, see [Introduction to the Microsoft Azure Content Delivery Network service](http://www.windowsazure.cn/home/features/cdn/).

If you are an existing user of the Content Delivery Network, visit the [Microsoft Azure Content Delivery Network management portal](https://manage.windowsazure.cn) to manage network acceleration domain names. See [Using Microsoft Azure Content Delivery Network](http://www.windowsazure.cn/documentation/articles/cdn-how-to-use/) for a more specific user guide.

+ [What is a Content Delivery Network?](#step1)
+ [Advantages of Content Delivery Network](#step2)
+ [Features of Content Delivery Network](#step3)

## What is Content Delivery Network?<a id="step1"></a>

CDN stands for content delivery network. Virtually all large-scale websites use the Content Delivery Network technology today, but the technology is by no means exclusive to large websites. The basic purpose of the network is to avoid bottlenecks and other parts of the Internet that could affect data transfer rates and stability, to make content transfers faster and more stable. By placing node servers in different places across the network and building a more intelligent layer of virtual networks by using the Internet as a foundation, Content Delivery Network systems can redirect user requests in real time to the service node closest to the user based on the status of network traffic and node connections and loads, as well as overall information on distance to the user and response times.
 
Taking the Microsoft website as an example, Microsoft may be an American company, but its customers are distributed across the globe. This means that there are users in every part of the world who need to access the Microsoft website or download product updates from Microsoft Update. If the website servers were deployed only in a single location in the US, users in the areas around this location could undoubtedly achieve satisfactory speeds when accessing the website, as the distances involved would be small and network delays would also be minimal. However, a user in China who is downloading product updates from a server in this US location would require that all data packets were transferred back and forth between China and the US. As the total length of the route extends to thousands of kilometers, this would cause enormous delays.

However, this problem can be solved by placing Content Delivery Network nodes in China. The nodes automatically cache data to data centers in the major cities throughout China, shortening the distance between users and content and thereby reducing the time required to transfer data. Using Content Delivery Network caching means that users can obtain content from a nearby location, which resolves the issue of Internet network congestion and increases the response speed for users who are accessing websites and apps.


![][4]


## Advantages<a id="step2"></a>

### Built-in support for many types of Microsoft Azure services

Native support for a number of different Microsoft Azure services, including storage blobs, cloud services, websites, and media services, is offered by default, providing the user with comprehensive, one-stop cloud service support.

![][1]


### Full self-service model

Traditional Content Delivery Network services require a large amount of complex and tedious configuration processes. However, users can accomplish every imaginable task themselves by using the Azure portal and the dedicated Content Delivery Network portal. Users can create network acceleration nodes to the subsequent management of the entire node life cycle, check a wide range of statistical reports, download raw access logs, and configure various advanced functions (such as cache rule configuration, forced refreshing of cached content, content preloading, and antitheft chains).

![][2]

![][3]

### Dynamic optimization of all network nodes

The Content Delivery Network service integrates mainstream network services from a number of China-based companies to provide comprehensive static webpage acceleration and acceleration for a range of service types, including download delivery for large files such as software installation packages, game clients, apps and videos, and video on demand (VoD) and streaming (direct-broadcast) targeted primarily at online video websites and online educational websites, thereby meeting the delivery needs of different types of resource. It also provides full network coverage that spans the entire region for mainstream telecoms carriers, including China Telecom, China Unicom, and China Mobile, as well as other ISPs, and allocates user requests to the optimal node by using load-balancing technology and intelligent dispatch strategies based on the real-time network status.


### Reduces costs

Content Delivery Network leverages the advantages of cooperation between mainstream network services from several companies to provide all Azure users, including business clients and website payment users, with high-quality, low-cost services. This allows even more users to enjoy the benefits that Content Delivery Network services bring.

## Acceleration for multiple scenarios

The Content Delivery Network service supports all different acceleration scenarios described below, which creates a comprehensive and multidimensional acceleration service for users.

![][8]

### Website and small file acceleration

One classic usage scenario for Content Delivery Network is providing acceleration for the so-called “small files” (e.g., HTML webpage files, image files, JavaScript files, or CSS files) used by many websites. This allows the website to deliver a better user experience and thereby increase user visits and ultimately drive up revenues for the entire business. The typical user group would be small, medium, and large enterprises that provide website services for Internet users.

### Download delivery for large files

Another typical usage scenario for Content Delivery Network is to facilitate multinode delivery of large file downloads, which ultimately ensures that the download experience proceeds smoothly. Without the use of Content Delivery Network services, typical user scenarios such as operating system and firmware upgrades, publishing new games online (which require downloading client installation packages), and mobile app updates, would have a huge impact on source station bandwidth usage and could even cause the source station to stop working.

### Streaming media acceleration

As the range of online video and media services has grown over the last few years, increasing numbers of people have become used to using Internet platforms to watch videos and listen to audio content. The limitations on the Internet environment in China places huge demands on the final delivery of audio and video content. The typical user group is all types of media website and mobile app clients that provide services to Internet users.

### HTTPS secure acceleration

Security will always be the issue that users are most concerned about. Content Delivery Network not only provides comprehensive acceleration for HTTP access, but also offers a dedicated HTTPS acceleration service for users who need access via the HTTPS access protocol. In terms of usage scenarios, this service could be categorized as a small file acceleration service, but it also provides certain optimization services that use dynamic routing access.


## Functions<a id="step3"></a>

### Full self-service creation and management of Content Delivery Network acceleration nodes

Content Delivery Network provides extensive self-service management and configuration services for the entire lifecycle of network acceleration nodes, including functions such as creating, deleting, enabling, and banning network acceleration nodes, as well as editing source stations.

![][5]

### Visualized queries for traffic and bandwidth information

The dedicated Content Delivery Network portal allows easy, quick, and clear checking of traffic and bandwidth usage details for network acceleration domain names.

![][6]

![][7]


### Cache rule configuration

The system already provides default cache rules for various types of Content Delivery Network acceleration. Users can also customize and edit rules according to their actual requirements, to achieve the goal of flexible control over content cache times.

![][9]

### Antitheft chain

Content Delivery Network provides content access control features to address the specific needs of users in China, including an antitheft chain. Users can use these features to take better and more effective control over their accelerated content, to achieve the goal of keeping content protected.

![][10]


### Cache refreshing

Sometimes when users finish updating a particular file on the source station, they want to see the results of the update reflected on the network service nodes in real time. However, as the network has default or user-defined cache rules, the updated changes are not generally apparent on all network nodes in real time. It is at times like this that the “cache refresh” function can be used to force a cache refresh for individual files or batches of files. The goal is to make the network service clear the file(s) designated by the user from all nodes, so that the next time users access one of these files they will obtain the updated file.

![][11]

### Content preloading

Content preloading means caching the content of a designated URL from the source station to the network nodes, to eliminate the waiting time the first time that the user accesses the resource. Content prefetching is generally used in scenarios that involve the delivery of large files, where it can effectively improve the user access experience.

![][12]

### Log downloads

Users sometimes need to perform statistical analyses of network acceleration effectiveness or raw access information. In such situations, they can obtain such raw access information by using the “log download” function. The user must provide an accessible Azure storage account to use this feature, as the Content Delivery Network will save the log access files for the corresponding customer(s) on this account.

![][13]

### Service checks

Once you have created a Content Delivery Network service endpoint, you can use the "Service Check" view to see whether it is possible to access the source station, whether network deployment is complete, and whether network caching is working normally.

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
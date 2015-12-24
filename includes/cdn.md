# Use Microsoft Azure Content Delivery Network

Microsoft Azure Content Delivery Network caches static content in storage blobs, cloud services, and websites on the Azure platform by using large numbers of physical nodes that are distributed across mainland China to provide developers with a solution for delivering high-bandwidth content. This network also currently supports the use of source stations that have not been deployed on the Azure platform.

This task includes the steps listed below:

+ [Step 1: Create a storage account, cloud service, website, or media service](#step1)
+ [Step 2: Create a new Content Delivery Network endpoint](#step2)
+ [Step 3: Access content in Content Delivery Network](#step3)
+ [Step 4: Delete content from Content Delivery Network](#step4)
+ [Step 5: Use advanced management features](#step5)

The advantages of using Content Delivery Network to cache Azure data include:

- Better performance and user experience for end users of apps with distant content sources that require the use of multiple Internet journeys to load content.
- Large-scale distribution that enables the system to cope better with transient high loads (for example, at the start of events such as product launches).

Existing Azure customers in China can now use Content Delivery Network in the [Microsoft Azure portal](https://manage.windowsazure.cn/).

## Step 1: Create a storage account, cloud service, website, or media service<a id="step1"></a>
You can create Content Delivery Network endpoints for storage accounts, cloud services, websites, or media services in existing Azure subscriptions. You can also create new storage accounts, cloud services, or websites for use in Azure subscriptions by using the following method:

### Create a storage account for Azure subscriptions
Refer to [How to create storage accounts](http://www.windowsazure.cn/zh-cn/documentation/articles/storage-create-storage-account/)

### Create a cloud service for Azure subscriptions
Refer to [How to create and deploy cloud services](http://www.windowsazure.cn/zh-cn/documentation/articles/cloud-services-how-to-create-deploy/)

### Create a website for Azure subscriptions
Refer to [How to create and deploy websites](http://www.windowsazure.cn/zh-cn/documentation/articles/web-sites-create-deploy/)

### Create a media service for Microsoft Azure subscriptions
Refer to [How to create and deploy media services](http://www.windowsazure.cn/documentation/articles/media-services-create-account/)

## Step 2: Create a new Content Delivery Network endpoint<a id="step2"></a>
Once a storage account is enabled, all publicly available objects are entitled to access the network edge high-speed caching for access to cloud services or websites. If you edit an object that is currently cached in the network, the new content will be accessible only via the network after the time to live (TTL) expires and the object’s content is updated (or after a manual refresh is performed by using the advanced management features).

### Create a new Content Delivery Network endpoint
1. In the navigation pane of the [Microsoft Azure portal](https://manage.windowsazure.cn/), click Content Delivery Network.
2. In the Function area, click Create New. In the Create New dialog box, select App Services, CDN, and Quick Create in that order.

    ![CDN Quick Create][1]
3. Select all Azure subscriptions you wish to use from the Subscriptions drop-down list (if there are multiple subscriptions).
4. Select the acceleration type from the Acceleration Type drop-down list. The types of acceleration currently supported are Web Acceleration, Download Acceleration, HTTP VoD (Video on Demand) Acceleration, and Live Streaming (Video Direct Broadcast) Acceleration.
5. In the Origin Domain Type drop-down list, select Cloud Service, Storage Account, Web App, Media Service, or a customized origin domain.
6. In the Origin Domain drop-down list, select the endpoint that was used to create the network from the cloud service, storage account, web app, or media service list. If the selected Origin Domain Type is Customized Origin Domain, input your own origin domain address under Origin Domain.
7. In Custom Domain, enter the customized domain name you wish to use, e.g., cdn.<yourcompany>.com.
8. In Origin Host Header, enter the return-to-source access host header that your source station accepted. Once you have entered the custom domain, the system will automatically fill in a default value based on the origin domain type that you selected. To be more specific, if your source station is on Azure, the default value will be the corresponding source station address. If your source station is not on Azure, the default value will be the custom domain that you entered. Of course, you can also modify this based on the actual configuration of your source station.
9. In ICP Number, enter the corresponding **ICP record number** for the custom domain that you entered (e.g., Jing ICP Bei XXXXXXXX Hao-X).
10. Click Create to create the new endpoint.
11. Once the endpoint has been created, it will appear in the list of subscribed endpoints. The list view shows the custom domains that were used to access cached content, as well as the origin domains.

The origin domain is the original location of the content cached on Content Delivery Network. Custom domains are URLs that are used to access cache content.
> **Note** that configurations created for endpoints cannot be used immediately:

> 1. The custom domain name and ICP number that you entered must first be reviewed to ensure that they match and are valid. This process can take up to **one business day** to complete.
2. If the details do not pass the ICP review, you must delete the Content Delivery Network endpoint you created and create a new endpoint by using the correct custom domain name and ICP number.
3. If the details pass the ICP review, the service will be registered within **60 minutes** so that it can be propagated by the network. At the same time, you also need to configure the CNAME mapping details, as indicated by the notifications in the interface, before the cache content can finally be accessed via the custom domain name.

## Step 3: Access content in Content Delivery Network<a id="step3"></a>
If you want to access content cached on the network, do so by using the custom domain name you provided in Step 2. The addresses of cached blobs are similar to the following address (using the example from Step 2):

`http://cdn.yourcompany.com/<myPublicContainer>/<BlobName>`

## Step 4: Delete content from the Content Delivery Network<a id="step4"></a>
If you don’t want to continue to cache objects on Content Delivery Network, you can use any one of the following procedures:

- For Azure blobs, delete the blob from the public container.
- Generate a private container to replace the public container. For more information on this, refer to [Restricting access to containers and blobs](http://msdn.microsoft.com/zh-cn/library/dd179354.aspx).
- You can use the Azure portal to ban or delete Content Delivery Network endpoints.
- You can change the cloud service to a request that no longer responds to this object.

Objects already cached in Content Delivery Network will remain in a cached state until the TTL for the object expires. Once the TTL expires, the network will check whether the endpoint is still valid and whether anonymous access to the object is still possible. If the object cannot be accessed, it will no longer be cached.


## Step 5: Use advanced management features<a id="step5"></a>
Once you have created a new Content Delivery Network endpoint, you can use the Azure portal to check the basic configuration details and perform other basic operations, such as banning/enabling and deleting network endpoints. You can also click the Management button to jump to another management page, where you can use the advanced management functions:

![Manage Button][2]
> **Note: You will be taken to another Content Delivery Network management page that is not part of the Azure portal. (Ensure that you allow your browser to open the new window)**

![Adv Portal][3]

This advanced management interface provides features including overview, domain name management, traffic report, bandwidth report, cache refresh, content prefetch, and log download. For specific methods of using and configuring the interface, click to enter the corresponding function modules, and then read the corresponding help files. You can also open the help files directly via the left navigation bar.




[步骤 1:创建存储帐户，云服务,网站或媒体服务]: https://github.com/mccdn/cdndoc/blob/master/wacn/azurecdn.md#步骤-1创建存储帐户云服务网站或媒体服务
[步骤 2:创建新的 CDN 终结点]: #%E6%AD%A5%E9%AA%A4-2%E5%88%9B%E5%BB%BA%E6%96%B0%E7%9A%84-cdn-%E7%BB%88%E7%BB%93%E7%82%B9
[步骤 3:访问 CDN 内容]: #%E6%AD%A5%E9%AA%A4-3%E8%AE%BF%E9%97%AE-cdn-%E5%86%85%E5%AE%B9
[步骤 4:删除 CDN 中的内容]: #%E6%AD%A5%E9%AA%A4-4%E5%88%A0%E9%99%A4-cdn-%E4%B8%AD%E7%9A%84%E5%86%85%E5%AE%B9
[步骤 5:使用高级管理功能]: #%E6%AD%A5%E9%AA%A4-5%E4%BD%BF%E7%94%A8%E9%AB%98%E7%BA%A7%E7%AE%A1%E7%90%86%E5%8A%9F%E8%83%BD


<!--Image references-->
[1]: ./media/cdn/image005.png
[2]: ./media/cdn/image002.png
[3]: ./media/cdn/how_to_001.png

<!---HONumber=CDN_1201_2015-->
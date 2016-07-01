## 创建 Azure 存储帐户

若要使用 Azure 存储空间，您将需要一个存储帐户。可通过以下步骤创建存储帐户。（您还可以通过使用 Azure 服务管理客户端库或服务管理 [REST API] 来创建存储帐户。）

1.  登录到 [Azure 管理门户]。

2.  在导航窗格的底部，单击"新建"。

	![+new][plus-new]

3.  依次单击"数据服务"、"存储"和"快速创建"。

	![Quick create dialog][quick-create-storage]

4.  在 URL 中，键入要在存储帐户的 URI 中使用的子域名称。该条目可能包含 3 到 24 个小写字母和数字。此值将成为用于对订阅的 Blob、队列或表资源进行寻址的 URI 中的主机名。

5.  选择要在其中查找存储的区域/地缘组。如果将从您的 Azure 应用程序使用存储，请选择要在其中部署您的应用程序的同一区域。

6. 或者，可以选择您的帐户所需的复制的类型。地域冗余复制是默认设置。有关复制选项的详细信息，请参阅 [Azure 存储冗余选项](/documentation/articles/storage-redundancy)和 [Azure 存储团队博客](http://blogs.msdn.com/b/windowsazurestorage)。

6.  单击"创建存储帐户"。

[REST API]: http://msdn.microsoft.com/zh-cn/library/azure/hh264518.aspx
[Azure 管理门户]: http://manage.windowsazure.cn
[plus-new]: ./media/storage-create-account-include/plus-new.png
[quick-create-storage]: ./media/storage-create-account-include/quick-storage-2.png

<!--HONumber=50-->
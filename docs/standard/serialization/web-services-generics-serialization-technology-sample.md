---
title: "Web 服务泛型序列化技术示例"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cdc15ea4-f678-4729-8ebe-188ae720bef7
caps.latest.revision: 7
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 0b5dfc6be702b37eafeac2ae0d944dabe074d209
ms.contentlocale: zh-cn
ms.lasthandoff: 08/21/2017

---
# <a name="web-services-generics-serialization-technology-sample"></a><span data-ttu-id="5bb01-102">Web 服务泛型序列化技术示例</span><span class="sxs-lookup"><span data-stu-id="5bb01-102">Web Services Generics Serialization Technology Sample</span></span>
[<span data-ttu-id="5bb01-103">下载示例</span><span class="sxs-lookup"><span data-stu-id="5bb01-103">Download Sample</span></span>](http://download.microsoft.com/download/4/7/B/47B2164C-E780-4B10-8DE4-2CB5B886E0A6/Technologies/Serialization/Xml%20Serialization/GenericsSerialization.zip.exe)  
  
 <span data-ttu-id="5bb01-104">此示例演示如何在 ASP.NET Web 服务中使用和控制泛型的序列化。</span><span class="sxs-lookup"><span data-stu-id="5bb01-104">This sample shows how to use and control the serialization of generics in ASP.NET Web Services.</span></span>  
  
### <a name="to-build-the-sample-using-visual-studio"></a><span data-ttu-id="5bb01-105">使用 Visual Studio 生成示例</span><span class="sxs-lookup"><span data-stu-id="5bb01-105">To build the sample using Visual Studio</span></span>  
  
1.  <span data-ttu-id="5bb01-106">打开 Visual Studio，然后从“文件”菜单中选择“新建网站”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-106">Open Visual Studio and select **New Web Site** from the **File** menu.</span></span>  
  
2.  <span data-ttu-id="5bb01-107">在“新建网站”对话框的左侧窗格中选择所需的编程语言，然后从右侧窗格中选择“ASP.NET Web 服务”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-107">In the **New Web Site** dialog, select from the left pane your desired programming language, then from the right pane, select **ASP.NET Web Service**.</span></span>  
  
3.  <span data-ttu-id="5bb01-108">单击“浏览”，然后导航至 \CS\GenericsService 子目录。</span><span class="sxs-lookup"><span data-stu-id="5bb01-108">Click **Browse** and navigate to the \CS\GenericsService subdirectory.</span></span>  
  
4.  <span data-ttu-id="5bb01-109">选择 Service.asmx 以在 Visual Studio 中打开该文件。</span><span class="sxs-lookup"><span data-stu-id="5bb01-109">Select Service.asmx to open the file in Visual Studio.</span></span>  
  
5.  <span data-ttu-id="5bb01-110">在 **“生成”** 菜单上，单击 **“生成解决方案”**。</span><span class="sxs-lookup"><span data-stu-id="5bb01-110">On the **Build** menu, click **Build Solution**.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bb01-111">此列表中的前五个步骤是可选的。</span><span class="sxs-lookup"><span data-stu-id="5bb01-111">The first five steps in this list are optional.</span></span> <span data-ttu-id="5bb01-112">.NET Framework 运行时将在首次请求该 Web 服务时自动生成该服务。</span><span class="sxs-lookup"><span data-stu-id="5bb01-112">The .NET Framework runtime will automatically generate the Web service the first time the service is requested.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5bb01-113">必须执行以下步骤，才能生成示例。</span><span class="sxs-lookup"><span data-stu-id="5bb01-113">The following steps are required to build the sample.</span></span>  
  
1.  <span data-ttu-id="5bb01-114">打开[!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)]并导航到 \CS 子目录。</span><span class="sxs-lookup"><span data-stu-id="5bb01-114">Open [!INCLUDE[fileExplorer](../../../includes/fileexplorer-md.md)] and navigate to the \CS subdirectory.</span></span>  
  
2.  <span data-ttu-id="5bb01-115">右键单击 GenericsService 子目录的图标，然后选择“共享和安全”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-115">Right-click the icon for the GenericsService subdirectory, and select **Sharing and Security**.</span></span>  
  
3.  <span data-ttu-id="5bb01-116">在“Web 共享”选项卡中，选择“共享此文件夹”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-116">In the **Web Sharing** tab, select **Share this Folder**.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bb01-117">请记下“别名”窗格中列出的虚拟目录名，因为需要用它来运行示例。</span><span class="sxs-lookup"><span data-stu-id="5bb01-117">Take note of the virtual directory name that is listed in the **Aliases** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-build-the-sample-using-internet-information-services"></a><span data-ttu-id="5bb01-118">使用 Internet 信息服务生成示例</span><span class="sxs-lookup"><span data-stu-id="5bb01-118">To build the sample using Internet Information Services</span></span>  
  
1.  <span data-ttu-id="5bb01-119">打开“Internet Information Services”管理单元，然后展开“网站”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-119">Open the **Internet Information Services** management snap-in and expand **Web Sites**.</span></span>  
  
2.  <span data-ttu-id="5bb01-120">左键单击“默认网站”，选择“新建”，然后选择“虚拟目录?”来创建“虚拟目录创建向导”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-120">Left-click **Default Web Site**, select **New**, and then select **Virtual Directory?** to create the **Virtual Directory Creation Wizard**.</span></span>  
  
3.  <span data-ttu-id="5bb01-121">单击“下一步”，输入虚拟目录的公共别名，然后再单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-121">Click **Next**, enter the public alias for your virtual directory, and click **Next**.</span></span>  
  
4.  <span data-ttu-id="5bb01-122">输入保存示例的目录路径（通常是 \CS\GenericsService 子目录），然后单击“下一步”。</span><span class="sxs-lookup"><span data-stu-id="5bb01-122">Enter the path to the directory where you saved the sample (normally the \CS\GenericsService subdirectory) and click **Next**.</span></span> <span data-ttu-id="5bb01-123">单击“下一步”完成向导。</span><span class="sxs-lookup"><span data-stu-id="5bb01-123">Click **Next** to finish the wizard.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="5bb01-124">请记下“别名”窗格中列出的虚拟目录名，因为需要用它来运行示例。</span><span class="sxs-lookup"><span data-stu-id="5bb01-124">Take note of the virtual directory name that is listed in the **Alias** pane, because you will need it to run the sample.</span></span>  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="5bb01-125">运行示例</span><span class="sxs-lookup"><span data-stu-id="5bb01-125">To run the sample</span></span>  
  
1.  <span data-ttu-id="5bb01-126">打开浏览器窗口，选择其地址栏。</span><span class="sxs-lookup"><span data-stu-id="5bb01-126">Open a browser window and select its address bar.</span></span>  
  
2.  <span data-ttu-id="5bb01-127">键入“http://localhost/[virtual directory]/Service.asmx”，其中“[virtual directory]”表示生成该示例时创建的虚拟目录。</span><span class="sxs-lookup"><span data-stu-id="5bb01-127">Type **http://localhost/[virtual directory]/Service.asmx**, where [virtual directory] represents the virtual directory you created when you built the sample.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5bb01-128">备注</span><span class="sxs-lookup"><span data-stu-id="5bb01-128">Remarks</span></span>  
 <span data-ttu-id="5bb01-129">该示例将显示默认的 ASP.NET 页面，该页面包含指向 Web 服务定义的链接。</span><span class="sxs-lookup"><span data-stu-id="5bb01-129">The sample displays a default ASP.NET page that contains links to the definition of the Web Service.</span></span> <span data-ttu-id="5bb01-130">除了修改 Web 服务的源代码以外，还可以自定义其显示方式。</span><span class="sxs-lookup"><span data-stu-id="5bb01-130">You can customize the display in addition to modifying the source code for the Web service.</span></span> <span data-ttu-id="5bb01-131">有关详细信息，请参阅[生成 XML Web services 客户端](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c)。</span><span class="sxs-lookup"><span data-stu-id="5bb01-131">For more information, see [Building XML Web Service Clients](http://msdn.microsoft.com/en-us/c606f3cb-4111-45b4-ae42-9300420fa16c).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5bb01-132">另请参阅</span><span class="sxs-lookup"><span data-stu-id="5bb01-132">See Also</span></span>  
 <span data-ttu-id="5bb01-133"><xref:System.Collections.Generic></span><span class="sxs-lookup"><span data-stu-id="5bb01-133"><xref:System.Collections.Generic></span></span>   
 <span data-ttu-id="5bb01-134"><xref:System.Web.Services></span><span class="sxs-lookup"><span data-stu-id="5bb01-134"><xref:System.Web.Services></span></span>   
 <span data-ttu-id="5bb01-135"><xref:System.Xml.Serialization></span><span class="sxs-lookup"><span data-stu-id="5bb01-135"><xref:System.Xml.Serialization></span></span>   
 <span data-ttu-id="5bb01-136">[序列化](../../../docs/standard/serialization/index.md) </span><span class="sxs-lookup"><span data-stu-id="5bb01-136">[Serialization](../../../docs/standard/serialization/index.md) </span></span>  
 [<span data-ttu-id="5bb01-137">使用 ASP.NET 创建的 XML Web service 以及 XML Web Service 客户端</span><span class="sxs-lookup"><span data-stu-id="5bb01-137">XML Web Services Created Using ASP.NET and XML Web Service Clients</span></span>](http://msdn.microsoft.com/en-us/1e64af78-d705-4384-b08d-591a45f4379c)

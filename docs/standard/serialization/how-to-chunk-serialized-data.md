---
title: "如何：对序列化数据进行分块"
ms.date: 03/30/2017
ms.prod: .net
ms.topic: article
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- chunking serialized data
- data chunking
- binary serialization, chunking data
- large data set chunking
- serialization, chunking data
- serialization, examples
- binary serialization, examples
ms.assetid: 22f1b818-7e0d-428a-8680-f17d6ebdd185
caps.latest.revision: 3
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 5d8c56be905d6dbfa966546c109a322e013baaac
ms.contentlocale: zh-cn
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-chunk-serialized-data"></a><span data-ttu-id="7401f-102">如何：对序列化数据进行分块</span><span class="sxs-lookup"><span data-stu-id="7401f-102">How to: chunk serialized data</span></span>

[!INCLUDE [binary-serialization-warning](../../../includes/binary-serialization-warning.md)]

<span data-ttu-id="7401f-103">在 Web 服务消息中发送大型数据集时，会出现下面两个问题：</span><span class="sxs-lookup"><span data-stu-id="7401f-103">Two issues that occur when sending large data sets in Web service messages are:</span></span>  
  
1.  <span data-ttu-id="7401f-104">因序列化引擎执行缓冲而使工作集（内存）很大。</span><span class="sxs-lookup"><span data-stu-id="7401f-104">A large working set (memory) due to buffering by the serialization engine.</span></span>  
  
2.  <span data-ttu-id="7401f-105">因使用 Base64 编码后产生 33% 的膨胀而过度占用带宽。</span><span class="sxs-lookup"><span data-stu-id="7401f-105">Inordinate bandwidth consumption due to 33 percent inflation after Base64 encoding.</span></span>  
  
 <span data-ttu-id="7401f-106">若要解决这两个问题，可以通过实现 <xref:System.Xml.Serialization.IXmlSerializable> 接口，来控制序列化和反序列化。</span><span class="sxs-lookup"><span data-stu-id="7401f-106">To solve these problems, implement the <xref:System.Xml.Serialization.IXmlSerializable> interface to control the serialization and deserialization.</span></span> <span data-ttu-id="7401f-107">具体来讲，就是实现 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 和 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法，对数据进行分块。</span><span class="sxs-lookup"><span data-stu-id="7401f-107">Specifically, implement the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> and <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> methods to chunk the data.</span></span>  
  
### <a name="to-implement-server-side-chunking"></a><span data-ttu-id="7401f-108">实现服务器端数据分块</span><span class="sxs-lookup"><span data-stu-id="7401f-108">To implement server-side chunking</span></span>  
  
1.  <span data-ttu-id="7401f-109">在服务器计算机上，必须采用 Web 方法禁用 ASP.NET 缓冲，并返回实现 <xref:System.Xml.Serialization.IXmlSerializable> 的类型。</span><span class="sxs-lookup"><span data-stu-id="7401f-109">On the server machine, the Web method must turn off ASP.NET buffering and return a type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span>  
  
2.  <span data-ttu-id="7401f-110">实现 <xref:System.Xml.Serialization.IXmlSerializable> 的类型可以采用 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法对数据进行分块。</span><span class="sxs-lookup"><span data-stu-id="7401f-110">The type that implements <xref:System.Xml.Serialization.IXmlSerializable> chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
### <a name="to-implement-client-side-processing"></a><span data-ttu-id="7401f-111">实现客户端处理</span><span class="sxs-lookup"><span data-stu-id="7401f-111">To implement client-side processing</span></span>  
  
1.  <span data-ttu-id="7401f-112">通过更改客户端代理上的 Web 方法，可以返回实现 <xref:System.Xml.Serialization.IXmlSerializable> 的类型。</span><span class="sxs-lookup"><span data-stu-id="7401f-112">Alter the Web method on the client proxy to return the type that implements <xref:System.Xml.Serialization.IXmlSerializable>.</span></span> <span data-ttu-id="7401f-113">可以使用 <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> 自动执行这项操作，但此处不加以说明。</span><span class="sxs-lookup"><span data-stu-id="7401f-113">You can use a <xref:System.Xml.Serialization.Advanced.SchemaImporterExtension> to do this automatically, but this isn't shown here.</span></span>  
  
2.  <span data-ttu-id="7401f-114">通过实现 <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> 方法，可以读取分块数据流，并将字节写入磁盘。</span><span class="sxs-lookup"><span data-stu-id="7401f-114">Implement the <xref:System.Xml.Serialization.IXmlSerializable.ReadXml%2A> method to read the chunked data stream and write the bytes to disk.</span></span> <span data-ttu-id="7401f-115">此实现还会引发可供图形控件（如进度栏）使用的进度事件。</span><span class="sxs-lookup"><span data-stu-id="7401f-115">This implementation also raises progress events that can be used by a graphic control, such as a progress bar.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7401f-116">示例</span><span class="sxs-lookup"><span data-stu-id="7401f-116">Example</span></span>  
<span data-ttu-id="7401f-117">下面的代码示例演示客户端上用于禁用 ASP.NET 缓冲的 Web 方法。</span><span class="sxs-lookup"><span data-stu-id="7401f-117">The following code example shows the Web method on the client that turns off ASP.NET buffering.</span></span> <span data-ttu-id="7401f-118">它还演示了如何在客户端实现 <xref:System.Xml.Serialization.IXmlSerializable> 接口，该实现可以采用 <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> 方法对数据进行分块。</span><span class="sxs-lookup"><span data-stu-id="7401f-118">It also shows the client-side implementation of the <xref:System.Xml.Serialization.IXmlSerializable> interface that chunks the data in the <xref:System.Xml.Serialization.IXmlSerializable.WriteXml%2A> method.</span></span>  
  
<span data-ttu-id="7401f-119">[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)] [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]</span><span class="sxs-lookup"><span data-stu-id="7401f-119">[!code-csharp[HowToChunkSerializedData#1](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#1)] [!code-vb[HowToChunkSerializedData#1](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#1)]</span></span>  
<span data-ttu-id="7401f-120">[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)] [!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]</span><span class="sxs-lookup"><span data-stu-id="7401f-120">[!code-csharp[HowToChunkSerializedData#2](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#2)] [!code-vb[HowToChunkSerializedData#2](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#2)]</span></span>  
<span data-ttu-id="7401f-121">[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)] [!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]</span><span class="sxs-lookup"><span data-stu-id="7401f-121">[!code-csharp[HowToChunkSerializedData#3](../../../samples/snippets/csharp/VS_Snippets_Remoting/HowToChunkSerializedData/CS/SerializationChunk.cs#3)] [!code-vb[HowToChunkSerializedData#3](../../../samples/snippets/visualbasic/VS_Snippets_Remoting/HowToChunkSerializedData/VB/SerializationChunk.vb#3)]</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="7401f-122">编译代码</span><span class="sxs-lookup"><span data-stu-id="7401f-122">Compiling the code</span></span>  
  
-   <span data-ttu-id="7401f-123">代码使用下面的命名空间：<xref:System>、<xref:System.Runtime.Serialization>、<xref:System.Web.Services>、<xref:System.Web.Services.Protocols>、<xref:System.Xml>、<xref:System.Xml.Serialization> 和 <xref:System.Xml.Schema>。</span><span class="sxs-lookup"><span data-stu-id="7401f-123">The code uses the following namespaces: <xref:System>, <xref:System.Runtime.Serialization>, <xref:System.Web.Services>, <xref:System.Web.Services.Protocols>, <xref:System.Xml>, <xref:System.Xml.Serialization>, and <xref:System.Xml.Schema>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7401f-124">请参阅</span><span class="sxs-lookup"><span data-stu-id="7401f-124">See also</span></span>  
 [<span data-ttu-id="7401f-125">自定义序列化</span><span class="sxs-lookup"><span data-stu-id="7401f-125">Custom Serialization</span></span>](custom-serialization.md)

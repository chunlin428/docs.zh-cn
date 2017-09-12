---
title: "如何：将对象序列化为 SOAP 编码的 XML 流"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
- CSharp
- C++
- jsharp
helpviewer_keywords:
- SOAP, XML serialization
- XML serialization, SOAP
- serialization, SOAP
ms.assetid: af406e0a-fa3a-46dd-a7ba-c80731eba3a0
caps.latest.revision: 6
author: Erikre
ms.author: erikre
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 717bcb6f9f72a728d77e2847096ea558a9c50902
ms.openlocfilehash: 84bdce1e7a877425a38a980ba306d38573add227
ms.contentlocale: zh-cn
ms.lasthandoff: 08/21/2017

---
# <a name="how-to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="8fd70-102">如何：将对象序列化为 SOAP 编码的 XML 流</span><span class="sxs-lookup"><span data-stu-id="8fd70-102">How to: Serialize an Object as a SOAP-Encoded XML Stream</span></span>
  
 <span data-ttu-id="8fd70-103">由于 SOAP 消息是使用 XML 生成的，因此 <xref:System.Xml.Serialization.XmlSerializer> 类可用于序列化类和生成编码的 SOAP 消息。</span><span class="sxs-lookup"><span data-stu-id="8fd70-103">Because a SOAP message is built using XML, the <xref:System.Xml.Serialization.XmlSerializer> class can be used to serialize classes and generate encoded SOAP messages.</span></span> <span data-ttu-id="8fd70-104">生成的 XML 符合[万维网联合会文档“简单对象访问协议 (SOAP) 1.1”的第 5 节](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512)。</span><span class="sxs-lookup"><span data-stu-id="8fd70-104">The resulting XML conforms to [section 5 of the World Wide Web Consortium document "Simple Object Access Protocol (SOAP) 1.1"](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/#_Toc478383512).</span></span> <span data-ttu-id="8fd70-105">如果您要创建通过 SOAP 消息进行通信的 XML Web services，则可以将一组特殊的 SOAP 属性应用于类和类的成员来自定义 XML 流。</span><span class="sxs-lookup"><span data-stu-id="8fd70-105">When you are creating an XML Web service that communicates through SOAP messages, you can customize the XML stream by applying a set of special SOAP attributes to classes and members of classes.</span></span> <span data-ttu-id="8fd70-106">有关属性列表，请参阅[控制编码的 SOAP 序列化的特性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)。</span><span class="sxs-lookup"><span data-stu-id="8fd70-106">For a list of attributes, see [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
### <a name="to-serialize-an-object-as-a-soap-encoded-xml-stream"></a><span data-ttu-id="8fd70-107">将对象序列化为 SOAP 编码的 XML 流</span><span class="sxs-lookup"><span data-stu-id="8fd70-107">To serialize an object as a SOAP-encoded XML stream</span></span>  
  
1.  <span data-ttu-id="8fd70-108">使用 [XML 架构定义工具 (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md) 创建类。</span><span class="sxs-lookup"><span data-stu-id="8fd70-108">Create the class using the [XML Schema Definition Tool (Xsd.exe)](../../../docs/standard/serialization/xml-schema-definition-tool-xsd-exe.md).</span></span>  
  
2.  <span data-ttu-id="8fd70-109">应用在 `System.Xml.Serialization` 中找到的一个或多个特殊属性。</span><span class="sxs-lookup"><span data-stu-id="8fd70-109">Apply one or more of the special attributes found in `System.Xml.Serialization`.</span></span> <span data-ttu-id="8fd70-110">请参见“用来控制编码的 SOAP 序列化的属性”中的列表。</span><span class="sxs-lookup"><span data-stu-id="8fd70-110">See the list in "Attributes That Control Encoded SOAP Serialization."</span></span>  
  
3.  <span data-ttu-id="8fd70-111">通过创建新的 `XmlTypeMapping`，然后用已序列化类的类型调用 `SoapReflectionImporter` 方法，来创建 `ImportTypeMapping`。</span><span class="sxs-lookup"><span data-stu-id="8fd70-111">Create an `XmlTypeMapping` by creating a new `SoapReflectionImporter`, and invoking the `ImportTypeMapping` method with the type of the serialized class.</span></span>  
  
     <span data-ttu-id="8fd70-112">以下代码示例调用 `SoapReflectionImporter` 类的 `ImportTypeMapping` 方法来创建 `XmlTypeMapping`。</span><span class="sxs-lookup"><span data-stu-id="8fd70-112">The following code example calls the `ImportTypeMapping` method of the `SoapReflectionImporter` class to create an `XmlTypeMapping`.</span></span>  
  
    ```vb  
    ' Serializes a class named Group as a SOAP message.  
    Dim myTypeMapping As XmlTypeMapping =
        New SoapReflectionImporter().ImportTypeMapping(GetType(Group))  
    ```  
  
    ```csharp  
    // Serializes a class named Group as a SOAP message.  
    XmlTypeMapping myTypeMapping =
        new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
    ```  
  
4.  <span data-ttu-id="8fd70-113">通过将 `XmlSerializer` 传递给 `XmlTypeMapping` 构造函数，来创建 <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> 类的实例。</span><span class="sxs-lookup"><span data-stu-id="8fd70-113">Create an instance of the `XmlSerializer` class by passing the `XmlTypeMapping` to the <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Xml.Serialization.XmlTypeMapping%29> constructor.</span></span>  
  
    ```vb  
    Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
    ```  
  
    ```csharp  
    XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
    ```  
  
5.  <span data-ttu-id="8fd70-114">调用 `Serialize` 或 `Deserialize` 方法。</span><span class="sxs-lookup"><span data-stu-id="8fd70-114">Call the `Serialize` or `Deserialize` method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8fd70-115">示例</span><span class="sxs-lookup"><span data-stu-id="8fd70-115">Example</span></span>  
  
```vb  
' Serializes a class named Group as a SOAP message.  
Dim myTypeMapping As XmlTypeMapping =
    New SoapReflectionImporter().ImportTypeMapping(GetType(Group))
Dim mySerializer As XmlSerializer = New XmlSerializer(myTypeMapping)  
```  
  
```csharp  
// Serializes a class named Group as a SOAP message.  
XmlTypeMapping myTypeMapping =
    new SoapReflectionImporter().ImportTypeMapping(typeof(Group));
XmlSerializer mySerializer = new XmlSerializer(myTypeMapping);  
```  
  
## <a name="see-also"></a><span data-ttu-id="8fd70-116">另请参阅</span><span class="sxs-lookup"><span data-stu-id="8fd70-116">See Also</span></span>  
 <span data-ttu-id="8fd70-117">[XML 和 SOAP 序列化](../../../docs/standard/serialization/xml-and-soap-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="8fd70-117">[XML and SOAP Serialization](../../../docs/standard/serialization/xml-and-soap-serialization.md) </span></span>  
 <span data-ttu-id="8fd70-118">[控制编码的 SOAP 序列化的特性](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) </span><span class="sxs-lookup"><span data-stu-id="8fd70-118">[Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md) </span></span>  
 <span data-ttu-id="8fd70-119">[使用 XML Web 服务进行 XML 序列化](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md) </span><span class="sxs-lookup"><span data-stu-id="8fd70-119">[XML Serialization with XML Web Services](../../../docs/standard/serialization/xml-serialization-with-xml-web-services.md) </span></span>  
 <span data-ttu-id="8fd70-120">[如何：序列化对象](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="8fd70-120">[How to: Serialize an Object](../../../docs/standard/serialization/how-to-serialize-an-object.md) </span></span>  
 <span data-ttu-id="8fd70-121">[如何：反序列化对象](../../../docs/standard/serialization/how-to-deserialize-an-object.md) </span><span class="sxs-lookup"><span data-stu-id="8fd70-121">[How to: Deserialize an Object](../../../docs/standard/serialization/how-to-deserialize-an-object.md) </span></span>  
 [<span data-ttu-id="8fd70-122">如何：重写编码的 SOAP XML 序列化</span><span class="sxs-lookup"><span data-stu-id="8fd70-122">How to: Override Encoded SOAP XML Serialization</span></span>](../../../docs/standard/serialization/how-to-override-encoded-soap-xml-serialization.md)

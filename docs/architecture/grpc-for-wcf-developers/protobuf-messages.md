---
title: Protobuf 消息-WCF 开发人员 gRPC
description: 了解 Protobuf 消息是如何在 IDL 中定义并在中C#生成的。
ms.date: 09/09/2019
ms.openlocfilehash: c7375bafb7572b0eaa0458b0310a0114e3fd078c
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: zh-CN
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543035"
---
# <a name="protobuf-messages"></a>Protobuf 消息

本部分介绍如何在 `.proto` 文件中声明协议缓冲区（Protobuf）消息。 它介绍了字段编号和类型的基本概念，并查看了 `protoc` 编译器C#生成的代码。 

本章的其余部分将更详细地介绍如何在 Protobuf 中表示不同类型的数据。

## <a name="declaring-a-message"></a>声明消息

在 Windows Communication Foundation （WCF）中，可按以下示例所示定义股票市场贸易应用程序的 `Stock` 类：

```csharp
namespace TraderSys
{
    [DataContract]
    public class Stock
    {
        [DataMember]
        public int Id { get; set;}
        [DataMember]
        public string Symbol { get; set;}
        [DataMember]
        public string DisplayName { get; set;}
        [DataMember]
        public int MarketId { get; set; }
    }
}
```

若要在 Protobuf 中实现等效类，必须在 `.proto` 文件中对其进行声明。 然后，`protoc` 编译器将生成 .NET 类作为生成过程的一部分。

```protobuf
syntax "proto3";

option csharp_namespace = "TraderSys";

message Stock {

    int32 id = 1;
    string symbol = 2;
    string display_name = 3;
    int32 market_id = 4;

}  
```

第一行声明所使用的语法版本。 语言版本3在2016中发布。 这是我们建议用于 gRPC 服务的版本。

`option csharp_namespace` 行指定要用于生成C#的类型的命名空间。 为其他语言编译 `.proto` 文件时，将忽略此选项。 Protobuf 文件通常包含多种语言的特定于语言的选项。

`Stock` 消息定义指定了四个字段。 每个都有类型、名称和字段编号。

## <a name="field-numbers"></a>字段编号

字段编号是 Protobuf 的重要组成部分。 它们用于标识二进制编码数据中的字段，这意味着它们不能从版本更改为服务版本。 优点在于可以实现向后兼容性和向前兼容性。 只要处理丢失值的可能性，客户端和服务就会忽略他们不知道的字段编号。

在二进制格式中，字段号与类型标识符组合在一起。 1到15之间的字段编号可以使用其类型编码为单字节。 从16到2047的数字需要2个字节。 如果出于任何原因需要将超过2047个字段，则可以更高。 字段号1到15的单字节标识符提供更好的性能，因此，你应将其用于最基本的常用字段。

## <a name="types"></a>类型

类型声明使用 Protobuf 的本机标量数据类型，[下一部分](protobuf-data-types.md)将对此进行更详细的讨论。 本章的其余部分将介绍 Protobuf 的内置类型，并说明它们如何与常见的 .NET 类型相关。

> [!NOTE]
> Protobuf 不能以本机方式支持 `decimal` 类型，因此改为使用 `double`。 对于需要完全小数精度的应用程序，请参阅本章下一部分中[有关小数部分的部分](protobuf-data-types.md#decimals)。

## <a name="the-generated-code"></a>生成的代码

构建应用程序时，Protobuf 会为每个消息创建类，并将其本机类型映射C#到类型。 生成的 `Stock` 类型将具有以下签名：

```csharp
public class Stock
{
    public int Id { get; set; }
    public string Symbol { get; set; }
    public string DisplayName { get; set; }
    public int MarketId { get; set; }
}
```

生成的实际代码比此要复杂得多。 原因在于，每个类都包含序列化并将自身反序列化为二进制线路格式所需的所有代码。

### <a name="property-names"></a>属性名称

请注意，Protobuf 编译器 `PascalCase` 应用于属性名称，不过它们 `snake_case` 在 `.proto` 文件中。 [Protobuf 样式指南](https://developers.google.com/protocol-buffers/docs/style)建议在消息定义中使用 `snake_case`，以便其他平台的代码生成会生成其约定的预期事例。

>[!div class="step-by-step"]
>[上一页](protocol-buffers.md)
>[下一页](protobuf-data-types.md)

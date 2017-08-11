---
title: "配信拡張機能ライブラリを作成する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- delivery extensions [Reporting Services], namespace assignments
- library [Reporting Services]
- assigning namespaces to extensions
ms.assetid: 63b32f93-4bab-4b07-bd72-39a47aca1cda
caps.latest.revision: 36
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: a6aab5e722e732096e9e4ffdf458ac25088e09ae
ms.openlocfilehash: bcfb5b69df148108531e9e5b843f127af0e3fbb4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="creating-a-delivery-extension-library"></a>配信拡張機能ライブラリの作成
  作成する [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能は、それぞれ一意の名前空間に割り当てられ、ライブラリまたはアセンブリ ファイルに組み込まれている必要があります。 名前空間の正確な名前はあまり重要ではありませんが、名前は他の拡張機能とは共有しない一意のものである必要があります。 会社の配信拡張機能には、独自に一意の名前空間を作成してください。  
  
 次の例は、[!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能を開始するためのコードを示しています。配信インターフェイスとユーティリティ クラスを含む名前空間を使用しています。  
  
```vb  
Imports System  
Imports Microsoft.ReportingServices.Interfaces  
  
Namespace CompanyName.ExtensionName  
   ...  
```  
  
```csharp  
using System;  
using Microsoft.ReportingServices.Interfaces;  
  
namespace CompanyName.ExtensionName  
{  
   ...  
```  
  
 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] 配信拡張機能をコンパイルする場合は、コンパイラに対して Microsoft.ReportingServices.Interfaces.dll への参照を指定する必要があります。配信拡張機能のインターフェイスとクラスがそこに格納されているためです。 <xref:Microsoft.ReportingServices.Interfaces> 名前空間は、<xref:Microsoft.ReportingServices.Interfaces.IExtension> インターフェイス、<xref:Microsoft.ReportingServices.Interfaces.IDeliveryExtension> インターフェイスなどを実装するために必要です。 たとえば、すべてを実装するコードを含むファイル、 [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] c# で記述された配信拡張機能が 1 つのディレクトリ、拡張子が .cs で、CompanyName.ExtensionName.dll に格納されたファイルをコンパイルするには、そのディレクトリから次のコマンドが発行されます。  
  
```csharp  
csc /t:library /out:CompanyName.ExtensionName.dll *.cs /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
 次のコード例を使用するコマンドを示しています。 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]拡張子の付いたファイルです。 vb です。  
  
```vb  
vbc /t:library /out:CompanyName.ExtensionName.dll *.vb /r:System.dll   
/r:Microsoft.ReportingServices.Interfaces.dll  
```  
  
> [!NOTE]  
>  [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] を使用して、配信拡張機能を設計、開発、および構築することもできます。 [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] でのアセンブリ開発の詳細については、[!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] ドキュメントを参照してください。  
  
## <a name="see-also"></a>参照  
 [Reporting Services 拡張機能](../../../reporting-services/extensions/reporting-services-extensions.md)   
 [Implementing a Delivery Extension](../../../reporting-services/extensions/delivery-extension/implementing-a-delivery-extension.md)   
 [Reporting Services 拡張機能ライブラリ](../../../reporting-services/extensions/reporting-services-extension-library.md)  
  
  

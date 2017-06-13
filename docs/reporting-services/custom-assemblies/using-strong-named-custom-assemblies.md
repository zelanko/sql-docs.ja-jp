---
title: "カスタム アセンブリの厳密な名前の使用 |Microsoft ドキュメント"
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
- AllowPartiallyTrustedCallersAttribute attribute
- strong-named custom assemblies [Reporting Services]
- strong names [Reporting Services]
- assemblies [Reporting Services], strong names
- custom assemblies [Reporting Services], strong-named
ms.assetid: ca9f19d7-6e86-46f2-b9ad-9bf807eaa52e
caps.latest.revision: 35
author: sabotta
ms.author: carlasab
manager: erikre
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 3c024efb9f8531ed9b87b0e2b7d7b22489a76dcf
ms.contentlocale: ja-jp
ms.lasthandoff: 06/13/2017

---
# <a name="using-strong-named-custom-assemblies"></a>複雑な名前を持つカスタム アセンブリの使用
  複雑な名前はアセンブリを識別します。この名前には、アセンブリのマニフェストに格納されたアセンブリのテキスト名、4 つの部分から成るバージョン番号、カルチャ情報 (指定されている場合)、公開キー、およびデジタル署名が含まれます。 複雑な名前は、共通言語ランタイム (CLR) にアセンブリを一意に識別し、バイナリの整合性を確保します。  
  
## <a name="using-allowpartiallytrustedcallersattribute"></a>AllowPartiallyTrustedCallersAttribute の使用  
 レポートでは、アセンブリの厳密な名前を使用するには、厳密な名前付きアセンブリを使用して、アセンブリの部分的に信頼されたコードから呼び出すことを許可する必要が**AllowPartiallyTrustedCallers**属性。 使用することができます**AllowPartiallyTrustedCallersAttribute**レポート デザイナーまたはレポートの式でレポート サーバーによって呼び出されるアセンブリの厳密な名前を使用できるようにします。 部分的に信頼されるコードが複雑な名前を持つアセンブリを呼び出すことを許可するには、アセンブリ属性ファイルに次のアセンブリ レベル属性を追加します。  
  
```vb  
<assembly:AllowPartiallyTrustedCallers>  
```  
  
```csharp  
[assembly:AllowPartiallyTrustedCallers]  
```  
  
 **AllowPartiallyTrustedCallersAttribute**アセンブリ レベルでの厳密な名前のアセンブリによって適用される場合にのみ有効です。 詳細については、アセンブリ レベル属性を適用するの属性の適用」を参照して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] SDK のドキュメントです。  
  
> [!CAUTION]  
>  ときに**AllowPartiallyTrustedCallersAttribute**が含まれている既定**FullTrustLinkDemand**セキュリティ チェックが行われないため、部分的に、他の呼び出しを可能にするには、アセンブリのアセンブリを信頼します。 すべてのセキュリティ チェックは、クラス レベルやメソッド レベルの宣言セキュリティ属性を含め、明示的に指定する必要があります。  
  
## <a name="see-also"></a>参照  
 [レポートでカスタム アセンブリの使用](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md)  
  
  

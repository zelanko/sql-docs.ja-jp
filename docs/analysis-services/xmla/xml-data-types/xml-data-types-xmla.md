---
title: "XML データ型 (XMLA) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- XML data types [XMLA]
- data types [XML for Analysis]
- XMLA, data types
- XML for Analysis, data types
ms.assetid: 979b5384-90d9-4e09-9286-1d1eafdc4864
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 60a10edf09c041b563f15bf5fec83cd1b5ec4ec7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="xml-data-types-xmla"></a>XML データ型 (XMLA)
  XML for Analysis (XMLA) 1.1 仕様では、XML 1.0 勧告で定義された標準的なプリミティブ型および派生型に加えて、多次元データおよび表形式データの表記をサポートする追加のデータ型が定義されています。  
  
 XMLA は、次の表に示されているデータ型を使用します。  
  
|データ型|Description|  
|----------------|-----------------|  
|ブール値|標準 XML**ブール**データ型。|  
|Decimal|標準 XML **decimal**データ型。|  
|[EmptyResult](../../../analysis-services/xmla/xml-data-types/emptyresult-data-type-xmla.md)|上の名前空間、**ルート**要素。 エラーが発生したためか、いずれかの XMLA コマンドが通常結果を返さないため、XMLA コマンドが結果を返さない場合、この名前空間が返されます、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] XMLA コマンドの実行中にインスタンス。|  
|[EnumString](../../../analysis-services/xmla/xml-data-types/enumstring-data-type-xmla.md)|特定の列挙子に関連した名前付き文字列定数のセット。|  
|Integer|標準 XML **int**データ型。|  
|[MDDataSet](../../../analysis-services/xmla/xml-data-types/mddataset-data-type-xmla.md)|によって返される多次元データ、*結果*のパラメーター、 [Execute](../../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。|  
|[結果セット](../../../analysis-services/xmla/xml-data-types/resultset-data-type-xmla.md)|自己記述型 XML 結果セットがによって返される、 **Execute**メソッドです。|  
|[行セット](../../../analysis-services/xmla/xml-data-types/rowset-data-type-xmla.md)|によって返される、埋め込みの XML スキーマによって構造化されたデータ ソースから行、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドです。|  
|文字列|XML**文字列**データ型。|  
|UnsignedInt|XML **unsignedInt**スキーマの型。|  
  
 標準的な XML データ型の詳細な説明については、World Wide Web Consortium (W3C) 勧告候補を参照してください。  
  
## <a name="see-also"></a>参照  
 [XML 要素 & #40 です。XMLA &#41;](http://msdn.microsoft.com/library/40ab2360-efb6-4ba6-bf23-e84964e51008)   
 [XML for Analysis & #40 です。XMLA &#41;参照](../../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  


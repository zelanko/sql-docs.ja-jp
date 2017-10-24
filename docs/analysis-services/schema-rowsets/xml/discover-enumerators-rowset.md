---
title: "DISCOVER_ENUMERATORS 行セット |Microsoft ドキュメント"
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
apiname:
- DISCOVER_ENUMERATORS
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_ENUMERATORS rowset
ms.assetid: ddc7b13c-3135-4419-8166-eddd459167da
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 66ad0a7e82cb1b74108a1275a9e0a7363183d051
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discoverenumerators-rowset"></a>DISCOVER_ENUMERATORS 行セット
  特定のデータ ソースの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされている列挙子の名前、データ型、および列挙値の一覧を返します。 XMLA プロバイダーは、認識できるすべての列挙定数をパブリッシュします。  
  
 呼び出す場合は、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドを**DISCOVER_ENUMERATORS**の列挙値に、 [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)要素、 **Discover**メソッドを返します、 **DISCOVER_ENUMERATORS**スキーマ行セット。  
  
## <a name="rowset-columns"></a>行セットの列  
 列挙子ごとに複数の要素があり、各要素は列挙内の各値に対応しています。 各列挙子を表す行セットはフラットであり、列挙子の名前は同じ列挙に所属する要素に対して重複して使用される場合があります。  
  
 **DISCOVER_ENUMERATORS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|Description|  
|-----------------|--------------------|------------|-----------------|  
|**EnumName**|**DBTYPE_WSTR**||値のセットが含まれている列挙子の名前。|  
|**EnumDescription**|**DBTYPE_WSTR**||列挙子のローカライズ可能な説明。 指定できます**NULL**です。|  
|**EnumType**|**DBTYPE_WSTR**||列挙値のデータ型。|  
|**ElementName**|**DBTYPE_WSTR**||列挙子セット内のいずれかの値要素の名前。<br /><br /> 例: **TDP**|  
|**ElementDescription**|**DBTYPE_WSTR**||(省略可) 要素のローカライズ可能な説明。 指定できます**NULL**です。|  
|**要素の値**|**DBTYPE_WSTR**||要素の値です。 指定できます**NULL**です。<br /><br /> 例: **01**|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_ENUMERATORS**行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**EnumName**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  


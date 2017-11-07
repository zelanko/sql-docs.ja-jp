---
title: "DISCOVER_PROPERTIES 行セット |Microsoft ドキュメント"
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
- DISCOVER_PROPERTIES
apitype: NA
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 374ca8fc9ce17f7da659a9718e8a7a531e8c3ca5
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="discoverproperties-rowset"></a>DISCOVER_PROPERTIES 行セット
  指定されたデータ ソースの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされている標準プロパティとプロバイダー固有のプロパティに関する情報および値の一覧を返します。 サポートされていないプロパティは、返される結果セットに表示されません。  
  
 呼び出す場合は、 [Discover](../../../analysis-services/xmla/xml-elements-methods-discover.md)メソッドを**DISCOVER_PROPERTIES**の列挙値に、 [RequestType](../../../analysis-services/xmla/xml-elements-properties/requesttype-element-xmla.md)要素、 **Discover**メソッドを返します、 **DISCOVER_PROPERTIES**行セット.  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_PROPERTIES**行セットには、次の列が含まれています。  
  
|列名|型|長さ|Description|  
|-----------------|----------|------------|-----------------|  
|**プロパティ名**|**DBTYPE_WSTR**||プロパティの名前。|  
|**調べます。**|**DBTYPE_WSTR**||プロパティのローカライズ可能な説明テキスト。 返す可能性があります**NULL**です。|  
|**PropertyType**|**DBTYPE_WSTR**||プロパティの XML データ型。<br /><br /> 返す可能性があります**NULL**です。|  
|**PropertyAccessType**|**DBTYPE_WSTR**||プロパティのアクセス。 値を指定できます**読み取り**、**書き込み**、または**ReadWrite**です。|  
|**IsRequired**|**DBTYPE_BOOL**||プロパティが必須かどうかを示すブール値。<br /><br /> 必須の場合は True、必須でない場合は False です。<br /><br /> 返す可能性があります**NULL**です。|  
|**値**|**DBTYPE_WSTR**||プロパティの現在の値。<br /><br /> 返す可能性があります**NULL**です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_PROPERTIES**行セットは、次の表に表示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**プロパティ名**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  


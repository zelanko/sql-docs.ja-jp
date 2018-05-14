---
title: DISCOVER_PROPERTIES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 8752af7b67b69659ec3d9a348b4ec7c647f41c55
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="discoverproperties-rowset"></a>DISCOVER_PROPERTIES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
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
  
  

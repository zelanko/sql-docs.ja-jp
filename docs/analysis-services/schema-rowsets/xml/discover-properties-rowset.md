---
title: DISCOVER_PROPERTIES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
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
ms.openlocfilehash: ec2485a79588e4e7cdd9a73b4c6169a069a57318
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discoverproperties-rowset"></a>DISCOVER_PROPERTIES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]サポートされている標準とプロバイダー固有のプロパティに関する情報と値の一覧を返します、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーの指定したデータ ソース。 サポートされていないプロパティは、返される結果セットに表示されません。  
  
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
|**[値]**|**DBTYPE_WSTR**||プロパティの現在の値。<br /><br /> 返す可能性があります**NULL**です。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_PROPERTIES**行セットは、次の表に表示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|**プロパティ名**|**DBTYPE_WSTR**||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

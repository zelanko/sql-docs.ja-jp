---
title: DISCOVER_PROPERTIES 行セット |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
api_name:
- DISCOVER_PROPERTIES
topic_type:
- apiref
helpviewer_keywords:
- DISCOVER_PROPERTIES rowset
ms.assetid: 3e2b50e2-3855-4091-8b02-4968e8e57d4c
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: af566467345e29362a7b2fdd2c5bda04a35a6dd5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164182"
---
# <a name="discoverproperties-rowset"></a>DISCOVER_PROPERTIES 行セット
  指定されたデータ ソースの [!INCLUDE[msCoName](../../../includes/msconame-md.md)] XML for Analysis (XMLA) プロバイダーによってサポートされている標準プロパティとプロバイダー固有のプロパティに関する情報および値の一覧を返します。 サポートされていないプロパティは、返される結果セットに表示されません。  
  
 呼び出す場合は、 [Discover](../../xmla/xml-elements-methods-discover.md)メソッドを`DISCOVER_PROPERTIES`の列挙値に、 [RequestType](../../xmla/xml-elements-properties/type-element-xmla.md)要素、`Discover`メソッドを返します、`DISCOVER_PROPERTIES`行セット.  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_PROPERTIES`行セットには、次の列が含まれています。  
  
|列名|型|長さ|説明|  
|-----------------|----------|------------|-----------------|  
|`PropertyName`|`DBTYPE_WSTR`||プロパティの名前。|  
|`PropertyDescription`|`DBTYPE_WSTR`||プロパティのローカライズ可能な説明テキスト。 `NULL` を返す場合もあります。|  
|`PropertyType`|`DBTYPE_WSTR`||プロパティの XML データ型。<br /><br /> `NULL` を返す場合もあります。|  
|`PropertyAccessType`|`DBTYPE_WSTR`||プロパティのアクセス。 値を指定できます`Read`、 `Write`、または`ReadWrite`です。|  
|`IsRequired`|`DBTYPE_BOOL`||プロパティが必須かどうかを示すブール値。<br /><br /> 必須の場合は True、必須でない場合は False です。<br /><br /> `NULL` を返す場合もあります。|  
|`Value`|`DBTYPE_WSTR`||プロパティの現在の値。<br /><br /> `NULL` を返す場合もあります。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_PROPERTIES` 行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|`PropertyName`|`DBTYPE_WSTR`||  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
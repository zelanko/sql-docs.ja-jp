---
title: DISCOVER_STORAGE_TABLES 行セット |Microsoft Docs
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
ms.assetid: 13df6f10-8efe-4fe9-83a6-96d108809ed1
caps.latest.revision: 13
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 97f5e645098da53c720d37814b4dc4dbfe6f1c76
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37169553"
---
# <a name="discoverstoragetables-rowset"></a>DISCOVER_STORAGE_TABLES 行セット
  クライアントは、テーブル モードまたは SharePoint モードで動作している Analysis Services データベースに含まれているテーブルを調べることができます。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_STORAGE_TABLES`行セットには、次の列が含まれています。  
  
|**列名**|**型インジケーター**|**Length**|**[説明]**|  
|---------------------|------------------------|----------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`||テーブルを含んでいるデータベースの名前を指定します。<br /><br /> `DISCOVER_STORAGE_TABLES`行セットは、この列を使用して制限できます。 この列を使用せずに行セットを制限した場合、現在のデータベースが使用されます。|  
|`CUBE_NAME`|`DBTYPE_WSTR`||テーブルを含んでいるキューブまたはモデルを指定します。<br /><br /> `DISCOVER_STORAGE_TABLES`行セットは、この列を使用して制限できます。|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`||メジャー グループの名前。|  
|`PARTITION_NAME`|`DBTYPE_WSTR`||パーティションの名前。|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||ディメンションの名前。|  
|`TABLE_ID`|`DBTYPE_WSTR`||テーブルの属性を格納するために使用されるテーブルの ID。|  
|`TABLE_PARTITIONS_COUNT`|`DBTYPE_ WSTR`||テーブルのパーティション数。|  
|`HINT_TABLE_TYPE`|`DBTYPE_ WSTR`||テーブル型のヒント。|  
|`ROWS_COUNT`|`DBTYPE_UI4`||パーティション内の行の数。|  
|`RIVIOLATION_COUNT`|`DBTYPE_UI4`||参照整合性違反の行数。|  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_STORAGE_TABLES`行セットは、次の表に示されている列で制限できます。  
  
|**列名**|**型インジケーター**|**制限の状態**|  
|---------------------|------------------------|---------------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|任意。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|任意。|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|省略可|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|省略可|  
  
## <a name="example"></a>例  
 次のコード サンプルは、現在の接続の既定のデータベースから、ストレージ テーブルとその行数の一覧を返します。  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

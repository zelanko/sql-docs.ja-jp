---
title: DISCOVER_STORAGE_TABLES 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 0685808f47364f7e88f82b48540034ef0d0e688a
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discoverstoragetables-rowset"></a>DISCOVER_STORAGE_TABLES 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  クライアントは、テーブル モードまたは SharePoint モードで動作している Analysis Services データベースに含まれているテーブルを調べることができます。  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_STORAGE_TABLES**行セットには、次の列が含まれています。  
  
|**列名**|**型インジケーター**|**長さ**|**Description**|  
|---------------------|------------------------|----------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**||テーブルを含んでいるデータベースの名前を指定します。<br /><br /> **DISCOVER_STORAGE_TABLES**この列を使用して行セットを制限することができます。 この列を使用せずに行セットを制限した場合、現在のデータベースが使用されます。|  
|**CUBE_NAME**|**DBTYPE_WSTR**||テーブルを含んでいるキューブまたはモデルを指定します。<br /><br /> **DISCOVER_STORAGE_TABLES**この列を使用して行セットを制限することができます。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**||メジャー グループの名前。|  
|**PARTITION_NAME**|**DBTYPE_WSTR**||パーティションの名前。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||ディメンションの名前。|  
|**TABLE_ID**|**DBTYPE_WSTR**||テーブルの属性を格納するために使用されるテーブルの ID。|  
|**TABLE_PARTITIONS_COUNT**|**DBTYPE_ WSTR**||テーブルのパーティション数。|  
|**HINT_TABLE_TYPE**|**DBTYPE_ WSTR**||テーブル型のヒント。|  
|**ROWS_COUNT**|**DBTYPE_UI4**||パーティション内の行の数。|  
|**RIVIOLATION_COUNT**|**DBTYPE_UI4**||参照整合性違反の行数。|  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_STORAGE_TABLES**行セットは、次の表に示されている列で制限できます。  
  
|**列名**|**型インジケーター**|**制限の状態**|  
|---------------------|------------------------|---------------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|省略可。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|省略可|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|省略可|  
  
## <a name="example"></a>例  
 次のコード サンプルは、現在の接続の既定のデータベースから、ストレージ テーブルとその行数の一覧を返します。  
  
```  
SELECT TABLE_ID, ROWS_COUNT  
FROM $system.DISCOVER_STORAGE_TABLES  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

---
title: DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行セット |Microsoft ドキュメント
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
ms.assetid: 3e514715-9fe6-4e6a-accb-4149ffd7e0bf
caps.latest.revision: 13
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 2155e4a905da3aeade0f0789f05cc04cdd42f8d8
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072184"
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行セット
  テーブル モードまたは PowerPivot モードで動作している Analysis Services データベースに関して、使用されているストレージ テーブルについての列およびセグメント レベルの情報を提供します。 この行セットは、主にトラブルシューティングや分析に使用されます。  
  
 **適用対象:** テーブル モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS`行セットには、次の列が含まれています。  
  
|**列名**|**型インジケーター**|**制限**|**description**|  
|---------------------|------------------------|---------------------|---------------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|はい|表形式のデータベースを指定します。<br /><br /> `DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS`この列を使用して行セットを制限することができます。 現在のデータベースを省略した場合は使用されます。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|はい|モデルの名前。<br /><br /> `DISCOVER_STORAGE_TABLES`この列を使用して行セットを制限することができます。|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|はい|メジャー グループの名前。|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|はい|パーティションの名前。|  
|`DIMENSION_NAME`|`DBTYPE_WSTR`||ディメンションの名前。|  
|`TABLE_ID`|`DBTYPE_WSTR`||テーブル セグメントの内部 ID。|  
|`COLUMN_ID`|`DBTYPE_WSTR`||列の内部 ID。|  
|`SEGMENT _NUMBER`|`DBTYPE_I8`||テーブル セグメントの序数。|  
|`TABLE_PARTTION_NUMBER`|`DBTYPE_I8`||パーティションの序数。|  
|`RECORDS_COUNT`|`DBTYPE_I8`||パーティション内のレコード数。|  
|`ALLOCATED_SIZE`|`DBTYPE_UI8`||列セグメントに割り当てられたサイズ (バイト単位)。|  
|`USED_SIZE`|`DBTYPE_UI8`||列セグメントによって使用されているサイズ (バイト単位)。|  
|`COMPRESSION_TYPE`|`DBTYPE_WSTR`||列セグメントに適用されている圧縮の種類。 この値は内部使用とカスタマー サポートでの使用のみを目的としています。 Microsoft では、有効な値およびこの列に関する説明を公開していません。|  
|`BITS_COUNT`|`DBTYPE_I8`||ビットのカウント。|  
|`BOOKMARK_BITS_COUNT`|`DBTYPE_I8`||ブックマーク ビットのカウント。|  
|`VERTIPAQ_STATE`|`DBTYPE_WSTR`||この列セグメントの VertiPaq 圧縮の状態です。 値は次のいずれかになります。<br /><br /> -SKIPPED – VertiPaq 圧縮はスキップされました。<br />完成した – VertiPaq 圧縮を正常に完了しました。<br />-TIMEBOXED – VertiPaq 圧縮は、時間枠は設定されました。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd45-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageSegments|  
  
## <a name="example"></a>例  
 次のクエリは、現在のデータベース内のモデル属性 LastName に関連付けられているストレージ テーブル セグメントを返します。  
  
```  
SELECT DISTINCT TABLE_ID, COLUMN_ID   
FROM $system.DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS  
WHERE COLUMN_ID = 'LastName'  
ORDER BY TABLE_ID  
  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../analysis-services-schema-rowsets.md)  
  
  
---
title: DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 110e5af35638c0eddb5cf0610955a737965373e3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discoverstoragetablecolumnsegments-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  表形式で実行される Analysis Services データベースによって使用されるストレージ テーブルに関する列およびセグメント レベルの情報を提供または[!INCLUDE[ssGemini](../../../includes/ssgemini-md.md)]モード。 この行セットは、主にトラブルシューティングや分析に使用されます。  
  
 **適用対象:** テーブル モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS**行セットには、次の列が含まれています。  
  
|**列名**|**型インジケーター**|**制限**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|はい|表形式のデータベースを指定します。<br /><br /> **DISCOVER_STORAGE_TABLE_COLUMN_SEGMENTS**この列を使用して行セットを制限することができます。 現在のデータベースを省略した場合は使用されます。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|はい|モデルの名前。<br /><br /> **DISCOVER_STORAGE_TABLES**この列を使用して行セットを制限することができます。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|はい|メジャー グループの名前。|  
|**PARTITION_NAME**|**DBTYPE_WSTR**|はい|パーティションの名前。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||ディメンションの名前。|  
|**TABLE_ID**|**DBTYPE_WSTR**||テーブル セグメントの内部 ID。|  
|**COLUMN_ID**|**DBTYPE_WSTR**||列の内部 ID。|  
|**セグメント数 (_N)**|**DBTYPE_I8**||テーブル セグメントの序数。|  
|**TABLE_PARTTION_NUMBER**|**DBTYPE_I8**||パーティションの序数。|  
|**RECORDS_COUNT**|**DBTYPE_I8**||パーティション内のレコード数。|  
|**ALLOCATED_SIZE**|**DBTYPE_UI8**||列セグメントに割り当てられたサイズ (バイト単位)。|  
|**USED_SIZE**|**DBTYPE_UI8**||列セグメントによって使用されているサイズ (バイト単位)。|  
|**COMPRESSION_TYPE**|**DBTYPE_WSTR**||列セグメントに適用されている圧縮の種類。 この値は内部使用とカスタマー サポートでの使用のみを目的としています。 Microsoft では、有効な値およびこの列に関する説明を公開していません。|  
|**BITS_COUNT**|**DBTYPE_I8**||ビットのカウント。|  
|**BOOKMARK_BITS_COUNT**|**DBTYPE_I8**||ブックマーク ビットのカウント。|  
|**VERTIPAQ_STATE**|**DBTYPE_WSTR**||この列セグメントの VertiPaq 圧縮の状態です。 値は次のいずれかになります。<br /><br /> SKIPPED – VertiPaq 圧縮はスキップされました。<br /><br /> COMPLETED – VertiPaq 圧縮は正常に完了しました。<br /><br /> TIMEBOXED – VertiPaq 圧縮は時間枠を設定されました。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
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
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

---
title: "DISCOVER_STORAGE_TABLE_COLUMNS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/03/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
ms.assetid: 24abb88e-33a9-4ae2-829d-cdef0ff22ec1
caps.latest.revision: "14"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8a0fec3423b126a425206441543fd50679712c2f
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discoverstoragetablecolumns-rowset"></a>DISCOVER_STORAGE_TABLE_COLUMNS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]SharePoint モードまたは表形式モードで実行されている Analysis Services データベースによって使用されるストレージ テーブルについて、列レベルの情報を提供します。  
  
 **適用対象:** テーブル モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_STORAGE_TABLE_COLUMNS**行セットには、次の列が含まれています。  
  
|**列名**|**型インジケーター**|**制限**|**Description**|  
|---------------------|------------------------|---------------------|---------------------|  
|**DATABASE_NAME**|**DBTYPE_WSTR**|可|テーブルを含んでいるデータベースの名前を指定します。 省略した場合は、現在のデータベースが使用されます。<br /><br /> **DISCOVER_STORAGE_TABLE_COLUMNS**この列を使用して行セットを制限することができます。|  
|**CUBE_NAME**|**DBTYPE_WSTR**|可|テーブルを含んでいるキューブまたはモデルを指定します。<br /><br /> **DISCOVER_STORAGE_TABLES**この列を使用して行セットを制限することができます。|  
|**MEASURE_GROUP_NAME**|**DBTYPE_WSTR**|可|メジャー グループの名前。|  
|**DIMENSION_NAME**|**DBTYPE_WSTR**||ディメンションの名前。|  
|**ATTRIBUTE_NAME**|**DBTYPE_WSTR**||属性の名前。|  
|**TABLE_ID**|**DBTYPE_WSTR**||テーブルの ID。|  
|**COLUMN_ID**|**DBTYPE _ WSTR**||列の ID。 列 ID は xVelocity メモリ内分析エンジン (VertiPaq) 内部の情報です。情報提供のみを目的としています。|  
|**COLUMN_TYPE**|**DBTYPE_WSTR**||列の型。 列の型は xVelocity メモリ内分析エンジン (VertiPaq) 内部の情報です。情報提供のみを目的としています。<br /><br /> BASIC_DATA<br /><br /> HIERARCHY_DATAID_TO_POSITION<br /><br /> HIERARCHY_POSITION_TO_DATAID<br /><br /> RELATIONSHIP|  
|**COLUMN_ENCODING**|**DBTYPE_UI8**||列のデータに対して使用されるエンコーディングの種類を表す整数。<br /><br /> **0**で使用される、 **COLUMN_TYPE**: HIERARCHY_DATAID_TO_POSITION、HIERARCHY_POSITION_TO_DATAID、リレーションシップ<br /><br /> **1**で使用される、 **COLUMN_TYPE**: BASIC_DATA<br /><br /> **2**で使用される、 **COLUMN_TYPE**: BASIC_DATA|  
|**データ型**|**DBTYPE_WSTR**||列のデータ型。 次の値があります。<br /><br /> DBTYPE_BOOL<br /><br /> DBTYPE_CY<br /><br /> DBTYPE_DATE<br /><br /> DBTYPE_I4<br /><br /> DBTYPE_I8<br /><br /> DBTYPE_R8<br /><br /> DBTYPE_WSTR<br /><br /> なし|  
|**ISKEY**|**DBTYPE_BOOL**||**True**場合は、列、主キーまたは外部キーとして使用されます。 それ以外の場合は、 **false**です。|  
|**ISUNIQUE**|**DBTYPE_BOOL**||**True**場合は、列の値は、それ以外の一意な**false**です。|  
|**ISNULLABLE**|**DBTYPE_BOOL**||**True**列が null 許容それ以外の場合**false**です。|  
|**ISROWNUMBER**|**DBTYPE_BOOL**||**True**列が行番号列の場合。 行番号列は、xVelocity メモリ内分析エンジンによって内部的に使用されます。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd44-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|StorageTableColumns|  
  
## <a name="example"></a>例  
 次のコード サンプルでは、DMV クエリを使用して結果セットを返します。  
  
```  
SELECT *  
FROM $System.DISCOVER_STORAGE_TABLE_COLUMNS  
ORDER BY TABLE_ID DESC  
  
```  
  
## <a name="see-also"></a>参照  
 [Analysis Services のスキーマ行セット](../../../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)  
  
  

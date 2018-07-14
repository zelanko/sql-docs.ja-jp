---
title: DISCOVER_PARTITION_STAT 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 20d339e2-f47f-437f-94d5-5b00b400356a
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 6711aa9d7a98fa635694cc76e98cc89507d524ca
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37197812"
---
# <a name="discoverpartitionstat-rowset"></a>DISCOVER_PARTITION_STAT 行セット
  特定のパーティションの集計に関する統計を返します。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_PARTITION_STAT`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|説明|  
|-----------------|--------------------|-----------------|-----------------|  
|`DATABASE_NAME`|`DBTYPE_WSTR`|必須|ディメンションを含むデータベースの名前。<br /><br /> この列は制限リストに必要です。|  
|`CUBE_NAME`|`DBTYPE_WSTR`|必須|パーティションを含むキューブまたはテーブル モデルの名前です。<br /><br /> この列は制限リストに必要です。|  
|`MEASURE_GROUP_NAME`|`DBTYPE_WSTR`|必須|ディメンション内のメジャー グループの名前です。<br /><br /> この列は制限リストに必要です。|  
|`PARTITION_NAME`|`DBTYPE_WSTR`|必須|パーティションの名前。<br /><br /> この列は制限リストに必要です。|  
|`AGGREGATION_NAME`|`DBTYPE_WSTR`||集計の名前です。|  
|`AGGREGATION_SIZE`|`DBTYPE_I8`||集計のサイズです。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd8f-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|PartitionStat|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  

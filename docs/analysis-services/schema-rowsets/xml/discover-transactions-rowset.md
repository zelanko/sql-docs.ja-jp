---
title: DISCOVER_TRANSACTIONS 行セット |Microsoft ドキュメント
ms.date: 05/03/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: schema-rowsets
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4084d4a964a901c7f4fc78114f596ef9d6708dc3
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS 行セット
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  現在システムで保留中のトランザクションのセットを返します。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_TRANSACTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|Description|  
|-----------------|--------------------|-----------------|  
|**TRANSACTION_ID**|**DBTYPE_WSTR**|トランザクション、一意な識別子として GUID。|  
|**TRANSACTION_SESSION_ID**|**DBTYPE_WSTR**|GUID としてのトランザクション セッションの一意識別子。|  
|**TRANSACTION_START_TIME**|**DBTYPE_DBTIMESTAMP**|トランザクションが開始されたときのサーバーの UTC 日時。|  
|**TRANSACTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|トランザクションが開始されてからの経過時間 (ミリ秒単位)。|  
|**TRANSACTION_CPU_TIME_MS**|**DBTYPE_I8**|トランザクションの開始以降にすべての要求で使用された CPU 時間 (ミリ秒単位)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 **DISCOVER_TRANSACTIONS**行セットは、次の表に示されている列で制限できます。  
  
|**列名**|**型インジケーター**|**制限の状態**|  
|---------------------|------------------------|---------------------------|  
|**ID**|**DBTYPE_WSTR**|省略可。|  
|**SESSION_ID**|**DBTYPE_WSTR**|省略可。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|文字列|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis スキーマ行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

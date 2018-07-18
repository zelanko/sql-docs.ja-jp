---
title: DISCOVER_TRANSACTIONS 行セット |Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 85789177-c5df-4336-a90c-c20d69277ab4
caps.latest.revision: 6
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 979067978855e8aa1012deb8df39bea61862fdeb
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37204552"
---
# <a name="discovertransactions-rowset"></a>DISCOVER_TRANSACTIONS 行セット
  現在システムで保留中のトランザクションのセットを返します。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_TRANSACTIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|説明|  
|-----------------|--------------------|-----------------|  
|`TRANSACTION_ID`|`DBTYPE_WSTR`|トランザクション一意の識別子を GUID として。|  
|`TRANSACTION_SESSION_ID`|`DBTYPE_WSTR`|GUID としてのトランザクション セッションの一意識別子。|  
|`TRANSACTION_START_TIME`|`DBTYPE_DBTIMESTAMP`|トランザクションが開始されたときのサーバーの UTC 日時。|  
|`TRANSACTION_ELAPSED_TIME_MS`|`DBTYPE_I8`|トランザクションが開始されてからの経過時間 (ミリ秒単位)。|  
|`TRANSACTION_CPU_TIME_MS`|`DBTYPE_I8`|トランザクションの開始以降にすべての要求で使用された CPU 時間 (ミリ秒単位)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_TRANSACTIONS`行セットは、次の表に示されている列で制限できます。  
  
|**列名**|**型インジケーター**|**制限の状態**|  
|---------------------|------------------------|---------------------------|  
|`ID`|`DBTYPE_WSTR`|任意。|  
|`SESSION_ID`|`DBTYPE_WSTR`|任意。|  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd28-8148-11d0-87bb-00c04fc33942|  
|String|DISCOVER_TRANSACTIONS|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  

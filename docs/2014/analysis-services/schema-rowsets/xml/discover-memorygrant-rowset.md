---
title: DISCOVER_MEMORYGRANT 行セット |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
ms.assetid: d254e42d-9918-47ce-b6df-47f1f0b432dd
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 21e24d1a7ab727eeb2c014870adb9928aed989dd
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48154262"
---
# <a name="discovermemorygrant-rowset"></a>DISCOVER_MEMORYGRANT 行セット
  サーバーで現在実行中のジョブによって確保されている内部メモリ クォータ付与の一覧を返します。 サーバーでジョブが実行されているかどうかを調べるには、`Select * from $System.Discover_Jobs` を使用します。  
  
 **適用対象:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_MEMORYGRANT`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|説明|  
|-----------------|--------------------|-----------------|-----------------|  
|`MEMORY_ID`|**DBTYPE_I8**||メモリ クォータ付与を識別する番号。 1 つの DISCOVER_MEMORYGRANT 要求のコンテキスト内で一意です。|  
|`SPID`|`DBTYPE_I4`|必須|SPID は、`Select * from $System.Discover_Sessions` を実行することにより取得できます。|  
|`CreationTime`|`DBTYPE_I8 DBTYPE_DBTIMESTAMP`||クォータが付与された時刻。|  
|`LastRequestTime`|**DBTYPE_DBTIMESTAMP**||クォータ要求を前回変更した時刻。|  
|`MemoryUsed`|`DBTYPE_I4`||クォータに関連して使用されたメモリの量。|  
|`MemoryGranted`|`DBTYPE_I4`||メモリ クォータを取得するジョブで使用するために付与されたメモリの量。|  
|`Blocked`|`DBTYPE_BOOL`||ジョブのブロック状態を示すブール値。 True は、そのジョブがブロックされており、そのクォータ要求を許可するのに十分なクォータが別のジョブから解放されるまで待機していることを示します。 False は、ジョブがそのクォータを受け取り、実行できることを示します。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd23-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|MemoryGrant|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  

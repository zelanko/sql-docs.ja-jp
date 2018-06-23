---
title: DISCOVER_COMMAND_OBJECTS 行セット |Microsoft ドキュメント
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
helpviewer_keywords:
- DISCOVER_COMMAND_OBJECTS rowset
ms.assetid: 325114ee-3a50-4504-9782-dbf7c1a44778
caps.latest.revision: 21
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: c53fccdecc824bd123312a881c1ddcdbcae6060a
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085104"
---
# <a name="discovercommandobjects-rowset"></a>DISCOVER_COMMAND_OBJECTS 行セット
  参照先のコマンドによって使用中のオブジェクトに関するリソース使用状況とアクティビティ情報を提供します。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_COMMAND_OBJECTS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|説明|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|はい|セッション ID。|  
|`SESSION_ID`|`DBTYPE_WSTR`|はい|GUID としてのセッションの一意識別子。|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||コマンドのシーケンス番号。|  
|`OBJECT_PARENT_PATH`|`DBTYPE_WSTR`|はい|現在のオブジェクトの親へのパス。|  
|`OBJECT_ID`|`DBTYPE_WSTR`|はい|作成したときに定義されたオブジェクトの ID。|  
|`OBJECT_VERSION`|`DBTYPE_I4`||オブジェクトのメタデータ バージョン番号。この番号は、オブジェクトが変更されるたびに変わります。|  
|`OBJECT_DATA_VERSION`|`DBTYPE_I4`||オブジェクト内のデータの系列番号。 この番号は、オブジェクトが処理されるたびに増加します。|  
|`OBJECT_CPU_TIME_MS`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによって使用された CPU 時間 (ミリ秒単位)。|  
|`OBJECT_READ_KB`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによって読み取られたデータの累積値 (KB 単位)。|  
|`OBJECT_READS`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによって行われた読み取り操作の累積数。|  
|`OBJECT_WRITE_KB`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによって書き込まれたデータの累積値 (KB 単位)。|  
|`OBJECT_WRITES`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによって行われた書き込み操作の累積数。|  
|`OBJECT_ROWS_RETURNED`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによって呼び出し元に返された行数。|  
|`OBJECT_ROWS_SCANNED`|`DBTYPE_I8`||コマンドの開始以降にオブジェクトによってスキャンされた行数。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  DISCOVER_COMMAND_OBJECTS スキーマ行セットは DMV クエリでは利用状況を報告しません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd35-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|CommandObjects|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
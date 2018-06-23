---
title: DISCOVER_COMMANDS 行セット |Microsoft ドキュメント
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
- DISCOVER_COMMANDS rowset
ms.assetid: d228f265-05d9-4d2c-a622-44c73eab7a71
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 14c4eb9ac8fe63422ee29f5880a8a5f1eb6329bf
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36082865"
---
# <a name="discovercommands-rowset"></a>DISCOVER_COMMANDS 行セット
  サーバーで、現在実行中または最後のコマンドの実行で開いている接続に関するリソース使用状況とアクティビティ情報を提供します。  
  
 **適用されます:** 表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_COMMANDS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|説明|  
|-----------------|--------------------|-----------------|-----------------|  
|`SESSION_SPID`|`DBTYPE_I4`|はい|セッション ID。|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||セッションの開始以降に実行されたコマンドの数。|  
|`COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||最後のコマンドが開始された日時。サーバーの UTC 時刻で表されます。|  
|`COMMAND_ELAPSED_TIME_MS`|`DBTYPE_I8`||コマンドが開始されてからの経過時間 (ミリ秒単位)。|  
|`COMMAND_CPU_TIME_MS`|`DBTYPE_I8`||コマンドの実行開始以降にコマンドによって使用された CPU 時間 (ミリ秒単位)。|  
|`COMMAND_READS`|`DBTYPE_I8`||コマンドの開始以降に行われたディスク読み取りの累積数。|  
|`COMMAND_READ_KB`|`DBTYPE_I8`||コマンドの開始以降にディスクから読み取られたデータの累積値 (KB 単位)。|  
|`COMMAND_WRITES`|`DBTYPE_I8`||コマンドの開始以降に行われたディスク書き込みの累積数。|  
|`COMMAND_WRITE_KB`|`DBTYPE_I8`||コマンドの開始以降にディスクに書き込まれたデータの累積値 (KB 単位)。|  
|`COMMAND_TEXT`|`DBTYPE_WSTR`||コマンド テキスト。|  
|`COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||コマンドが実行を完了したときのサーバーの UTC 日時。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../relational-databases/native-client-ole-db-rowsets/rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd34-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|コマンド|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
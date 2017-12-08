---
title: "DISCOVER_CONNECTIONS 行セット |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: schema-rowsets
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to: SQL Server 2016 Preview
helpviewer_keywords: DISCOVER_CONNECTIONS rowset
ms.assetid: e4703970-c31d-448c-ab68-503303c91aa4
caps.latest.revision: "16"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 249e8492927b9dd88d0f135e16236ecd2aea0609
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="discoverconnections-rowset"></a>DISCOVER_CONNECTIONS 行セット
  現在サーバー上で開いている接続について、リソースの使用状況とアクティビティに関する情報を提供します。  
  
 **適用されます:**表形式モデル、多次元モデル  
  
## <a name="rowset-columns"></a>行セットの列  
 **DISCOVER_CONNECTIONS**行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|制限|Description|  
|-----------------|--------------------|------------------|-----------------|  
|**CONNECTION_ID**|**DBTYPE_I4**|可|接続を識別する一意の番号。|  
|**CONNECTION_USER_NAME**|**DBTYPE_WSTR**|可|接続のユーザー名。|  
|**CONNECTION_IMPERSONATED_USER_NAME**|**DBTYPE_WSTR**|可|将来の使用のために予約されています。 Analysis Services は、CONNECTION_IMPERSONATED_USER_NAME の値に対しては常に NULL を返します。|  
|**CONNECTION_HOST_NAME**|**DBTYPE_WSTR**|可|接続を開始したコンピューターの名前。|  
|**CONNECTION_HOST_APPLICATION**|**DBTYPE_WSTR**||接続を開始したアプリケーションの名前。|  
|**CONNECTION_START_TIME**|**DBTYPE_DBTIMESTAMP**||接続が開始されたときのサーバーの UTC 日時。|  
|**CONNECTION_ELAPSED_TIME_MS**|**DBTYPE_I8**|可|接続が開始されてからの経過時間 (ミリ秒単位)。|  
|**CONNECTION_LAST_COMMAND_START_TIME**|**DBTYPE_DBTIMESTAMP**||サーバーの UTC 日付と時刻最後のコマンドが実行を開始したときにします。|  
|**CONNECTION_LAST_COMMAND_END_TIME**|**DBTYPE_DBTIMESTAMP**||最後のコマンドが実行を完了したときのサーバーの UTC 日時。|  
|**CONNECTION_LAST_COMMAND_ELAPSED_TIME_MS**|**DBTYPE_I8**|可|最後に実行されたコマンドが終了してからの経過時間 (ミリ秒単位)。|  
|**CONNECTION_IDLE_TIME_MS**|**DBTYPE_I8**|可|接続が開始されてからのアイドル時間 (ミリ秒単位)。|  
|**CONNECTION_BYTES_SENT**|**DBTYPE_I8**||接続の開始以降に送信した累積バイト数。|  
|**CONNECTION_DATA_BYTES_SENT**|**DBTYPE_I8**||接続の開始以降に送信したデータの累積バイト数。<br /><br /> 接続ではデータが圧縮されて送受信されます。この値は、展開された送信データを表します。|  
|**CONNECTION_BYTES_RECEIVED**|**DBTYPE_I8**||接続の開始以降に受信した累積バイト数。|  
|**CONNECTION_DATA_BYTES_RECEIVED**|**DBTYPE_I8**||接続の開始以降に受信したデータの累積バイト数。<br /><br /> 接続ではデータが圧縮されて送受信されます。この値は、展開された受信データを表します。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="using-adomdnet-to-return-the-rowset"></a>ADOMD.NET を使用した行セットのリターン  
 ADOMD.NET とスキーマ行セットを使用してメタデータを取得する場合、GetSchemaDataSet メソッドで GUID または文字列を使用してスキーマ行セット オブジェクトを参照できます。 詳細については、「 [Working with Schema Rowsets in ADOMD.NET](../../../analysis-services/multidimensional-models-adomd-net-client/retrieving-metadata-working-with-schema-rowsets.md)」を参照してください。  
  
 次の表に、この行セットを識別する GUID と文字列の値を示します。  
  
|引数|値|  
|--------------|-----------|  
|GUID|a07ccd25-8148-11d0-87bb-00c04fc33942|  
|ADOMDNAME|接続|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](../../../analysis-services/schema-rowsets/xml/xml-for-analysis-schema-rowsets.md)  
  
  

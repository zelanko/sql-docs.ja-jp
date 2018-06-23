---
title: DISCOVER_DB_CONNECTIONS 行セット |Microsoft ドキュメント
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
helpviewer_keywords:
- DISCOVER_DB_CONNECTIONS rowset
ms.assetid: 12a51a4e-5f3d-4449-9d94-7836fea1bc8b
caps.latest.revision: 18
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 76b078c5b61c685634636f8891f65da722be911e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178313"
---
# <a name="discoverdbconnections-rowset"></a>DISCOVER_DB_CONNECTIONS 行セット
  サーバーからデータベースへの現在開いている接続に関するリソース使用量と利用状況の情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_DB_CONNECTIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`CONNECTION_CATALOG_NAME`|`DBTYPE_WSTR`||現在接続されているデータベースの名前。|  
|`CONNECTION_ID`|`DBTYPE_I4`||接続を識別する一意の番号。|  
|`CONNECTION_IDLE_TIME_MS`|`DBTYPE_I8`||接続が開始されてからのアイドル時間 (ミリ秒単位)。|  
|`CONNECTION_IN_USE`|`DBTYPE_I4`||接続がアクティブ (1) かアイドル (0) かを示します。|  
|`CONNECTION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||最後のコマンドが実行を完了したときのサーバーの UTC 日時。|  
|`CONNECTION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||最後のコマンドが実行を開始したときのサーバーの UTC 日時。|  
|`CONNECTION_SERVER_NAME`|`DBTYPE_WSTR`||現在接続されているサーバーの名前。|  
|`CONNECTION_SPID`|`DBTYPE_I4`||セッション ID。|  
|`CONNECTION_START_TIME`|`DBTYPE_DBTIMESTAMP`||接続が開始されたときのサーバーの UTC 日時。|  
|`CONNECTION_USAGE_TIME_MS`|`DBTYPE_I8`||接続の開始以降に接続がアクティブであった時間 (ミリ秒単位)。|  
  
 このスキーマ行セットは並べ替えられません。  
  
> [!IMPORTANT]  
>  `DISCOVER_DB_CONNECTIONS` 行セットで情報が表示されるのは、サービスがリレーショナル データ ソースに接続されているときだけです。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_DB_CONNECTIONS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|CONNECTION_ID|DBTYPE_I4|任意。|  
|CONNECTION_IN_USE|DBTYPE_I4|任意。|  
|CONNECTION_SERVER_NAME|DBTYPE_WSTR|任意。|  
|CONNECTION_CATALOG_NAME|DBTYPE_WSTR|必須。|  
|CONNECTION_SPID|DBTYPE_I4|任意。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  
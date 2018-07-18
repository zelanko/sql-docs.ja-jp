---
title: DISCOVER_SESSIONS 行セット |Microsoft Docs
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
- DISCOVER_SESSIONS rowset
ms.assetid: 47a79542-3142-4e62-a66f-6c4dbfe0f5c0
caps.latest.revision: 18
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 2b9c137aafe16ad999bba5213afaaf92c15e1c35
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37218112"
---
# <a name="discoversessions-rowset"></a>DISCOVER_SESSIONS 行セット
  サーバー上で現在開いているセッションに関するリソース使用量と利用状況の情報を提供します。  
  
## <a name="rowset-columns"></a>行セットの列  
 `DISCOVER_SESSIONS`行セットには、次の列が含まれています。  
  
|列名|型を表すインジケーター|長さ|説明|  
|-----------------|--------------------|------------|-----------------|  
|`SESSION_COMMAND_COUNT`|`DBTYPE_I4`||セッションの開始以降に実行が開始されたコマンドの数。|  
|`SESSION_CONNECTION_ID`|`DBTYPE_I4`||セッションの接続識別子。|  
|`SESSION_CPU_TIME_MS`|`DBTYPE_UI8`||セッションの開始以降にすべての要求で使用された CPU 時間 (ミリ秒単位)。|  
|`SESSION_CURRENT_DATABASE`|`DBTYPE_WSTR`||現在実行中のコマンドで使用されているデータベース、または最後に実行されたコマンドで使用されたデータベースの名前。|  
|`SESSION_ELAPSED_TIME_MS`|`DBTYPE_UI8`||セッションが開始されてからの経過時間 (ミリ秒単位)。|  
|`SESSION_ID`|`DBTYPE_WSTR`||GUID としてのセッションの一意識別子。|  
|`SESSION_IDLE_TIME_MS`|`DBTYPE_UI8`||セッションが開始されてからのアイドル時間 (ミリ秒単位)。|  
|`SESSION_LAST_COMMAND`|`DBTYPE_WSTR`||現在実行中のコマンドまたは最後に実行されたコマンドのテキスト。|  
|`SESSION_LAST_COMMAND_CPU_TIME_MS`|`DBTYPE_UI8`||`SESSION_LAST_COMMAND` によって使用された CPU 時間 (ミリ秒単位)。|  
|`SESSION_LAST_COMMAND_ELAPSED_TIME_MS`|`DBTYPE_UI8`||`SESSION_LAST_COMMAND` が開始されてからの経過時間 (ミリ秒単位)。|  
|`SESSION_LAST_COMMAND_END_TIME`|`DBTYPE_DBTIMESTAMP`||最後のコマンドが実行を完了したときの UTC サーバー時刻。|  
|`SESSION_LAST_COMMAND_START_TIME`|`DBTYPE_DBTIMESTAMP`||最後のコマンドが実行を開始したときの UTC サーバー時刻。|  
|`SESSION_PROPERTIES`|`DBTYPE_WSTR`||将来使用するために予約されています。|  
|`SESSION_READ_KB`|`DBTYPE_UI8`||セッションの開始以降にディスクから読み取られたデータの累積値 (KB 単位)。|  
|`SESSION_READS`|`DBTYPE_UI8`||セッションの開始以降に行われたディスク読み取りの累積数。|  
|`SESSION_SPID`|`DBTYPE_I4`||セッション ID。|  
|`SESSION_START_TIME`|`DBTYPE_DBTIMESTAMP`||セッションが開始された日時 (サーバーの UTC 時刻)。|  
|`SESSION_STATUS`|`DBTYPE_I4`||セッションの利用状況。<br /><br /> 0 は "アイドル"、つまり現在何も実行されていないことを意味します。<br /><br /> 1 は "アクティブ"、つまりセッションが要求されたタスクを実行していることを意味します。<br /><br /> 2 は "ブロック"、つまり中断されたタスクの実行を再開するためにセッションがリソースを待機していることを意味します。<br /><br /> 3 は "キャンセル"、つまりセッションにキャンセルというタグが付けられていることを意味します。|  
|`SESSION_USED_MEMORY`|`DBTYPE_I4`||セッションによって現在使用されているメモリのサイズ (KB 単位)。 報告される値は、SPID による RAM 使用量を示します。圧縮可能なメモリと圧縮不可能なメモリに差はありません。 メモリ使用量を報告する他の DMV とは異なり、DISCOVER_SESSIONS はメモリ使用量をカテゴリ別に分類しません。<br /><br /> SESSION_USED_MEMORY は、複数のセッションで共有されるオブジェクトを除外するため、実際のメモリ使用量よりも少なく報告する傾向があることに注意してください。  メモリの計算で表されるのは、セッションに対して一意であるこれらのオブジェクトだけです。|  
|`SESSION_USER_NAME`|`DBTYPE_WSTR`||セッションのユーザー名。|  
|`SESSION_WRITE_KB`|`DBTYPE_UI8`||セッションの開始以降にディスクに書き込まれたデータの累積値 (KB 単位)。|  
|`SESSION_WRITES`|`DBTYPE_UI8`||セッションの開始以降に行われたディスク書き込みの累積数。|  
  
 このスキーマ行セットは並べ替えられません。  
  
## <a name="restriction-columns"></a>制限の列  
 `DISCOVER_SESSIONS`行セットは、次の表に示されている列で制限できます。  
  
|列名|型を表すインジケーター|制限の状態|  
|-----------------|--------------------|-----------------------|  
|SESSION_ID|DBTYPE_WSTR|任意。|  
|SESSION_SPID|DBTYPE_I4|任意。|  
|SESSION_CONNECTION_ID|DBTYPE_I4|任意。|  
|SESSION_USER_NAME|DBTYPE_WSTR|任意。|  
|SESSION_CURRENT_DATABASE|DBTYPE_WSTR|任意。|  
|SESSION_ELAPSED_TIME_MS|DBTYPE_UI8|任意。|  
|SESSION_CPU_TIME_MS|DBTYPE_UI8|任意。|  
|SESSION_IDLE_TIME_MS|DBTYPE_UI8|任意。|  
|SESSION_STATUS|DBTYPE_I4|任意。|  
  
## <a name="see-also"></a>参照  
 [XML for Analysis Schema 行セット](xml-for-analysis-schema-rowsets.md)  
  
  

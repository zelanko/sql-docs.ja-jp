---
title: コマンドの Events Data Columns |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- Command Events event category
ms.assetid: 7169f1e2-c6be-4d8c-b147-25719b84bc2c
caps.latest.revision: 35
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 290c9ca23a71c43d16f29e0bd0e6d1f595b6df14
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070791"
---
# <a name="command-events-data-columns"></a>Command イベントのデータ列
  次の表は、 **Command イベント** のイベント カテゴリにある各イベント クラスのデータ列の一覧です。  
  
 **Command イベント** のイベント カテゴリには、次のイベント クラスがあります。  
  
-   [Command Begin クラス](#bkmk_1)  
  
-   [Command End クラス](#bkmk_2)  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
##  <a name="bkmk_1"></a> Command Begin クラスのデータ列  
  
|データ列|説明|  
|-----------------|-----------------|  
|ConnectionID|Command イベントに関連付けられた一意の接続 ID を表します。|  
|TextData|Command イベントに関連付けられたテキスト データを表します。|  
|ServerName|Command イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|CurrentTime|Command イベントの現在の時刻を表します。|  
|DatabaseName|コマンドが実行されているデータベースの名前を表します。|  
|EventSubclass|Command イベント内のイベントのクラスを表します。 値は次のとおりです。<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Other|  
|NTUserName|Command イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|RequestProperties|Command イベントに関連付けられた XML for Analysis (XMLA) 要求プロパティを表します。|  
|SPID|Command イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|StartTime|有効な場合、Command イベントが開始された時刻を表します。|  
|SessionType|操作の原因となったエンティティを表します。|  
|NTDomainName|Object Permission イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|Command イベントに関連付けられた一意のクライアント プロセス ID を表します。|  
  
##  <a name="bkmk_2"></a> Command End クラスのデータ列  
  
|データ列|説明|  
|-----------------|-----------------|  
|ConnectionID|Command イベントに関連付けられた一意の接続 ID を表します。|  
|TextData|Command イベントに関連付けられたテキスト データを表します。|  
|ServerName|Command イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|CurrentTime|Command イベントの現在の時刻を表します。 フィルター選択では、 *YYYY*-*MM*-*DD* および *YYYY*-*MM*-*DD HH*:*MM*:*SS*の形式が使用されます。|  
|DatabaseName|コマンドが実行されているデータベースの名前を表します。|  
|Duration|Command Begin イベントから Command End イベントまでのおおよその時間を表します。|  
|EndTime|Command イベントが終了した時刻を表します。 フィルター選択では、 *YYYY*-*MM*-*DD* および *YYYY*-*MM*-*DD HH*:*MM*:*SS*の形式が使用されます。|  
|EventSubclass|Command イベント内のイベントのクラスを表します。 値は次のとおりです。<br /><br /> 0: Create<br />1: Alter<br />2: Delete<br />3: Process<br />4: DesignAggregations<br />5: WBInsert<br />6: WBUpdate<br />7: WBDelete<br />8: Backup<br />9: Restore<br />10: MergePartitions<br />11: Subscribe<br />12: Batch<br />13: BeginTransaction<br />14: CommitTransaction<br />15: RollbackTransaction<br />16: GetTransactionState<br />17: Cancel<br />18: Synchronize<br />19: Import80MiningModels<br />20: Attach<br />21: Detach<br />22: SetAuthContext<br />23: ImageLoad<br />24: ImageSave<br />10000: Other|  
|NTCanonicalUserName|Command イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|NTUserName|Command イベントに関連付けられた Windows ユーザー アカウントを表します。|  
|SPID|Command イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|StartTime|有効な場合、Command End イベントが開始された時刻を表します。|  
|CPUTime|Command Begin イベントと Command End イベントの間のプロセスにかかった CPU 時間の長さを表します (単位はミリ秒)。|  
|[エラー]|Comand イベントに関連付けられたエラーの番号を表します。|  
|Severity|Command イベントに関連付けられた例外の重大度レベルを表します。 値は次のとおりです。<br /><br /> 0 = 成功<br /><br /> 1 = 情報<br /><br /> 2 = 警告<br /><br /> 3 = エラー|  
|成功|Command イベントの成功または失敗を表します。 値は次のとおりです。<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
|SessionType|Command End イベントに関連付けられた操作が発生する原因となったエンティティを表します。|  
|NTDomainName|Command イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|Command イベントに関連付けられた一意のクライアント プロセス ID を表します。|  
  
## <a name="see-also"></a>参照  
 [コマンド イベントのイベント カテゴリ](command-events-event-category.md)  
  
  
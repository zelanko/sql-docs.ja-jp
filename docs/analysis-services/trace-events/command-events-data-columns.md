---
title: コマンドの Events Data Columns |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 4d9e4884ab8f4fea40be253a55b2ceae1802f3cb
ms.sourcegitcommit: 1aedef909f91dc88dc741748f36eabce3a04b2b1
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/08/2018
---
# <a name="command-events-data-columns"></a>Command イベントのデータ列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  次の表は、 **Command イベント** のイベント カテゴリにある各イベント クラスのデータ列の一覧です。  
  
 **Command イベント** のイベント カテゴリには、次のイベント クラスがあります。  
  
-   [Command Begin クラス](#bkmk_1)  
  
-   [Command End クラス](#bkmk_2)  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
##  <a name="bkmk_1"></a> Command Begin クラスのデータ列  
  
|データ列|Description|  
|-----------------|-----------------|  
|ConnectionID|Command イベントに関連付けられた一意の接続 ID を表します。|  
|TextData|Command イベントに関連付けられたテキスト データを表します。|  
|ServerName|Command イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|CurrentTime|Command イベントの現在の時刻を表します。|  
|DatabaseName|コマンドが実行されているデータベースの名前を表します。|  
|EventSubclass|Command イベント内のイベントのクラスを表します。 サポートされている値は次のとおりです。<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Other|  
|NTUserName|Command イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|RequestProperties|Command イベントに関連付けられた XML for Analysis (XMLA) 要求プロパティを表します。|  
|SPID|Command イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|StartTime|有効な場合、Command イベントが開始された時刻を表します。|  
|SessionType|操作の原因となったエンティティを表します。|  
|NTDomainName|Object Permission イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|Command イベントに関連付けられた一意のクライアント プロセス ID を表します。|  
  
##  <a name="bkmk_2"></a> Command End クラスのデータ列  
  
|データ列|Description|  
|-----------------|-----------------|  
|ConnectionID|Command イベントに関連付けられた一意の接続 ID を表します。|  
|TextData|Command イベントに関連付けられたテキスト データを表します。|  
|ServerName|Command イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|CurrentTime|Command イベントの現在の時刻を表します。 フィルター選択では、 *YYYY*-*MM*-*DD* および *YYYY*-*MM*-*DD HH*:*MM*:*SS*の形式が使用されます。|  
|DatabaseName|コマンドが実行されているデータベースの名前を表します。|  
|Duration|Command Begin イベントから Command End イベントまでのおおよその時間を表します。|  
|EndTime|Command イベントが終了した時刻を表します。 フィルター選択では、 *YYYY*-*MM*-*DD* および *YYYY*-*MM*-*DD HH*:*MM*:*SS*の形式が使用されます。|  
|EventSubclass|Command イベント内のイベントのクラスを表します。 サポートされている値は次のとおりです。<br /><br /> 0: Create<br /><br /> 1: Alter<br /><br /> 2: Delete<br /><br /> 3: Process<br /><br /> 4: DesignAggregations<br /><br /> 5: WBInsert<br /><br /> 6: WBUpdate<br /><br /> 7: WBDelete<br /><br /> 8: Backup<br /><br /> 9: Restore<br /><br /> 10: MergePartitions<br /><br /> 11: Subscribe<br /><br /> 12: Batch<br /><br /> 13: BeginTransaction<br /><br /> 14: CommitTransaction<br /><br /> 15: RollbackTransaction<br /><br /> 16: GetTransactionState<br /><br /> 17: Cancel<br /><br /> 18: Synchronize<br /><br /> 19: Import80MiningModels<br /><br /> 20: Attach<br /><br /> 21: Detach<br /><br /> 22: SetAuthContext<br /><br /> 23: ImageLoad<br /><br /> 24: ImageSave<br /><br /> 10000: Other|  
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
 [コマンドのイベントのイベント カテゴリ](../../analysis-services/trace-events/command-events-event-category.md)  
  
  

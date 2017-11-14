---
title: "進行状況レポートのデータ列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: trace-events
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Progress Reports event category
ms.assetid: d34a6322-e26b-4454-b98f-32307d6956b5
caps.latest.revision: 34
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 18f95a363c72cde1e067bb930d44c65254631ce2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="progress-reports-data-columns"></a>進行状況レポートのデータ列
  進行状況レポート イベント カテゴリには、次のイベント クラスがあります。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|5|Progress Report Begin|進行状況レポートが開始しました。|  
|6|Progress Report End|進行状況レポートが終了しました。|  
|7|Progress Report Current|進行状況レポートを実行中です。|  
|8|Progress Report Error|進行状況レポート エラーです。|  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
## <a name="progress-report-begindata-columns"></a>Progress Report Begin のデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。 有効な **サブクラス ID**と **サブクラス名** の組み合わせは次のとおりです。<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Reported イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|JobID|7|1|Reported イベントに関連付けられたジョブ ID を表します。|  
|SessionType|8|8|Reported イベントに関連付けられたセッションの種類 (イベントを発生させたエンティティ) を表します。 イベントを処理する場合、値は次のとおりです。<br /><br /> 1 = ユーザー<br /><br /> 2 = プロアクティブ キャッシュ<br /><br /> 3 = レイジー処理|  
|ObjectID|11|8|Reported イベントに関連付けられたオブジェクト ID (文字列) を表します。|  
|ObjectType|12|1|オブジェクトの種類が含まれます。|  
|ObjectName|13|8|Reported イベントに関連付けられたオブジェクトの名前を表します。|  
|ObjectPath|14|8|Reported イベントに関連付けられたオブジェクトのオブジェクト パスを表します。パスは、オブジェクトの親を先頭に、コンマで区切った親のリストとして表されます。|  
|ObjectReference|15|8|Reported イベントのオブジェクトの参照を表します。すべての親を XML としてエンコードし、オブジェクトを記述するタグを使用して表します。|  
|ConnectionID|25|1|Reported イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Reported イベントが発生したデータベースの名前を表します。|  
|NTUserName|32|8|Reported イベントに関連付けられた Windows ユーザー アカウントを表します。|  
|NTDomainName|33|8|Reported イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|SessionID|39|8|Reported イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|SPID|41|1|Reported イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XML for Analysis (XMLA) で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Reported イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Reported イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="progress-report-enddata-columns"></a>Progress Report End のデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。 有効な **サブクラス ID**と **サブクラス名** の組み合わせは次のとおりです。<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Reported イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントが終了した時刻を表します。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒) を表します。|  
|CPUTime|6|2|イベントで使用された CPU 時間 (ミリ秒) を表します。|  
|JobID|7|1|Reported イベントに関連付けられたジョブ ID を表します。|  
|SessionType|8|8|Reported イベントに関連付けられたセッションの種類 (イベントを発生させたエンティティ) を表します。 イベントを処理する場合、値は次のとおりです。<br /><br /> 1 = ユーザー<br /><br /> 2 = プロアクティブ キャッシュ<br /><br /> 3 = レイジー処理|  
|ProgressTotal|9|1|Reported イベントの進行状況の合計を表します。|  
|IntegerData|10|1|処理イベントに対して処理される行数の現在のカウントなど、Reported イベントに関連付けられた整数データを表します。|  
|ObjectID|11|8|Reported イベントに関連付けられたオブジェクト ID (文字列) を表します。|  
|ObjectType|12|1|オブジェクトの種類が含まれます。|  
|ObjectName|13|8|Reported イベントに関連付けられたオブジェクトの名前を表します。|  
|ObjectPath|14|8|Reported イベントに関連付けられたオブジェクトのオブジェクト パスを表します。パスは、オブジェクトの親を先頭に、コンマで区切った親のリストとして表されます。|  
|ObjectReference|15|8|Reported イベントのオブジェクトの参照を表します。すべての親を XML としてエンコードし、オブジェクトを記述するタグを使用して表します。|  
|Severity|22|1|Reported イベントに関連付けられた例外の重大度レベルを表します。 値は次のとおりです。<br /><br /> 0 = 成功<br /><br /> 1 = 情報<br /><br /> 2 = 警告<br /><br /> 3 = エラー|  
|Success|23|1|Reported イベントの成功または失敗を表します。 値は次のとおりです。<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
|[エラー]|24|1|特定のイベントのエラー番号が含まれます。|  
|ConnectionID|25|1|Reported イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Reported イベントが発生したデータベースの名前を表します。|  
|NTUserName|32|8|Reported イベントに関連付けられた Windows ユーザー アカウントを表します。|  
|NTDomainName|33|8|Reported イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|SessionID|39|8|Reported イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|Reported イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|1|Reported イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XML for Analysis (XMLA) で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Reported イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Reported イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="progress-report-currentdata-columns"></a>Progress Report Current のデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。 有効な **サブクラス ID**と **サブクラス名** の組み合わせは次のとおりです。<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Reported イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|JobID|7|1|Reported イベントに関連付けられたジョブ ID を表します。|  
|SessionType|8|8|Reported イベントに関連付けられたセッションの種類 (イベントを発生させたエンティティ) を表します。 イベントを処理する場合、値は次のとおりです。<br /><br /> 1 = ユーザー<br /><br /> 2 = プロアクティブ キャッシュ<br /><br /> 3 = レイジー処理|  
|ProgressTotal|9|1|Reported イベントの進行状況の合計を表します。|  
|IntegerData|10|1|処理イベントに対して処理される行数の現在のカウントなど、Reported イベントに関連付けられた整数データを表します。|  
|ObjectID|11|8|Reported イベントに関連付けられたオブジェクト ID (文字列) を表します。|  
|ObjectType|12|1|オブジェクトの種類が含まれます。|  
|ObjectName|13|8|Reported イベントに関連付けられたオブジェクトの名前を表します。|  
|ObjectPath|14|8|Reported イベントに関連付けられたオブジェクトのオブジェクト パスを表します。パスは、オブジェクトの親を先頭に、コンマで区切った親のリストとして表されます。|  
|ObjectReference|15|8|Reported イベントのオブジェクトの参照を表します。すべての親を XML としてエンコードし、オブジェクトを記述するタグを使用して表します。|  
|ConnectionID|25|1|Reported イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Reported イベントが発生したデータベースの名前を表します。|  
|SessionID|39|8|Reported イベントに関連付けられたセッション ID を表します。|  
|SPID|41|1|Reported イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XML for Analysis (XMLA) で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Reported イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Reported イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="progress-report-errordata-columns"></a>Progress Report Error のデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。 有効な **サブクラス ID**と **サブクラス名** の組み合わせは次のとおりです。<br /><br /> 1: **Process**<br /><br /> 2: **Merge**<br /><br /> 3: **Delete**<br /><br /> 4: **DeleteOldAggregations**<br /><br /> 5: **Rebuild**<br /><br /> 6: **Commit**<br /><br /> 7: **Rollback**<br /><br /> 8: **CreateIndexes**<br /><br /> 9: **CreateTable**<br /><br /> 10: **InsertInto**<br /><br /> 11: **Transaction**<br /><br /> 12: **Initialize**<br /><br /> 13: **Discretize**<br /><br /> 14: **Query**<br /><br /> 15: **CreateView**<br /><br /> 16: **WriteData**<br /><br /> 17: **ReadData**<br /><br /> 18: **GroupData**<br /><br /> 19: **GroupDataRecord**<br /><br /> 20: **BuildIndex**<br /><br /> 21: **Aggregate**<br /><br /> 22: **BuildDecode**<br /><br /> 23: **WriteDecode**<br /><br /> 24: **BuildDMDecode**<br /><br /> 25: **ExecuteSQL**<br /><br /> 26: **ExecuteModifiedSQL**<br /><br /> 27: **Connecting**<br /><br /> 28: **BuildAggsAndIndexes**<br /><br /> 29: **MergeAggsOnDisk**<br /><br /> 30: **BuildIndexForRigidAggs**<br /><br /> 31: **BuildIndexForFlexibleAggs**<br /><br /> 32: **WriteAggsAndIndexes**<br /><br /> 33: **WriteSegment**<br /><br /> 34: **DataMiningProgress**<br /><br /> 35: **ReadBufferFullReport**<br /><br /> 36: **ProactiveCacheConversion**<br /><br /> 37: **Backup**<br /><br /> 38: **Restore**<br /><br /> 39: **Synchronize**<br /><br /> 40: **Build Processing Schedule**<br /><br /> 41: **Detach**<br /><br /> 42: **Attach**<br /><br /> 43: **Analyze\Encode Data**<br /><br /> 44: **Compress Segment**<br /><br /> 45: **Write Table Column**<br /><br /> 46: **Relationship Build Prepare**<br /><br /> 47: **Build Relationship Segment**<br /><br /> 48: **Load**<br /><br /> 49: **Metadata Load**<br /><br /> 50: **Data Load**<br /><br /> 51: **Post Load**<br /><br /> 52: **Metadata traversal during Backup**<br /><br /> 53: **VertiPaq**<br /><br /> 54: **Hierarchy processing**<br /><br /> 55: **Switching dictionary**|  
|CurrentTime|2|5|Reported イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントが終了した時刻を表します。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒) を表します。|  
|JobID|7|1|Reported イベントに関連付けられたジョブ ID を表します。|  
|SessionType|8|8|Reported イベントに関連付けられたセッションの種類 (イベントを発生させたエンティティ) を表します。 イベントを処理する場合、値は次のとおりです。<br /><br /> 1 = ユーザー<br /><br /> 2 = プロアクティブ キャッシュ<br /><br /> 3 = レイジー処理|  
|ProgressTotal|9|1|Reported イベントの進行状況の合計を表します。|  
|IntegerData|10|1|処理イベントに対して処理される行数の現在のカウントなど、Reported イベントに関連付けられた整数データを表します。|  
|ObjectID|11|8|Reported イベントに関連付けられたオブジェクト ID (文字列) を表します。|  
|ObjectType|12|1|オブジェクトの種類が含まれます。|  
|ObjectName|13|8|Reported イベントに関連付けられたオブジェクトの名前を表します。|  
|ObjectPath|14|8|Reported イベントに関連付けられたオブジェクトのオブジェクト パスを表します。パスは、オブジェクトの親を先頭に、コンマで区切った親のリストとして表されます。|  
|ObjectReference|15|8|Reported イベントのオブジェクトの参照を表します。すべての親を XML としてエンコードし、オブジェクトを記述するタグを使用して表します。|  
|Severity|22|1|Reported イベントに関連付けられた例外の重大度レベルを表します。 値は次のとおりです。<br /><br /> 0 = 成功<br /><br /> 1 = 情報<br /><br /> 2 = 警告<br /><br /> 3 = エラー|  
|[エラー]|24|1|特定のイベントのエラー番号が含まれます。|  
|ConnectionID|25|1|Reported イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Reported イベントが発生したデータベースの名前を表します。|  
|SessionID|39|8|Reported イベントに関連付けられたセッション ID を表します。|  
|SPID|41|1|Reported イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XML for Analysis (XMLA) で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Reported イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Reported イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="see-also"></a>参照  
 [Progress Reports Event Category](../../analysis-services/trace-events/progress-reports-event-category.md)  
  
  


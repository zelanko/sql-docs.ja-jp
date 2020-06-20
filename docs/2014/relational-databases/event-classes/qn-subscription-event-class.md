---
title: QN:Subscription イベント クラス | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
topic_type:
- apiref
helpviewer_keywords:
- event classes [SQL Server], QN:Subscription
ms.assetid: 4916167e-8541-43b4-900e-ec8e6adcbc34
author: stevestein
ms.author: sstein
ms.openlocfilehash: cebcb693fc6f876c74f375c16de9ad3f09bbe9bd
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85028901"
---
# <a name="qnsubscription-event-class"></a>QN:Subscription イベント クラス
  QN:Subscription イベントでは、通知サブスクリプションに関する情報が報告されます。  
  
## <a name="qnsubscription-event-class-data-columns"></a>QN:Subscription イベント クラスのデータ列  
  
|データ列|種類|説明|列番号|フィルターの適用|  
|-----------------|----------|-----------------|-------------------|----------------|  
|ApplicationName|`nvarchar`|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスへの接続を作成したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|10|はい|  
|ClientProcessID|`int`|クライアント アプリケーションが実行されているプロセスに対し、ホスト コンピューターによって割り当てられた ID。 クライアントでクライアント プロセス ID が指定されると、このデータ列が作成されます。|9|はい|  
|DatabaseID|`int`|USE *database* ステートメントで指定されたデータベースの ID、または特定のインスタンスについて USE *database*ステートメントが実行されていない場合は既定のデータベースの ID となります。 [!INCLUDE[ssSqlProfiler](../../includes/sssqlprofiler-md.md)] では、ServerName データ列がトレースにキャプチャされ、そのサーバーが利用可能な場合、データベースの名前が表示されます。 データベースに対応する値は、DB_ID 関数を使用して特定します。|3|はい|  
|DatabaseName|`nvarchar`|ユーザーのステートメントが実行されているデータベースの名前。|35|はい|  
|EventClass|`int`|イベントの種類 = 199。|27|いいえ|  
|EventSequence|`int`|このイベントのシーケンス番号。|51|いいえ|  
|EventSubClass|`nvarchar`|イベント サブクラスの種類です。各イベント クラスについての詳細な情報を提供します。 この列には次の値が含まれます。<br /><br /> Subscription registered: クエリ通知サブスクリプションがデータベースに正常に登録された日時を示します。<br /><br /> Subscription 巻き戻し: が [!INCLUDE[ssDE](../../includes/ssde-md.md)] 既存のサブスクリプションと正確に一致するサブスクリプション要求を受信する時点を示します。 この場合、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] により、既存のサブスクリプションのタイムアウト値が、新しいサブスクリプション要求で指定されたタイムアウト値に設定されます。<br /><br /> Subscription fired: 通知サブスクリプションによって通知メッセージが生成された日時を示します。<br /><br /> Broker エラーでの起動失敗: エラーが原因で通知メッセージが失敗したことを示します [!INCLUDE[ssSB](../../includes/sssb-md.md)] 。<br /><br /> Broker エラーなしでの起動に失敗しました: 通知メッセージが失敗したが、エラーが原因ではないことを示します。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]<br /><br /> Broker error インターセプト: は、 [!INCLUDE[ssSB](../../includes/sssb-md.md)] クエリ通知で使用されるメッセージ交換でエラーが配信されたことを示します。<br /><br /> サブスクリプションの削除試行: は、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] 期限切れのサブスクリプションを削除してリソースを解放しようとしたことを示します。<br /><br /> Subscription deletion failed: 有効期限が切れたサブスクリプションを削除する試行が失敗したことを示します。 リソースを解放するために、サブスクリプションを削除するスケジュールが [!INCLUDE[ssDE](../../includes/ssde-md.md)] によって自動的に組み直されます。<br /><br /> 破棄されたサブスクリプション: が [!INCLUDE[ssDE](../../includes/ssde-md.md)] 有効期限切れのサブスクリプションを正常に削除したことを示します。|21|はい|  
|GroupID|`int`|SQL トレース イベントが発生したワークロード グループの ID。|66|はい|  
|HostName|`nvarchar`|クライアントが実行しているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。 ホスト名を指定するには、HOST_NAME 関数を使用します。|8|はい|  
|IsSystem|`int`|イベントがシステム プロセスとユーザー プロセスのどちらで発生したか。<br /><br /> 0 = ユーザー<br /><br /> 1 = システム|60|いいえ|  
|LoginName|`nvarchar`|ユーザーのログイン名 ( [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] セキュリティ ログインまたは DOMAIN\Username という形式の Windows ログイン資格情報)。|11|いいえ|  
|LoginSID|`image`|ログイン ユーザーのセキュリティ ID 番号 (SID)。 この情報は、sys.server_principals カタログ ビューで参照できます。 各 SID はサーバーのログインごとに一意です。|41|はい|  
|NTDomainName|`nvarchar`|ユーザーが属している Windows ドメイン。|7|はい|  
|NTUserName|`nvarchar`|このイベントが生成された接続を所有するユーザーの名前。|6|はい|  
|RequestID|`int`|ステートメントを含む要求の ID。|49|はい|  
|ServerName|`nvarchar`|トレースされる [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスの名前。|26|いいえ|  
|SessionLoginName|`nvarchar`|セッションを開始したユーザーのログイン名。 たとえば、アプリケーションから、Login1 を使用して [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に接続し、Login2 でステートメントを実行すると、SessionLoginName には Login1 が表示され、LoginName には Login2 が表示されます。 この列には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインと Windows ログインの両方が表示されます。|64|はい|  
|SPID|`int`|イベントが発生したセッションの ID。|12|はい|  
|StartTime|`datetime`|イベントの開始時刻 (取得できた場合)。|14|はい|  
|TextData|`ntext`|このイベント固有の情報を含む XML ドキュメントを返します。 このドキュメントは、 [SQL Server Query Notification Profiler Event Schema](https://go.microsoft.com/fwlink/?LinkId=63331) ページから入手できる XML スキーマに準拠しています。|1|はい|  
  
  

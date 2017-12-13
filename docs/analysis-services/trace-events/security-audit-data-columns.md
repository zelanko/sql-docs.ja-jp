---
title: "セキュリティ監査のデータ列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Security Audit event category [SQL Server]
ms.assetid: fac1a7f9-5961-4f4b-bb04-847616b505d7
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 5aad698cab42cc52126efed7c7e72b977df97f27
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="security-audit-data-columns"></a>Security Audit のデータ列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Security Audit イベント カテゴリには、次のイベント クラスがあります。  
  
||||  
|-|-|-|  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|1|Audit Login|SQL Server のインスタンスを実行するサーバーへの接続をクライアントが要求したときなど、トレースが開始された後の接続イベントをすべて収集します。|  
|2|Audit Logout|クライアントが切断コマンドを発行したときなど、トレースが開始された後の切断イベントをすべて収集します。|  
|4|Audit Server Starts And Stops|サービスのシャットダウン、起動、一時停止のアクティビティを記録します。|  
|18|Audit Object Permission Event|オブジェクト権限の変更を記録します。|  
|19|Audit Admin Operations Even|サーバーのバックアップ/復元/同期/アタッチ/デタッチ/イメージ読み込み/イメージ保存を記録します。|  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
## <a name="audit-login"></a>Audit Login  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Severity|22|1|例外の重大度レベル。|  
|成功|23|1|1 = 成功。 0 = 失敗 (たとえば、値が 1 の場合は権限チェックの成功を表し、値が 0 の場合は失敗を表します)。|  
|[エラー]|24|1|特定のイベントのエラー番号。|  
|ConnectionID|25|1|一意の接続 ID。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="audit-logout"></a>Audit Logout  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントの終了時刻。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒)。|  
|CPUTime|6|2|イベントに使用された CPU 時間 (ミリ秒単位)。|  
|成功|23|1|1 = 成功。 0 = 失敗 (たとえば、値が 1 の場合は権限チェックの成功を表し、値が 0 の場合は失敗を表します)。|  
|ConnectionID|25|1|一意の接続 ID。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="audit-server-starts-and-stops"></a>Audit Server Starts And Stops  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 1: インスタンスのシャットダウン<br /><br /> 2: インスタンスの起動<br /><br /> 3: インスタンスの一時停止<br /><br /> 4: インスタンスの続行|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Severity|22|1|例外の重大度レベル。|  
|成功|23|1|1 = 成功。 0 = 失敗 (たとえば、値が 1 の場合は権限チェックの成功を表し、値が 0 の場合は失敗を表します)。|  
|[エラー]|24|1|特定のイベントのエラー番号。|  
|TextData|42|9|イベントに関連付けられているテキスト データ。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="audit-object-permission-event"></a>Audit Object Permission Event  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|ObjectID|11|8|オブジェクト ID (文字列です)。|  
|ObjectType|12|1|オブジェクトの種類です。|  
|ObjectName|13|8|オブジェクト名です。|  
|ObjectPath|14|8|オブジェクトのパス。 そのオブジェクトの親から始まり、各親がコンマで区切られた一覧です。|  
|ObjectReference|15|8|オブジェクト参照。 タグを使用してオブジェクトを記述することにより、すべての親の XML としてエンコードされます。|  
|Severity|22|1|例外の重大度レベル。|  
|成功|23|1|1 = 成功。 0 = 失敗 (たとえば、値が 1 の場合は権限チェックの成功を表し、値が 0 の場合は失敗を表します)。|  
|[エラー]|24|1|特定のイベントのエラー番号。|  
|ConnectionID|25|1|一意の接続 ID。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|セッション GUID。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|SPID|41|1|サーバー プロセス ID。 この ID によりユーザー セッションが一意に識別されます。 これは、XML/A で使用されるセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられているテキスト データ。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="audit-admin-operations-event"></a>Audit Admin Operations Even  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 1: **Backup**<br /><br /> 2: **Restore**<br /><br /> 3: **Synchronize**<br /><br /> 4: **Detach**<br /><br /> 5: **Attach**<br /><br /> 6: **ImageLoad**<br /><br /> 7: **ImageSave**|  
|Severity|22|1|例外の重大度レベル。|  
|成功|23|1|1 = 成功。 0 = 失敗 (たとえば、値が 1 の場合は権限チェックの成功を表し、値が 0 の場合は失敗を表します)。|  
|[エラー]|24|1|特定のイベントのエラー番号。|  
|ConnectionID|25|1|一意の接続 ID。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|セッション GUID。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|SPID|41|1|サーバー プロセス ID。 この ID によりユーザー セッションが一意に識別されます。 これは、XML/A で使用されるセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられているテキスト データ。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="see-also"></a>参照  
 [セキュリティ監査イベント カテゴリ](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  

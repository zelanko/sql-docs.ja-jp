---
title: イベントのデータ列をロック |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: trace-events
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 43fe72949d70f06ff8a76e7125af1bcf2d292da9
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="lock-events-data-columns"></a>Lock イベントのデータ列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  Lock イベント カテゴリには、次のイベント クラスがあります。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|50|Deadlock|デッドロック状態にある現在のロックに関する情報。|  
|51|Lock Timeout|最近タイムアウトになったロックに関する情報|  
|52|Lock Acquired|最近取得されたロックに関する情報|  
|53|Lock Released|最近解放されたロックに関する情報|  
|54|Lock Waiting|他のロックを待機しているロックに関する情報|  
  
 次の表は、このイベント クラスのデータ列の一覧です。  
  
## <a name="deadlock"></a>Deadlock  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|TextData|42|9|イベントに関連付けられているテキスト データ。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="lock-timeout"></a>Lock Timeout  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントの終了時刻。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒)。|  
|IntegerData|10|1|整数データ。|  
|ObjectType|12|1|オブジェクトの種類です。|  
|ObjectPath|14|8|オブジェクトのパス。 そのオブジェクトの親から始まり、各親がコンマで区切られた一覧です。|  
|ConnectionID|25|1|一意の接続 ID。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|SessionID|39|8|セッション GUID。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|SPID|41|1|サーバー プロセス ID。 この ID によりユーザー セッションが一意に識別されます。 これは、XML/A で使用されるセッション GUID に直接対応します。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="lock-acquired"></a>Lock Acquired  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|1|一意の接続 ID。|  
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
  
## <a name="lock-released"></a>Lock Released  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|1|一意の接続 ID。|  
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
  
## <a name="lock-waiting"></a>Lock Waiting  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|1|一意の接続 ID。|  
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
 [ロック イベント カテゴリ](../../analysis-services/trace-events/lock-events-category.md)  
  
  

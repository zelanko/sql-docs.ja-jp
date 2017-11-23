---
title: "セッション Events Data Columns |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: trace-events
ms.reviewer: 
ms.suite: sql
ms.technology: analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Session Events event category
ms.assetid: 35853451-6768-4a02-8b8f-81a8ae37a333
caps.latest.revision: "21"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 6692609a547efbe6baa2be620d5405f634e5d5dd
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="session-events-data-columns"></a>Session イベントのデータ列
  Session イベントのイベント カテゴリには、次のイベント クラスが含まれています。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|41|Existing Connection|既存のユーザー接続。|  
|42|Existing Session|既存のセッション。|  
|43|Session Initialize|セッションの初期化。|  
  
 次の表は、このイベント クラスのデータ列の一覧です。  
  
## <a name="existing-connection"></a>Existing Connection  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|1|一意の接続 ID。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SPID|41|1|サーバー プロセス ID。 この ID によりユーザー セッションが一意に識別されます。 これは、XML/A で使用されるセッション GUID に直接対応します。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
  
## <a name="existing-session"></a>Existing Session  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒)。|  
|CPUTime|6|2|イベントに使用された CPU 時間 (ミリ秒単位)。|  
|ConnectionID|25|1|一意の接続 ID。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|SPID|41|1|サーバー プロセス ID。 この ID によりユーザー セッションが一意に識別されます。 これは、XML/A で使用されるセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられているテキスト データ。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
|RequestProperties|45|9|XMLA 要求のプロパティ。|  
  
## <a name="session-initialize"></a>Session Initialize  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|1|一意の接続 ID。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|NTUserName|32|8|Windows のユーザー名。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|ClientHostName|35|8|クライアントが実行されているコンピューターの名前。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|NTCanonicalUserName|40|8|正規の形式のユーザー名。 たとえば、engineering.microsoft.com/software/someone などです。|  
|SPID|41|1|サーバー プロセス ID。 この ID によりユーザー セッションが一意に識別されます。 これは、XML/A で使用されるセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられているテキスト データ。|  
|ServerName|43|8|イベントを生成したサーバーの名前。|  
|RequestProperties|45|9|XMLA 要求のプロパティ。|  
  
## <a name="see-also"></a>「  
 [セキュリティ監査イベント カテゴリ](../../analysis-services/trace-events/security-audit-event-category.md)  
  
  

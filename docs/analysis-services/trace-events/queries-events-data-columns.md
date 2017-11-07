---
title: "イベントのデータ列を照会 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- Queries Events event category
ms.assetid: 28aa7df5-3e1f-4f4f-8a1c-8bbd29d5da13
caps.latest.revision: 33
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 48f2e8dec1939bedda904845dd2e56a237ddc10c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="queries-events-data-columns"></a>Queries イベントのデータ列
  Queries イベントのイベント カテゴリには、次のイベント クラスがあります。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|9|Query Begin|クエリ開始。|  
|10|クエリの終了|クエリ終了。|  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
## <a name="query-begin-classdata-columns"></a>Query Begin クラスのデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 0: MDXQuery<br /><br /> 1: DMXQuery<br /><br /> 2: SQLQuery<br /><br /> 3: DAXQuery|  
|CurrentTime|2|5|イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|1|Query イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|クエリが実行されているデータベースの名前を表します。|  
|NTUserName|32|8|Query イベントに関連付けられた Windows ユーザー名を表します。|  
|NTDomainName|33|8|Query イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前を表します。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|XMLA 要求のセッションの一意識別子 (ID) を表します。|  
|NTCanonicalUserName|40|8|Query イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|1|Query イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Query イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Query イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|RequestParameters|44|9|Query イベントに関連付けられたパラメーター化クエリとコマンドのパラメーターを表します。|  
|RequestProperties|45|9|XMLA 要求のプロパティを表します。|  
  
## <a name="query-end-classdata-columns"></a>Query End クラスのデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|1|1|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 0: MDXQuery<br /><br /> 1: DMXQuery<br /><br /> 2: SQLQuery<br /><br /> 3: DAXQuery|  
|CurrentTime|2|5|イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントが終了した時刻を表します。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントの実行に要した経過時間 (ミリ秒) を表します。|  
|CPUTime|6|2|イベントで使用された CPU 時間 (ミリ秒) を表します。|  
|Severity|22|1|Query イベントに関連付けられた例外の重大度レベルを表します。 値は次のとおりです。<br /><br /> 0 = 成功<br /><br /> 1 = 情報<br /><br /> 2 = 警告<br /><br /> 3 = エラー|  
|Success|23|1|Query イベントの成功または失敗を表します。 値は次のとおりです。<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
|[エラー]|24|1|Query イベントに関連付けられたエラーの番号を表します。|  
|ConnectionID|25|1|Query イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|クエリが実行されているデータベースの名前を表します。|  
|NTUserName|32|8|Query イベントに関連付けられた Windows ユーザー名を表します。|  
|NTDomainName|33|8|Query イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前を表します。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|XMLA 要求のセッションの一意識別子 (ID) を表します。|  
|NTCanonicalUserName|40|8|Query イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|1|Query イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Query イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Query イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="see-also"></a>参照  
 [Queries イベント カテゴリ](../../analysis-services/trace-events/queries-events-category.md)  
  
  


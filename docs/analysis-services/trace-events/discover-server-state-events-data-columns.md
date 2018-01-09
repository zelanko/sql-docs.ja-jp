---
title: "Discover Server State イベントのデータ列 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords: Discover Server State event category
ms.assetid: fbacb187-a4d1-4aa4-be3b-3ddd175f9e19
caps.latest.revision: "32"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 192c9bc97a67f5690619ac0b0ef667e9de6c99d6
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discover-server-state-events-data-columns"></a>Discover Server State イベントのデータ列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Discover Server State イベント カテゴリには、次のイベント クラスがあります。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|33|Server State Discover Begin|サーバー状態検出の開始。|  
|34|Server State Discover Data|サーバー状態検出の応答の内容。|  
|35|Server State Discover End|サーバー状態検出の終了。|  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
## <a name="server-state-discover-begin-classdata-columns"></a>Server State Discover Begin クラスのデータ列  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|EventClass|0|@shouldalert|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|@shouldalert|@shouldalert|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Server State Discover イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|@shouldalert|Server State Discover イベントに関連付けられた一意の接続 ID を表します。|  
|NTUserName|32|8|Server State Discover イベントに関連付けられた Windows ユーザー アカウントを表します。|  
|NTDomainName|33|8|Server State Discover イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|36|@shouldalert|サーバーに対する接続を確立したクライアント アプリケーションのプロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前を表します。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|Server State Discover イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|Server State Discover イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|@shouldalert|Server State Discover イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Server State Discover イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|RequestProperties|45|9|現在の XMLA 要求のプロパティを表します。|  
  
## <a name="server-state-discover-data-classdata-columns"></a>Server State Discover Data クラスのデータ列  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|EventClass|0|@shouldalert|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|@shouldalert|@shouldalert|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Server State Discover イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|@shouldalert|Server State Discover イベントに関連付けられた一意の接続 ID を表します。|  
|SessionID|39|8|Server State Discover イベントに関連付けられたセッション ID を表します。|  
|SPID|41|@shouldalert|Server State Discover イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|検出要求に対するサーバーの応答に関連付けられたテキスト データを表します。|  
|ServerName|43|8|Server State Discover イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="server-state-discover-end-classdata-columns"></a>Server State Discover End クラスのデータ列  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|EventClass|0|@shouldalert|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|@shouldalert|@shouldalert|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 1: **DISCOVER_CONNECTIONS**<br /><br /> 2: **DISCOVER_SESSIONS**<br /><br /> 3: **DISCOVER_TRANSACTIONS**<br /><br /> 6: **DISCOVER_DB_CONNECTIONS**<br /><br /> 7: **DISCOVER_JOBS**<br /><br /> 8: **DISCOVER_LOCKS**<br /><br /> 12: **DISCOVER_PERFORMANCE_COUNTERS**<br /><br /> 13: **DISCOVER_MEMORYUSAGE**<br /><br /> 14: **DISCOVER_JOB_PROGRESS**<br /><br /> 15: **DISCOVER_MEMORYGRANT**|  
|CurrentTime|2|5|Server State Discover イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントが終了した時刻を表します。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒) を表します。|  
|CPUTime|6|2|Server State Discover イベントが要した概算の CPU 時間 (ミリ秒単位) を表します。|  
|ConnectionID|25|@shouldalert|Server State Discover イベントに関連付けられた一意の接続 ID を表します。|  
|NTUserName|32|8|Server State Discover イベントに関連付けられた Windows ユーザー アカウントを表します。|  
|NTDomainName|33|8|Server State Discover イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|36|@shouldalert|XMLA 要求を開始した クライアント アプリケーションのプロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前を表します。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|Server State Discover イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|NTCanonicalUserName|40|8|Server State Discover イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|@shouldalert|Server State Discover イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|検出要求に対するサーバーの応答に関連付けられたテキスト データを表します。|  
|ServerName|43|8|Server State Discover イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="see-also"></a>参照  
 [Discover Server State Event Category](../../analysis-services/trace-events/discover-server-state-event-category.md)  
  
  

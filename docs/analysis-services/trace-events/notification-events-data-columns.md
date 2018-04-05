---
title: 通知 Events Data Columns |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- Notification Events event category
ms.assetid: 0ecf06da-1586-415a-9da8-60d4c634f030
caps.latest.revision: 30
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 901c9935629b584a0eb9c1fa4320fe590efa5e3d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="notification-events-data-columns"></a>Notification イベントのデータ列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Notification イベントのユーザーによって直接発生がないイベントとは[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]です。 たとえば、ユーザーがプロアクティブ キャッシュの基になるテーブルを更新すると、通知が発生します。  
  
 Notifications イベントのイベント カテゴリには、次のイベント クラスがあります。  
  
|**イベント ID**|**イベント名**|**イベントの説明**|  
|------------------|--------------------|---------------------------|  
|39|Notification|通知イベント。|  
|40|User Defined|ユーザー定義イベント。|  
  
 次の表は、このイベント クラスのデータ列の一覧です。  
  
## <a name="notification"></a>Notification  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|@shouldalert|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|@shouldalert|@shouldalert|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。<br /><br /> 次の " **サブクラス ID**:<br />                      **サブクラス名** " のペアが定義されています。<br /><br /> 0: Proactive Caching Begin<br /><br /> 1: Proactive Caching End<br /><br /> 2: Flight Recorder Started<br /><br /> 3: Flight Recorder Stopped<br /><br /> 4: Configuration Properties Updated<br /><br /> 5: SQL Trace<br /><br /> 6: Object Created<br /><br /> 7: Object Deleted<br /><br /> 8: Object Altered<br /><br /> 9: Proactive Caching Polling Begin<br /><br /> 10: Proactive Caching Polling End<br /><br /> 11: Flight Recorder Snapshot Begin<br /><br /> 12: Flight Recorder Snapshot End<br /><br /> 13: Proactive Caching: notifiable object updated<br /><br /> 14: Lazy Processing: start processing<br /><br /> 15: Lazy Processing: processing complete<br /><br /> 16: SessionOpened Event Begin<br /><br /> 17: SessionOpened Event End<br /><br /> 18: SessionClosing Event Begin<br /><br /> 19: SessionClosing Event End<br /><br /> 20: CubeOpened Event Begin<br /><br /> 21: CubeOpened Event End<br /><br /> 22: CubeClosing Event Begin<br /><br /> 23: CubeClosing Event End<br /><br /> 24: Transaction abort requested|  
|CurrentTime|2|5|Notification イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントが終了した時刻を表します。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|イベントにかかった時間 (ミリ秒) を表します。|  
|IntegerData|10|@shouldalert|Notification イベントに関連付けられた整数データを表します。 EventSubclass 列が 8 の場合、値は次のとおりです。<br /><br /> 1 = オブジェクトが作成された<br /><br /> 2 = オブジェクトが削除された<br /><br /> 3 = オブジェクトのプロパティが変更された<br /><br /> 4 = オブジェクトの子のプロパティが変更された<br /><br /> 6 = 子が追加された<br /><br /> 7 = 子が削除された<br /><br /> 8 = オブジェクトが完全に処理された<br /><br /> 9 = オブジェクトが部分的に処理された<br /><br /> 10 = オブジェクトが未処理<br /><br /> 11 = オブジェクトが完全に最適化された<br /><br /> 12 = オブジェクトが部分的に最適化された<br /><br /> 13 = オブジェクトが最適化されていない|  
|ObjectID|11|8|この通知が発行されるオブジェクト ID を表します。これは文字列値です。|  
|ObjectType|12|@shouldalert|Notification イベントに関連付けられたオブジェクトの種類を表します。|  
|ObjectName|13|8|Notification イベントに関連付けられたオブジェクト名を表します。|  
|ObjectPath|14|8|Notification イベントに関連付けられたオブジェクト パスを表します。 パスは、オブジェクトの親を先頭に、コンマで区切った親の一覧として返されます。|  
|ObjectReference|15|8|Progress Report End イベントのオブジェクト参照を表します。 オブジェクト参照は、タグを使用してオブジェクトを記述することにより、すべての親によって XML としてエンコードされます。|  
|ConnectionID|25|@shouldalert|Notification イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Notification イベントが発生したデータベースの名前を表します。|  
|NTUserName|32|8|Notification イベントに関連付けられた Windows ユーザー名を表します。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|SessionID|39|8|Notification イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|Notification イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|@shouldalert|Notification イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Notification イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Notification イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|RequestProperties|45|9|XMLA 要求のプロパティを表します。|  
  
## <a name="user-defined"></a>User Defined  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|@shouldalert|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|@shouldalert|@shouldalert|各イベント クラスに関する追加情報を提供する特定のユーザー イベント サブクラス。|  
|CurrentTime|2|5|Notification イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|IntegerData|10|@shouldalert|特定のユーザー定義イベント情報。|  
|ConnectionID|25|@shouldalert|Notification イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Notification イベントが発生したデータベースの名前を表します。|  
|NTUserName|32|8|Notification イベントに関連付けられた Windows ユーザー名を表します。|  
|NTDomainName|33|8|ユーザーが所属する Windows ドメイン。|  
|SessionID|39|8|Notification イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|Notification イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|@shouldalert|Notification イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Notification イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Notification イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
  
## <a name="see-also"></a>参照  
 [Notification Events Event Category](../../analysis-services/trace-events/notification-events-event-category.md)  
  
  

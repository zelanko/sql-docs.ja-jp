---
title: "Discover イベントのデータ列 |Microsoft ドキュメント"
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
helpviewer_keywords: Discover Events event category
ms.assetid: 10ec598e-5b51-4767-b4f7-42e261d96a40
caps.latest.revision: "29"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: eee3ed0e00d25e255d1cf8de5cc08f0645cdd0dd
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="discover-events-data-columns"></a>Discover イベントのデータ列
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]Discover イベント カテゴリには、次のイベント クラスがあります。  
  
-   Discover Begin クラス  
  
-   Discover End クラス  
  
 次の表は、これらのイベント クラスのデータ列の一覧です。  
  
## <a name="discover-begin-classdata-columns"></a>Discover Begin クラスのデータ列  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|EventClass|0|@shouldalert|イベント クラスを使用してイベントを分類します。|  
|EventSubclass|@shouldalert|@shouldalert|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。  有効な **サブクラス ID**/**サブクラス名** の組み合わせは次のとおりです。<br /><br /> 0: DBSCHEMA_CATALOGS<br /><br /> 1: DBSCHEMA_TABLES<br /><br /> 2: DBSCHEMA_COLUMNS<br /><br /> 3: DBSCHEMA_PROVIDER_TYPES<br /><br /> 4: MDSCHEMA_CUBES<br /><br /> 5: MDSCHEMA_DIMENSIONS<br /><br /> 6: MDSCHEMA_HIERARCHIES<br /><br /> 7: MDSCHEMA_LEVELS<br /><br /> 8: MDSCHEMA_MEASURES<br /><br /> 9: MDSCHEMA_PROPERTIES<br /><br /> 10: MDSCHEMA_MEMBERS<br /><br /> 11: MDSCHEMA_FUNCTIONS<br /><br /> 12: MDSCHEMA_ACTIONS<br /><br /> 13: MDSCHEMA_SETS<br /><br /> 14: DISCOVER_INSTANCES<br /><br /> 15: MDSCHEMA_KPIS<br /><br /> 16: MDSCHEMA_MEASUREGROUPS<br /><br /> 17: MDSCHEMA_COMMANDS<br /><br /> 18: DMSCHEMA_MINING_SERVICES<br /><br /> 19: DMSCHEMA_MINING_SERVICE_PARAMETERS<br /><br /> 20: DMSCHEMA_MINING_FUNCTIONS<br /><br /> 21: DMSCHEMA_MINING_MODEL_CONTENT<br /><br /> 22: DMSCHEMA_MINING_MODEL_XML<br /><br /> 23: DMSCHEMA_MINING_MODELS<br /><br /> 24: DMSCHEMA_MINING_COLUMNS<br /><br /> 25: DISCOVER_DATASOURCES<br /><br /> 26: DISCOVER_PROPERTIES<br /><br /> 27: DISCOVER_SCHEMA_ROWSETS<br /><br /> 28: DISCOVER_ENUMERATORS<br /><br /> 29: DISCOVER_KEYWORDS<br /><br /> 30: DISCOVER_LITERALS<br /><br /> 31: DISCOVER_XML_METADATA<br /><br /> 32: DISCOVER_TRACES<br /><br /> 33: DISCOVER_TRACE_DEFINITION_PROVIDERINFO<br /><br /> 34: DISCOVER_TRACE_COLUMNS<br /><br /> 35: DISCOVER_TRACE_EVENT_CATEGORIES<br /><br /> 36: DMSCHEMA_MINING_STRUCTURES<br /><br /> 37: DMSCHEMA_MINING_STRUCTURE_COLUMNS<br /><br /> 38: DISCOVER_MASTER_KEY<br /><br /> 39: MDSCHEMA_INPUT_DATASOURCES<br /><br /> 40: DISCOVER_LOCATIONS<br /><br /> 41: DISCOVER_PARTITION_DIMENSION_STAT<br /><br /> 42: DISCOVER_PARTITION_STAT<br /><br /> 43: DISCOVER_DIMENSION_STAT<br /><br /> 44: MDSCHEMA_MEASUREGROUP_DIMENSIONS<br /><br /> 49: DISCOVER_XEVENT_TRACE_DEFINITION|  
|CurrentTime|2|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|イベントの開始時刻 (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|ConnectionID|25|@shouldalert|Discover イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|ユーザーのステートメントが実行されているデータベースの名前。|  
|NTUserName|32|8|Discover イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|NTDomainName|33|8|Discover イベントに関連付けられた Windows ドメインを表します。|  
|ClientProcessID|36|@shouldalert|クライアント アプリケーションのプロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|Discover イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|Discover イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|@shouldalert|Discover イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Discover イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|RequestProperties|45|9|Discover イベントに関連付けられた XML for Analysis (XMLA) 要求プロパティを表します。|  
  
## <a name="discover-end-classdata-columns"></a>Discover End クラスのデータ列  
  
|||||  
|-|-|-|-|  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|EventClass|0|@shouldalert|イベント クラスを表します。イベントを分類するために使用されます。|  
|EventSubclass|@shouldalert|@shouldalert|イベント サブクラスにより、各イベント クラスに関する追加情報が提供されます。 有効な **サブクラス ID**/**サブクラス名** の組み合わせは次のとおりです。<br /><br /> 0: DBSCHEMA_CATALOGS<br /><br /> 1: DBSCHEMA_TABLES<br /><br /> 2: DBSCHEMA_COLUMNS<br /><br /> 3: DBSCHEMA_PROVIDER_TYPES<br /><br /> 4: MDSCHEMA_CUBES<br /><br /> 5: MDSCHEMA_DIMENSIONS<br /><br /> 6: MDSCHEMA_HIERARCHIES<br /><br /> 7: MDSCHEMA_LEVELS<br /><br /> 8: MDSCHEMA_MEASURES<br /><br /> 9: MDSCHEMA_PROPERTIES<br /><br /> 10: MDSCHEMA_MEMBERS<br /><br /> 11: MDSCHEMA_FUNCTIONS<br /><br /> 12: MDSCHEMA_ACTIONS<br /><br /> 13: MDSCHEMA_SETS<br /><br /> 14: DISCOVER_INSTANCES<br /><br /> 15: MDSCHEMA_KPIS<br /><br /> 16: MDSCHEMA_MEASUREGROUPS<br /><br /> 17: MDSCHEMA_COMMANDS<br /><br /> 18: DMSCHEMA_MINING_SERVICES<br /><br /> 19: DMSCHEMA_MINING_SERVICE_PARAMETERS<br /><br /> 20: DMSCHEMA_MINING_FUNCTIONS<br /><br /> 21: DMSCHEMA_MINING_MODEL_CONTENT<br /><br /> 22: DMSCHEMA_MINING_MODEL_XML<br /><br /> 23: DMSCHEMA_MINING_MODELS<br /><br /> 24: DMSCHEMA_MINING_COLUMNS<br /><br /> 25: DISCOVER_DATASOURCES<br /><br /> 26: DISCOVER_PROPERTIES<br /><br /> 27: DISCOVER_SCHEMA_ROWSETS<br /><br /> 28: DISCOVER_ENUMERATORS<br /><br /> 29: DISCOVER_KEYWORDS<br /><br /> 30: DISCOVER_LITERALS<br /><br /> 31: DISCOVER_XML_METADATA<br /><br /> 32: DISCOVER_TRACES<br /><br /> 33: DISCOVER_TRACE_DEFINITION_PROVIDERINFO<br /><br /> 34: DISCOVER_TRACE_COLUMNS<br /><br /> 35: DISCOVER_TRACE_EVENT_CATEGORIES<br /><br /> 36: DMSCHEMA_MINING_STRUCTURES<br /><br /> 37: DMSCHEMA_MINING_STRUCTURE_COLUMNS<br /><br /> 38: DISCOVER_MASTER_KEY<br /><br /> 39: MDSCHEMA_INPUT_DATASOURCES<br /><br /> 40: DISCOVER_LOCATIONS<br /><br /> 41: DISCOVER_PARTITION_DIMENSION_STAT<br /><br /> 42: DISCOVER_PARTITION_STAT<br /><br /> 43: DISCOVER_DIMENSION_STAT<br /><br /> 44: MDSCHEMA_MEASUREGROUP_DIMENSIONS<br /><br /> 49: DISCOVER_XEVENT_TRACE_DEFINITION|  
|CurrentTime|2|5|Discover イベントの現在の時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|StartTime|3|5|有効な場合、Discover End イベントが開始された時刻を表します。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|EndTime|4|5|イベントが終了した時刻を表します。 SQL:BatchStarting や SP:Starting などの開始イベント クラスについては、この列に値が格納されません。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|Duration|5|2|Discover イベントが要した概算の時間 (ミリ秒) を表します。|  
|CPUTime|6|2|イベントで使用された CPU 時間 (ミリ秒) を表します。|  
|Severity|22|@shouldalert|例外の重大度レベルを表します。|  
|成功|23|@shouldalert|Discover イベントの成功または失敗を表します。 値は次のとおりです。<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
|[エラー]|24|@shouldalert|Discover イベントに関連付けられたエラーの番号を表します。|  
|ConnectionID|25|@shouldalert|Discover イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Discover イベントが発生したデータベースの名前を表します。|  
|NTUserName|32|8|Object Permission イベントに関連付けられた Windows ユーザー名を表します。|  
|NTDomainName|33|8|Discover イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientProcessID|36|@shouldalert|イベントを開始したアプリケーションのクライアント プロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前を表します。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|Discover イベントに関連付けられたセッション ID を表します。|  
|NTCanonicalUserName|40|8|Object Permission イベントに関連付けられた Windows ユーザー名を表します。 ユーザー名は正規の形式です。 たとえば、engineering.microsoft.com/software/user などです。|  
|SPID|41|@shouldalert|Discover End イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XMLA で使用するセッション GUID に直接対応します。|  
|TextData|42|9|イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Discover イベントが発生した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|RequestProperties|45|9|XMLA 要求のプロパティを表します。|  
  
## <a name="see-also"></a>参照  
 [Discover Events Event Category](../../analysis-services/trace-events/discover-events-event-category.md)  
  
  

---
title: エラーと警告イベントのデータ列 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Errors and Warnings event category [SQL Server]
ms.assetid: f375d303-7aab-4c51-a955-05a2762cc4d1
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 712bb661c95b659b741374312370b352a3a1e2f6
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37298992"
---
# <a name="errors-and-warnings-events-data-columns"></a>Errors and Warnings イベントのデータ列
  セキュリティ監査イベント カテゴリには、次のイベント クラスがあります。  
  
-   Error クラス  
  
 次の表は、このイベント クラスのデータ列の一覧です。  
  
## <a name="error-event-classdata-columns"></a>Error イベント クラスのデータ列  
  
|**列名**|**列 ID**|**列の型**|**列の説明**|  
|---------------------|-------------------|---------------------|----------------------------|  
|EventClass|0|1|イベント クラスを使用してイベントを分類します。|  
|StartTime|3|5|イベントが開始された時刻を表します (取得できた場合)。 フィルター選択を行うには、'YYYY-MM-DD' および 'YYYY-MM-DD HH:MM:SS' の形式である必要があります。|  
|SessionType|8|8|エラーの原因となったエンティティの種類を表します。|  
|Severity|22|1|Error イベントに関連付けられた例外の重大度レベルを表します。 値は次のとおりです。<br /><br /> 0 = 成功<br /><br /> 1 = 情報<br /><br /> 2 = 警告<br /><br /> 3 = エラー|  
|Success|23|1|Error イベントの成功または失敗を表します。 値は次のとおりです。<br /><br /> 0 = 失敗<br /><br /> 1 = 成功|  
|[エラー]|24|1|Error イベントに関連付けられたエラーの番号を表します。|  
|ConnectionID|25|1|Error イベントに関連付けられた一意の接続 ID を表します。|  
|DatabaseName|28|8|Error イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスの名前を表します。|  
|NTUserName|32|8|Error イベントに関連付けられた Windows ユーザー名を表します。|  
|NTDomainName|33|8|Login イベントに関連付けられた Windows ドメイン アカウントを表します。|  
|ClientHostName|35|8|クライアントを実行しているコンピューターの名前を表します。 このデータ列には、クライアントがホスト名を指定している場合にデータが格納されます。|  
|ClientProcessID|36|1|クライアント アプリケーションのプロセス ID を表します。|  
|ApplicationName|37|8|サーバーに対する接続を確立したクライアント アプリケーションの名前を表します。 この列には、プログラムの表示名ではなく、アプリケーションによって渡された値が格納されます。|  
|SessionID|39|8|Error イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XML for Analysis (XMLA) で使用するセッション GUID に直接対応します。|  
|SPID|41|1|Error イベントに関連付けられたユーザー セッションを一意に識別するサーバー プロセス ID (SPID) を表します。 SPID は、XML for Analysis (XMLA) で使用するセッション GUID に直接対応します。|  
|TextData|42|9|Error イベントに関連付けられたテキスト データを表します。|  
|ServerName|43|8|Error イベントが発生した [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスを実行しているサーバーの名前を表します。|  
  
## <a name="see-also"></a>参照  
 [セキュリティ監査イベント カテゴリ](security-audit-event-category.md)  
  
  

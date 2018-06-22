---
title: MSSQLSERVER_9955 | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 9955 (Database Engine error)
ms.assetid: 77f30570-7790-4747-b372-eac71c036e19
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: f3618984aaf0ee8b64ff73ed30c0fe88e5206c2f
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36070503"
---
# <a name="mssqlserver9955"></a>MSSQLSERVER_9955
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|9955|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|FTXT2_MSSEARCHACCESSDENY|  
|メッセージ テキスト|SQL Server は、名前付きパイプ '%ls' を作成して、フルテキスト フィルター デーモンと通信することができませんでした (Windows エラー: %d)。 フィルター デーモン ホスト プロセス用の名前付きパイプが既に存在するか、システムのリソースが不足しているか、またはフィルター デーモン アカウント グループのセキュリティ ID 番号 (SID) の検索に失敗したかのいずれかです。 このエラーを解決するには、実行中のフルテキスト フィルター デーモン プロセスをすべて終了し、必要に応じて、フルテキスト デーモン ランチャー サービス アカウントを再構成してください。|  
  
## <a name="explanation"></a>説明  
 このメッセージは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] がフルテキスト フィルター デーモンと通信するための名前付きパイプを作成できなかったことが原因で表示されます。 フィルター デーモン ホスト プロセス用の名前付きパイプが既に存在するか、システムのリソースが不足しているか、またはフィルター デーモン アカウント グループのセキュリティ ID 番号 (SID) の検索に失敗したかのいずれかです。  
  
## <a name="user-action"></a>ユーザーの操作  
 このエラーを解決するには、実行中のフルテキスト フィルター デーモン プロセスをすべて終了し、必要に応じて SQL Server 構成マネージャーを使用してフルテキスト デーモン ホスト アカウントを再構成します。  
  
## <a name="see-also"></a>参照  
 [SQL Server 構成マネージャー](../sql-server-configuration-manager.md)   
 [フルテキスト フィルター デーモン ランチャーのサービス アカウントの設定](../search/set-the-service-account-for-the-full-text-filter-daemon-launcher.md)   
 [フルテキスト検索](../search/full-text-search.md)  
  
  
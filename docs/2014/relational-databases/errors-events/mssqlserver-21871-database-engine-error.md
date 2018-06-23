---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
caps.latest.revision: 7
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 910fc06aac87eb846c0db76956eb45377fa3ecdb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36077333"
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
    
## <a name="details"></a>詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|21871|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|SQLEngine|  
|シンボル名|SQLErrorNum21871|  
|メッセージ テキスト|データベース %s のパブリッシャー %s がリダイレクトされていません。|  
  
## <a name="explanation"></a>説明  
 `sp_validate_replica_hosts_as_publishers` MSredirected_publishers、識別されたパブリッシャーおよびパブリッシャー データベースのエントリをディストリビューション データベース内のテーブルを確認します。  エントリが見つからない場合、`sp_validate_replica_hosts_as_publishers` はエラー 21871 を返します。  
  
## <a name="user-action"></a>ユーザーの操作  
 `sp_validate_replica_hosts_as_publishers` は、リダイレクトされたパブリッシャーにのみ関連しています。 パブリッシャー データベースが可用性グループのメンバーである場合、ストアド プロシージャ `sp_redirect_publisher` を使用して、パブリッシャーおよびパブリッシャー データベースを可用性グループの可用性グループ リスナー名に関連付けます。  
  
  
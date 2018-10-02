---
title: MSSQLSERVER_21871 | Microsoft Docs
ms.custom: ''
ms.date: 04/04/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: supportability
ms.topic: language-reference
helpviewer_keywords:
- 21871 (Database Engine error)
ms.assetid: d3215378-9282-444f-a18b-00b96fd0133d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 9ff004ff621e97566560efd4af7510025117c8c7
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47629390"
---
# <a name="mssqlserver21871"></a>MSSQLSERVER_21871
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  
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
**sp_validate_replica_hosts_as_publishers** は、ディストリビューション データベースのテーブル MSredirected_publishers で、識別されたパブリッシャーおよびパブリッシャー データベースのエントリがあるかどうかをチェックします。  エントリが見つからない場合、**sp_validate_replica_hosts_as_publishers** はエラー 21871 を返します。  
  
## <a name="user-action"></a>ユーザーの操作  
**sp_validate_replica_hosts_as_publishers** は、リダイレクトされたパブリッシャーにのみ関連しています。 パブリッシャー データベースが可用性グループのメンバーである場合、ストアド プロシージャ **sp_redirect_publisher** を使用して、パブリッシャーおよびパブリッシャー データベースを可用性グループの可用性グループ リスナー名に関連付けます。  
  

---
title: "MSSQL_ENG024070 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "MSSQL_ENG024070 エラー"
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
caps.latest.revision: 14
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 14
---
# MSSQL_ENG024070
    
## メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|24070|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|クライアントには必要な特権がありません。|  
  
## 説明  
 このエラーは、レプリケーションが使用されたかどうかにかかわらず発生する一般エラーです。 一般に、レプリケーション トポロジ内のサーバーでは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーではなく [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス コントロール マネージャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントが変更された場合に、このエラーが発生します。 サービス アカウントの変更後にエージェント ジョブを実行しようとすると、次のようなエラー メッセージが表示されてジョブが失敗する場合があります。  
  
 "ユーザーとして実行: \< UserAccount>です。 レプリケーション-レプリケーション スナップショット サブシステム: エージェント \< AgentName> できませんでした。 ユーザーとして実行: \< UserAccount>します。 クライアントには必要な特権がありません。 ステップは失敗しました。 [SQLSTATE 42000] (エラー 14151)。 ステップは失敗しました。"  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの新しいサービス アカウントに必要な権限を Windows サービス コントロール マネージャーが付与できないので、この問題が発生します。  
  
## ユーザーの操作  
 今後この問題を回避するには、サービス アカウントおよびパスワードを変更する場合に、Windows サービス コントロール マネージャーではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを必ず使用してください。  
  
 この問題を解決するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、サービス アカウントを元のアカウントに戻します。 その後、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、新しいアカウントに変更します。 このとき、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、新しいアカウントを次のセキュリティ グループに追加します。  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 このセキュリティ グループのメンバーになると、レプリケーション エージェント ジョブを実行するために必要な権限が新しいアカウントに付与されます。  
  
## 参照  
 [エラーとイベントのリファレンスと #40 です。レプリケーションと #41 です。](../../relational-databases/replication/errors-and-events-reference-replication.md)   
 [レプリケーションのログインとパスワードの管理](../../relational-databases/replication/security/manage-logins-and-passwords-in-replication.md)   
 [SQL Server 構成マネージャー](../../relational-databases/sql-server-configuration-manager.md)  
  
  
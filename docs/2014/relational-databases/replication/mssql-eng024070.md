---
title: MSSQL_ENG024070 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- MSSQL_ENG024070 error
ms.assetid: 23ac7e00-fab6-429b-9f85-2736a322aa65
caps.latest.revision: 12
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 583603105c6c5ce4a7c24dc09ef50b56ccf77173
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36174734"
---
# <a name="mssqleng024070"></a>MSSQL_ENG024070
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|24070|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|クライアントには必要な特権がありません。|  
  
## <a name="explanation"></a>説明  
 このエラーは、レプリケーションが使用されたかどうかにかかわらず発生する一般エラーです。 一般に、レプリケーション トポロジ内のサーバーでは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーではなく [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows サービス コントロール マネージャーで [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェント サービス アカウントが変更された場合に、このエラーが発生します。 サービス アカウントの変更後にエージェント ジョブを実行しようとすると、次のようなエラー メッセージが表示されてジョブが失敗する場合があります。  
  
 "ユーザーとして実行: \<UserAccount >。 レプリケーション-レプリケーション スナップショット サブシステム: エージェント\<AgentName > できませんでした。 ユーザーとして実行: \<UserAccount >。 クライアントには必要な特権がありません。 ステップは失敗しました。 `[SQLSTATE 42000] (Error 14151)`。 ステップは失敗しました。"  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] エージェントの新しいサービス アカウントに必要な権限を Windows サービス コントロール マネージャーが付与できないので、この問題が発生します。  
  
## <a name="user-action"></a>ユーザーの操作  
 今後この問題を回避するには、サービス アカウントおよびパスワードを変更する場合に、Windows サービス コントロール マネージャーではなく [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを必ず使用してください。  
  
 この問題を解決するには、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、サービス アカウントを元のアカウントに戻します。 その後、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーを使用して、新しいアカウントに変更します。 このとき、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 構成マネージャーは、新しいアカウントを次のセキュリティ グループに追加します。  
  
 SQLServer2008SQLAgentUser$ComputerName$InstanceName  
  
 このセキュリティ グループのメンバーになると、レプリケーション エージェント ジョブを実行するために必要な権限が新しいアカウントに付与されます。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](errors-and-events-reference-replication.md)   
 [レプリケーションのログインとパスワードの管理](security/manage-logins-and-passwords-in-replication.md)   
 [SQL Server 構成マネージャー](../sql-server-configuration-manager.md)  
  
  
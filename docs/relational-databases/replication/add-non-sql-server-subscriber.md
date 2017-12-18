---
title: "SQL Server 以外のサブスクライバーの追加 | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: sql13.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: "11"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 477107d3314678c01a045e874bb88a0a5e996922
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="add-non-sql-server-subscriber"></a>[SQL Server 以外のサブスクライバーの追加]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] レプリケーションでは、Oracle サブスクライバーと IBM DB2 のサブスクライバーのスナップショット パブリケーションおよびトランザクション パブリケーションに対するプッシュ サブスクリプションの作成をサポートします。  
  
## <a name="options"></a>オプション  
 **[追加するサブスクライバーの種類]**  
 Oracle サブスクライバーまたは IBM DB2 サブスクライバーを選択します。 これらのサブスクライバーのサポートの詳細については、「[SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。  
  
 **[データ ソース名]**  
 ネットワーク上のデータベースを探すために使用される名前です。 レプリケーションでは、このウィザードの **[ディストリビューション エージェント セキュリティ]** ページに指定されたログイン、パスワード、および任意の接続オプションをデータ ソース名と組み合わせて、データベースの接続文字列を生成します。  
  
> [!NOTE]  
>  データ ソース名と接続文字列は、ディストリビューション エージェントがサブスクリプションの初期化を試みるまでは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって検証されません。  
  
## <a name="see-also"></a>参照  
 [SQL Server 以外のサブスクライバーのサブスクリプションの作成](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  

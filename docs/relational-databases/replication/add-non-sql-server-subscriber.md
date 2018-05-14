---
title: SQL Server 以外のサブスクライバーの追加 | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: replication
ms.reviewer: ''
ms.suite: sql
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql13.rep.newsubwizard.addnonsqlsubscriber.f1
ms.assetid: 21beeaa0-4b9e-48da-be63-1b9ff14e03d2
caps.latest.revision: 11
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 97688beba720f9bd99d5b621d0ae5abda70be6c3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="add-non-sql-server-subscriber"></a>[SQL Server 以外のサブスクライバーの追加]
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  レプリケーションでは、Oracle サブスクライバーと IBM DB2 のサブスクライバーのスナップショット パブリケーションおよびトランザクション パブリケーションに対するプッシュ サブスクリプションの作成をサポートします。  
  
## <a name="options"></a>および  
 **[追加するサブスクライバーの種類]**  
 Oracle サブスクライバーまたは IBM DB2 サブスクライバーを選択します。 これらのサブスクライバーのサポートの詳細については、「[SQL Server 以外のサブスクライバー](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)」を参照してください。  
  
 **[データ ソース名]**  
 ネットワーク上のデータベースを探すために使用される名前です。 レプリケーションでは、このウィザードの **[ディストリビューション エージェント セキュリティ]** ページに指定されたログイン、パスワード、および任意の接続オプションをデータ ソース名と組み合わせて、データベースの接続文字列を生成します。  
  
> [!NOTE]  
>  データ ソース名と接続文字列は、ディストリビューション エージェントがサブスクリプションの初期化を試みるまでは [!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によって検証されません。  
  
## <a name="see-also"></a>参照  
 [SQL Server 以外のサブスクライバーのサブスクリプションの作成](../../relational-databases/replication/create-a-subscription-for-a-non-sql-server-subscriber.md)   
 [Non-SQL Server Subscribers](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)  
  
  

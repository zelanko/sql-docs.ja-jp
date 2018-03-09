---
title: MSSQL_ENG014157 | Microsoft Docs
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: MSSQL_ENG014157 error
ms.assetid: 1a0890cf-d977-43e0-a2ba-9c5ff1a8f856
caps.latest.revision: "17"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 2e89d3e6bd9929277ac7384124d6130783910a32
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="mssqleng014157"></a>MSSQL_ENG014157
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
## <a name="message-details"></a>メッセージの詳細  
  
|||  
|-|-|  
|製品名|SQL Server|  
|イベント ID|14157|  
|イベント ソース|MSSQLSERVER|  
|コンポーネント|[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]|  
|シンボル名||  
|メッセージ テキスト|サブスクライバー '%s' によって作成された、パブリケーション '%s' に対するサブスクリプションは、有効期限が切れたので削除されました。|  
  
## <a name="explanation"></a>説明  
 サブスクライバーは、パブリケーションの保有期間で指定された時間内にパブリッシャーと同期する必要があります。 サブスクライバーがこの期間内に同期しないと、サブスクリプションの有効期限が切れます。 詳細については、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」を参照してください。  
  
## <a name="user-action"></a>ユーザーの操作  
 サブスクライバーがデータ変更の受信を再び開始するには、サブスクリプションを再作成して初期化する必要があります。  
  
-   サブスクリプションの作成については、「[パブリケーションのサブスクライブ](../../relational-databases/replication/subscribe-to-publications.md)」を参照してください。  
  
-   サブスクリプションの初期化については、「[サブスクリプションの初期化](../../relational-databases/replication/initialize-a-subscription.md)」を参照してください。  
  
 サブスクリプション データベースに、パブリッシャーと同期していない変更が含まれる場合は、 [tablediff Utility](../../tools/tablediff-utility.md) を使用して、パブリケーションとサブスクリプション データベースとの間で異なる行を確認できます。  
  
 サブスクリプションの有効期限が切れないように、パブリケーションの保有期間を長くすることができます。 保有期間に高い値を設定すると、保存されるデータとメタデータの量が増えてパフォーマンスに影響するため注意が必要です。 詳細については、「 [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [エラーとイベントのリファレンス &#40;レプリケーション&#41;](../../relational-databases/replication/errors-and-events-reference-replication.md)  
  
  

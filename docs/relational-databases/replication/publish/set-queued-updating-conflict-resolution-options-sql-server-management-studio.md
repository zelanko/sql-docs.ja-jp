---
title: "キュー更新の競合解決オプションの設定 (SQL Server Management Studio) | Microsoft Docs"
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
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
caps.latest.revision: "34"
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 60b92cb933e8ef7bf5978c289e42f6d986d5c548
ms.sourcegitcommit: dcac30038f2223990cc21775c84cbd4e7bacdc73
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/18/2018
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>キュー更新の競合解決オプションの設定 (SQL Server Management Studio)
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)] **[パブリケーション プロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、キュー更新サブスクリプションをサポートするパブリケーションの競合解決オプションを設定します。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>キュー更新の競合解決オプションを設定するには  
  
1.  **[パブリケーション プロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、**[競合の解決方法]** オプションに対して、次のいずれかの値を選択します。  
  
    -   **[パブリッシャーの変更を保持します]**  
  
    -   **[サブスクライバーの変更を保持します]**  
  
    -   **[サブスクリプションを再初期化します]**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](../../../relational-databases/replication/publish/enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../../../relational-databases/replication/transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  

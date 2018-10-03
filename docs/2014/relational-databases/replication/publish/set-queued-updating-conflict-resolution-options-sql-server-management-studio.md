---
title: キュー更新の競合解決オプションの設定 (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- conflict resolution [SQL Server replication], queued updating subscriptions
- queued updating subscriptions [SQL Server replication]
ms.assetid: bb6b6c71-42c7-421a-a0fa-d5594d27e35d
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 09c7f65a83ca1ec3190a87f4191fd01ed80f9231
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/02/2018
ms.locfileid: "48196282"
---
# <a name="set-queued-updating-conflict-resolution-options-sql-server-management-studio"></a>キュー更新の競合解決オプションの設定 (SQL Server Management Studio)
  **[パブリケーション プロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、キュー更新サブスクリプションをサポートするパブリケーションの競合解決オプションを設定します。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](view-and-modify-publication-properties.md)」を参照してください。  
  
### <a name="to-set-queued-updating-conflict-resolution-options"></a>キュー更新の競合解決オプションを設定するには  
  
1.  **[パブリケーション プロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、**[競合の解決方法]** オプションに対して、次のいずれかの値を選択します。  
  
    -   **[パブリッシャーの変更を保持します]**  
  
    -   **[サブスクライバーの変更を保持します]**  
  
    -   **[サブスクリプションを再初期化します]**  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>参照  
 [トランザクション パブリケーションの更新可能なサブスクリプションの有効化](enable-updating-subscriptions-for-transactional-publications.md)   
 [Queued Updating Conflict Detection and Resolution](../transactional/updatable-subscriptions-queued-updating-conflict-resolution.md)  
  
  

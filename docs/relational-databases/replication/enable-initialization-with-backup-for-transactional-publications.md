---
title: "トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
caps.latest.revision: 30
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 954362e3ef6728df6f497bcb337aa234718cdee8
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="enable-initialization-with-backup-for-transactional-publications"></a>トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする
  バックアップからトランザクション パブリケーションに対してサブスクリプションを初期化するには、パブリケーションを有効にしてバックアップからの初期化を許可し、サブスクリプションの作成時にバックアップ情報を指定します。  
  
-   パブリケーションは、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで有効にします。 このダイアログ ボックスへのアクセスの詳細については、「 [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   バックアップ情報は、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) を使用して指定します。 **sp_addsubscription** で必要とされるパラメーターに関する詳細については、「[トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)」を参照してください。  
  
### <a name="to-enable-initialization-with-a-backup"></a>バックアップを使用した初期化を有効にするには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、**[バックアップ ファイルからの初期化を許可]** オプションに対して **[True]** の値を選択します。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用しないトランザクション サブスクリプションの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  


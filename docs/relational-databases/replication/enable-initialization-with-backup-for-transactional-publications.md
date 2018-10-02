---
title: トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- manual subscription initialization [SQL Server replication]
- subscriptions [SQL Server replication], initializing
- initializing subscriptions [SQL Server replication], without snapshots
- transactional replication, backup and restore
- backups [SQL Server replication], transactional replication
ms.assetid: 9df00514-aa9d-4ac6-9766-d226c9958175
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 3d8e6b14ab673d877bbee1b46b6a3c9c363186b0
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634880"
---
# <a name="enable-initialization-with-backup-for-transactional-publications"></a>トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  バックアップからトランザクション パブリケーションに対してサブスクリプションを初期化するには、パブリケーションを有効にしてバックアップからの初期化を許可し、サブスクリプションの作成時にバックアップ情報を指定します。  
  
-   パブリケーションは、**[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで有効にします。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   バックアップ情報は、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-addsubscription-transact-sql.md) を使用して指定します。 **sp_addsubscription** で必要とされるパラメーターに関する詳細については、「[トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)](../../relational-databases/replication/initialize-a-transactional-subscription-from-a-backup.md)」を参照してください。  
  
### <a name="to-enable-initialization-with-a-backup"></a>バックアップを使用した初期化を有効にするには  
  
1.  **[パブリケーションのプロパティ - \<Publication>]** ダイアログ ボックスの **[サブスクリプション オプション]** ページで、**[バックアップ ファイルからの初期化を許可]** オプションに対して **[True]** の値を選択します。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用しないトランザクション サブスクリプションの初期化](../../relational-databases/replication/initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  

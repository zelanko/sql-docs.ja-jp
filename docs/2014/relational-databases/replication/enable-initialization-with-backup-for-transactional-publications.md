---
title: トランザクションパブリケーションのバックアップによる初期化を有効にする (SQL Server Management Studio) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
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
ms.openlocfilehash: f5e22614c8c4f5250db3966e747b686091512774
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85010717"
---
# <a name="enable-initialization-with-a-backup-for-transactional-publications-sql-server-management-studio"></a>トランザクション パブリケーションに対してバックアップを使用した初期化を有効にする (SQL Server Management Studio)
  バックアップからトランザクション パブリケーションに対してサブスクリプションを初期化するには、パブリケーションを有効にしてバックアップからの初期化を許可し、サブスクリプションの作成時にバックアップ情報を指定します。  
  
-   [**パブリケーションのプロパティ \<Publication> -** ] ダイアログボックスの [**サブスクリプションオプション**] ページでパブリケーションを有効にします。 このダイアログ ボックスへのアクセス方法の詳細については、「[パブリケーション プロパティの表示および変更](publish/view-and-modify-publication-properties.md)」を参照してください。  
  
-   バックアップ情報は、ストアド プロシージャ [sp_addsubscription &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addsubscription-transact-sql) を使用して指定します。 **sp_addsubscription** で必要とされるパラメーターに関する詳細については、「[トランザクション サブスクリプションのバックアップからの初期化 (レプリケーション Transact-SQL プログラミング)](initialize-a-transactional-subscription-from-a-backup.md)」を参照してください。  
  
### <a name="to-enable-initialization-with-a-backup"></a>バックアップを使用した初期化を有効にするには  
  
1.  [**パブリケーションのプロパティ \<Publication> -** ] ダイアログボックスの [**サブスクリプションオプション**] ページで、[**バックアップファイルからの初期化を許可する**] オプションの値として [ **True** ] を選択します。  
  
## <a name="see-also"></a>参照  
 [スナップショットを使用せずにトランザクションサブスクリプションを初期化する](initialize-a-transactional-subscription-without-a-snapshot.md)  
  
  

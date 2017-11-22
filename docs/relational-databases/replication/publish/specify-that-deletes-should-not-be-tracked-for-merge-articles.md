---
title: "マージ アーティクルに対して削除を追跡しないように指定する | Microsoft Docs"
ms.custom: 
ms.date: 03/07/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: replication
ms.reviewer: 
ms.suite: sql
ms.technology: replication
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: "34"
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 405b64985b4a0f38974d85399aaccc08c8797c9c
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles"></a>マージ アーティクルに対して削除を追跡しないように指定する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 既定では、マージ レプリケーションではパブリッシャーとサブスクライバーの DELETE コマンドが同期されます。 マージ レプリケーションを使用すると、行がパブリケーションから削除されても、サブスクリプション データベースでその行を保持できます。その逆の操作も可能です。 新しいアーティクルを作成するときに DELETE コマンドを無視するようにプログラムで指定したり、レプリケーション ストアド プロシージャを使用してこの機能を後で有効にすることができます。  
  
> [!IMPORTANT]  
>  この機能を有効にすると、データが収束しなくなります。つまり、サブスクライバーに存在するデータにパブリッシャーのデータが正確に反映されなくなります。 削除された行を手動で削除するためのメカニズムを独自に実装する必要があります。  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>新しいマージ アーティクルで削除を無視するように指定するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md) を実行します。 **@delete_tracking** の値には **false** を指定します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
    > [!NOTE]  
    >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、両方のアーティクルで **delete_tracking** の値を同じにする必要があります。  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>既存のマージ アーティクルで削除を無視するように指定するには  
  
1.  アーティクルでエラー補正が有効になっているかどうかを確認するために、[sp_helpmergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) を実行して、結果セット内の **delete_tracking** の値を確認します。 値が **0**の場合、削除は既に無視されています。  
  
2.  手順 1. で得た値が **1** だった場合、パブリッシャー側のパブリケーション データベースに対して [sp_changemergearticle &#40;Transact-SQL&#41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) を実行します。 **@property** に **delete_tracking** の値を指定し、**@value** には **false** の値を指定します。  
  
    > [!NOTE]  
    >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、両方のアーティクルで **delete_tracking** の値を同じにする必要があります。  
  
## <a name="see-also"></a>参照  
 [条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  

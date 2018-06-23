---
title: マージ アーティクル (レプリケーション TRANSACT-SQL プログラミング) の削除を追跡しないことを指定して |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- replication
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- TSQL
helpviewer_keywords:
- conditional delete tracking [SQL Server replication]
- merge replication [SQL Server replication], conditional delete tracking
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 7ab89664d39f6dbe8a929b7bd1280f39e97e2414
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075937"
---
# <a name="specify-that-deletes-should-not-be-tracked-for-merge-articles-replication-transact-sql-programming"></a>マージ アーティクルに対して削除を追跡しないように指定する (レプリケーション Transact-SQL プログラミング)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 既定では、マージ レプリケーションではパブリッシャーとサブスクライバーの DELETE コマンドが同期されます。 マージ レプリケーションを使用すると、行がパブリケーションから削除されても、サブスクリプション データベースでその行を保持できます。その逆の操作も可能です。 新しいアーティクルを作成するときに DELETE コマンドを無視するようにプログラムで指定したり、レプリケーション ストアド プロシージャを使用してこの機能を後で有効にすることができます。  
  
> [!IMPORTANT]  
>  この機能を有効にすると、データが収束しなくなります。つまり、サブスクライバーに存在するデータにパブリッシャーのデータが正確に反映されなくなります。 削除された行を手動で削除するためのメカニズムを独自に実装する必要があります。  
  
### <a name="to-specify-that-deletes-be-ignored-for-a-new-merge-article"></a>新しいマージ アーティクルで削除を無視するように指定するには  
  
1.  パブリッシャー側のパブリケーション データベースに対して、[sp_addmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql) を実行します。 値を指定して`false`の **@delete_tracking**です。 詳しくは、「 [アーティクルを定義](define-an-article.md)」をご覧ください。  
  
    > [!NOTE]  
    >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、両方のアーティクルで **delete_tracking** の値を同じにする必要があります。  
  
### <a name="to-specify-that-deletes-be-ignored-for-an-existing-merge-article"></a>既存のマージ アーティクルで削除を無視するように指定するには  
  
1.  アーティクルでエラー補正が有効になっているかどうかを確認するために、[sp_helpmergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql) を実行して、結果セット内の **delete_tracking** の値を確認します。 値が **0**の場合、削除は既に無視されています。  
  
2.  手順 1. で得た値が **1** だった場合、パブリッシャー側のパブリケーション データベースに対して [sp_changemergearticle &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql) を実行します。 値を指定して**delete_tracking**の **@property**の値と`false`の **@value**です。  
  
    > [!NOTE]  
    >  アーティクルのソース テーブルが別のパブリケーションで既にパブリッシュされている場合、両方のアーティクルで **delete_tracking** の値を同じにする必要があります。  
  
## <a name="see-also"></a>参照  
 [条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化](../merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  

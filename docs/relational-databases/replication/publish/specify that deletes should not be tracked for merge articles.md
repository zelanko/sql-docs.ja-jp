---
title: "マージ アーティクルに対して削除を追跡しないように指定する (レプリケーション Transact-SQL プログラミング) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "TSQL"
helpviewer_keywords: 
  - "条件付き削除の追跡 [SQL Server レプリケーション]"
  - "マージ レプリケーション [SQL Server レプリケーション], 条件付き削除の追跡"
ms.assetid: 0fe330ca-5fb5-422e-ad6f-92fb5d6a3b6c
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
---
# マージ アーティクルに対して削除を追跡しないように指定する (レプリケーション Transact-SQL プログラミング)
    
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../../includes/ssnotedepfutureavoid-md.md)]  
  
 既定では、マージ レプリケーションではパブリッシャーとサブスクライバーの DELETE コマンドが同期されます。 マージ レプリケーションを使用すると、行がパブリケーションから削除されても、サブスクリプション データベースでその行を保持できます。その逆の操作も可能です。 新しいアーティクルを作成するときに DELETE コマンドを無視するようにプログラムで指定したり、レプリケーション ストアド プロシージャを使用してこの機能を後で有効にすることができます。  
  
> [!IMPORTANT]  
>  この機能を有効にすると、データが収束しなくなります。つまり、サブスクライバーに存在するデータにパブリッシャーのデータが正確に反映されなくなります。 削除された行を手動で削除するためのメカニズムを独自に実装する必要があります。  
  
### 新しいマージ アーティクルで削除を無視するように指定するには  
  
1.  パブリッシャー、パブリケーション データベースで、次のように実行します。 [sp_addmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-addmergearticle-transact-sql.md)です。 値を指定して **false** の **@delete_tracking**します。 詳しくは、「 [Define an Article](../../../relational-databases/replication/publish/define-an-article.md)」をご覧ください。  
  
    > [!NOTE]  
    >  アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合 **delete_tracking** の両方のアーティクルで同じである必要があります。  
  
### 既存のマージ アーティクルで削除を無視するように指定するには  
  
1.  アーティクルのエラーの補正が有効になっているかどうかかを確認するには、次のように実行します。 [sp_helpmergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-helpmergearticle-transact-sql.md) 値をメモ **delete_tracking** 結果に設定します。 この値が場合 **0**, 、削除は既に無視されています。  
  
2.  手順 1. の値の場合 **1**, 、実行 [sp_changemergearticle & #40 です。Transact SQL と #41;](../../../relational-databases/system-stored-procedures/sp-changemergearticle-transact-sql.md) パブリッシャー、パブリケーション データベースに対して。 値を指定して **delete_tracking** の **@property**, の値との **false** の **@value**します。  
  
    > [!NOTE]  
    >  アーティクルのソース テーブルが別のパブリケーションの値で既にパブリッシュされている場合 **delete_tracking** の両方のアーティクルで同じである必要があります。  
  
## 参照  
 [条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)  
  
  
---
title: "マージ アーティクルの処理順序の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "アーティクル [SQL Server レプリケーション], 処理順序"
  - "マージ レプリケーション [SQL Server レプリケーション], アーティクルの処理順序"
ms.assetid: d151e2c5-cf50-4cb3-a829-8f32455dbd66
caps.latest.revision: 34
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 34
---
# マージ アーティクルの処理順序の指定
  始まる [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../../includes/ssversion2005-md.md)], 、処理のマージ パブリケーションのアーティクルの既定の順序をオーバーライドすることはできます。 これは、たとえば、トリガーを使用して参照整合性を定義し、これらのトリガーを特定の順序で起動する必要がある場合に便利です。  
  
 **アーティクルの処理順序を指定するには**  
  
-   レプリケーション TRANSACT-SQL プログラミング: [指定、処理順序のマージ テーブル アーティクルと #40 です。レプリケーション TRANSACT-SQL プログラミングと #41 です。](../../../relational-databases/replication/publish/specify the processing order of merge table articles.md)  
  
## 処理順序を決定する方法  
 マージ同期の際、既定ではアーティクルがオブジェクト間の依存関係で必要な順序で処理されます。依存関係には、ベース テーブルに対して定義されている宣言参照整合性 (DRI) 制約も含まれます。 同期処理では、テーブルに対する変更が列挙された後で、これらの変更が適用されます。 DRI が定義されておらず、テーブル アーティクル間に結合フィルターか論理レコードが存在する場合、フィルターや論理レコードで必要な順序でアーティクルが処理されます。 記事に関係のない dri では、他のアーティクル結合フィルター、論理レコード、または他の依存関係が内のニックネームに従って処理される、 [sysmergearticles & #40 です。Transact SQL と #41;](../../../relational-databases/system-tables/sysmergearticles-transact-sql.md) システム テーブルです。  
  
 テーブルを含むパブリケーションを検討してください **SalesOrderHeader** と **SalesOrderDetail** 主キー列を含む **SalesOrderID** で、 **SalesOrderHeader** テーブルと、対応する外部キー列 **SalesOrderID** で、 **SalesOrderDetail** テーブルです。 同期時に、マージ レプリケーションにより、外部キーの違反に新しい行を挿入する **SalesOrderHeader** に関連する行を挿入する前に **SalesOrderDetail**します。 同様に、行が削除される **SalesOrderDetail** から、関連する行が削除されるまで **SalesOrderHeader**します。  
  
 ただし、アプリケーションによっては、DRI ではなくデータベース トリガーやアプリケーション レベルで参照整合性が設定されます。 パブリケーションでは前の手順は、DRI ではなく、 **SalesOrderDetail** テーブルに関連付けられている行に確実に insert トリガーを持つ可能性があります、 **SalesOrderHeader** 挿入を許可する前にテーブルが存在します。 **SalesOrderHeader** に関連する行が存在しないように、delete トリガーがあって **SalesOrderDetail** 削除を許可する前にします。 マージ レプリケーションでは、アーティクルの処理順序を決定する際にトリガーは考慮されません。トリガーが起動されないとその結果がどのようになるかがわからないためです。 同様に、アプリケーション レベルで定義された制約も考慮されません。  
  
 トリガーやアプリケーション レベルで参照整合性を保つ場合は、アーティクルの処理順序を指定する必要があります。 トリガーを使用した例では指定すること、 **SalesOrderHeader** 前にテーブルを処理する必要があります **SalesOrderDetail**, 、アーティクルの順序は挿入の順序に基づくためです。 マージ レプリケーションでは、削除の場合、自動的に順序が逆になります。 アーティクルの順序がなくてもマージ レプリケーションは失敗しません。これは、制約違反が発生してもマージ エージェントで処理が継続され、他のアーティクルの処理を終えた後で操作が再試行されるためです。 アーティクルの順序を指定すると、再試行とそれに付随する追加の処理が不要になります。 誤った順序 (詳細レコードがヘッダー レコードの前に処理されるような順序など) を指定すると、マージ レプリケーションは成功するまで処理を再試行します。  
  
## 参照  
 [マージ レプリケーションのアーティクルのオプション](../../../relational-databases/replication/merge/article-options-for-merge-replication.md)   
 [論理レコードによる関連行への変更のグループ化](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)   
 [結合フィルター](../../../relational-databases/replication/merge/join-filters.md)  
  
  
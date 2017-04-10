---
title: "マージ レプリケーションのアーティクルのオプション | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マージ レプリケーション [SQL Server レプリケーション], アーティクル オプション"
  - "アーティクル [SQL Server レプリケーション]、マージ レプリケーション オプション"
ms.assetid: 670abd41-d204-4cd7-a371-7664e603a0ce
caps.latest.revision: 37
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 37
---
# マージ レプリケーションのアーティクルのオプション
  アプリケーションのニーズに合わせてレプリケーション動作をカスタマイズするためのマージ テーブル アーティクルには多くのオプションがあります。 マージ レプリケーションを使用すると、以下のようなことが可能です。  
  
-   行フィルター、結合フィルター、および列フィルターを使用します。 テーブル アーティクルをフィルター選択すると、パブリッシュされるデータのパーティションを作成できます。 詳細については、次を参照してください。 [パブリッシュされたデータのフィルター](../../../relational-databases/replication/publish/filter-published-data.md)します。  
  
-   サブスクライバーでの変更をパブリッシャーにアップロードするかどうかを指定します。 サブスクライバーでデータの一部またはすべてが読み取り専用であるアプリケーションでは、アーティクルをダウンロード専用にすることにより、パフォーマンスが向上します。 詳細については、次を参照してください。 [Download-Only アーティクルを使用したマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-download-only-articles.md)です。  
  
-   1 つまたは複数のアーティクルに対する削除をレプリケーション トリガーおよびシステム テーブルによって追跡しないように指定します。 このオプションは多くのアプリケーション シナリオで役に立ちます。 レプリケートする必要のないバッチ削除を使用するシナリオなどがあります。 詳細については、次を参照してください。 [条件付き削除の追跡によるマージ レプリケーション パフォーマンスの最適化](../../../relational-databases/replication/merge/optimize-merge-replication-performance-with-conditional-delete-tracking.md)します。  
  
-   アーティクルの処理順序を指定し、アプリケーションが要求する順序でアーティクルが処理されるようにします。 詳細については、次を参照してください。 [アーティクルを指定して、処理順序のマージ](../../../relational-databases/replication/merge/specify-the-processing-order-of-merge-articles.md)します。  
  
-   関連するレコードのセットを 1 つの単位として処理するように指定します (既定では、マージ レプリケーションはテーブルへの変更を行単位で処理します)。 詳細については、次を参照してください。 [論理レコードによる関連行へのグループの変更](../../../relational-databases/replication/merge/group-changes-to-related-rows-with-logical-records.md)です。  
  
-   トポロジの複数のノードで同じデータが変更される可能性がある場合に、競合の検出と解決を使用します。 詳細については、次を参照してください。 [検出し、マージ レプリケーションの競合を解決する](../../../relational-databases/replication/merge/detect-and-resolve-merge-replication-conflicts.md)です。  
  
-   制約やトリガーをサブスクライバーにコピーするかどうかなど、スキーマ オプションを指定します。 詳細については、次を参照してください。 [スキーマ オプションの指定](../../../relational-databases/replication/publish/specify-schema-options.md)します。  
  
-   ビジネス ロジック ハンドラーを使用して、同期中に発生するさまざまな状況に対処します。 たとえば、データの変更、競合、エラーに対処します。 詳細については、次を参照してください。 [マージ同期中にビジネス ロジックを実行](../../../relational-databases/replication/merge/execute-business-logic-during-merge-synchronization.md)します。  
  
## 参照  
 [データとデータベース オブジェクトのパブリッシュ](../../../relational-databases/replication/publish/publish-data-and-database-objects.md)  
  
  
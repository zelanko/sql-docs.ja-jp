---
title: "一括インポートで最小ログ記録を行うための前提条件 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "最小ログ [SQL Server]"
  - "ログの一括コピー [SQL Server]"
  - "ログ [SQL Server], 最小ログ記録"
  - "最小ログ記録操作 [SQL Server]"
  - "一括インポート [SQL Server], 最小ログ記録"
ms.assetid: bd1dac6b-6ef8-4735-ad4e-67bb42dc4f66
caps.latest.revision: 48
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 47
---
# 一括インポートで最小ログ記録を行うための前提条件
[!INCLUDE[tsql-appliesto-ss2016-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2016-xxxx-xxxx-xxx-md.md)]

  完全復旧モデルのデータベースの場合、一括インポート中に実行されるすべての行挿入操作が、トランザクション ログに完全に記録されます。 完全復旧モデルを使用する場合、大きなデータをインポートするとトランザクション ログがすぐにいっぱいになってしまいます。 これとは対照的に、単純復旧モデルまたは一括ログ復旧モデルでは、一括インポート操作の最小ログ記録を行うと、一括インポート操作によってログ領域がいっぱいになる可能性が少なくなります。 最小ログ記録は完全ログ記録よりも効率的です。  
  
> [!NOTE]  
>  一括ログ復旧モデルは、大量の一括操作中に完全復旧モデルの代わりとして一時的に使用するためのものです。  
  
## 一括インポート操作の最小ログ記録のためのテーブルの要件  
 最小ログ記録を行うテーブルは、次の条件を満たしている必要があります。  
  
-   テーブルがレプリケート中でないこと。  
  
-   (TABLOCK を使用して) テーブル ロックが指定されていること。 クラスター化列ストア インデックスを持つテーブルでは、最小ログ記録に TABLOCK は不要です。  さらに、バッチ サイズが 102400 以上の圧縮された行グループに対するデータ ロードでのみ最小ログ記録が行われます。  
  
    > [!NOTE]  
    >  最小限のログ記録しか行われない一括インポート操作では、データを挿入してもトランザクション ログに記録されませんが、新しいエクステントがテーブルに割り当てられるたびに、[!INCLUDE[ssDE](../../includes/ssde-md.md)]によりエクステントの割り当てがログに記録されます。  
  
-   テーブルは、メモリ最適化テーブルではありません。  
  
 あるテーブルの最小ログ記録を行うことができるかどうかは、そのテーブルにインデックスがあるかどうか、また、インデックスが存在する場合はテーブルが空かどうかによっても異なります。  
  
-   テーブルにインデックスがない場合、データ ページの最小ログ記録が行われます。  
  
-   テーブルにクラスター化インデックスがなく、非クラスター化インデックスが 1 つ以上ある場合、データ ページは常に最小ログ記録が行われます。 インデックス ページのログがどのように記録されるかは、テーブルが空かどうかにより異なります。  
  
    -   テーブルが空の場合、インデックス ページは最小ログ記録が行われます。  
  
    -   テーブルが空ではない場合、インデックス ページは完全ログ記録が行われます。  
  
        > [!NOTE]  
        >  空のテーブルに複数のバッチのデータを一括インポートする場合、最初のバッチについてはインデックス ページとデータ ページの最小ログ記録が行われますが、2 番目以降のバッチはデータ ページのみの最小ログ記録が行われます。  
  
-   テーブルが空で、クラスター化インデックスがある場合、データ ページとインデックス ページの最小ログ記録が行われます。 これと対照的に、空ではないテーブルに BTree ベースのクラスター化インデックスがある場合、いずれの復旧モデルであってもデータ ページとインデックス ページの完全ログ記録が行われます。 クラスター化列ストア インデックスを持つテーブルでは、バッチ サイズが 102400 以下であるときにテーブルが空であるかどうかに関係なく、圧縮された行グループに対するデータ ロードで常に最小ログ記録が行われます。  
  
    > [!NOTE]  
    >  空の行ストア テーブルにバッチのデータを一括インポートする場合、最初のバッチについてはインデックス ページとデータ ページの最小ログ記録が行われますが、2 番目以降のバッチはデータ ページのみ一括ログ記録が行われます。  
  
> [!NOTE]  
>  トランザクション レプリケーションが有効な場合、BULK INSERT 操作は、一括ログ復旧モデルでも完全にログ記録されます。  
  
##  <a name="RelatedTasks"></a> 関連タスク  
  
-   [データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)  
  
 ![[トップに戻る] リンクで使用される矢印アイコン](../../analysis-services/instances/media/uparrow16x16.png "[トップに戻る] リンクで使用される矢印アイコン") [&#91;先頭に戻る&#93;](#Top)  
  
## 参照  
 [復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)   
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)   
 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)   
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [テーブル ヒント &#40;Transact-SQL&#41;](../Topic/Table%20Hints%20\(Transact-SQL\).md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)  
  
  
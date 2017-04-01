---
title: "データの一括インポートの準備 (SQL Server) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dbe-bulk-import-export"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "一括インポート [SQL Server], 一括インポートについて"
  - "BULK INSERT ステートメント, ガイドライン"
  - "BULK INSERT ステートメント, 制限事項"
  - "bcp ユーティリティ [SQL Server], ガイドライン"
  - "bcp ユーティリティ [SQL Server], 制限事項"
  - "隠し文字"
  - "OPENROWSET 関数, BCP ガイドライン"
ms.assetid: a82ef43c-d006-4c71-bfca-f001a3ba1ba0
caps.latest.revision: 34
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 34
---
# データの一括インポートの準備 (SQL Server)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  データ ファイルのみからデータを一括インポートするには、**bcp** コマンド、BULK INSERT ステートメント、または OPENROWSET(BULK) 関数を使用します。  
  
> [!NOTE]  
>  テキスト ファイル以外のオブジェクトからデータを一括インポートするカスタム アプリケーションを記述することもできます。 メモリ バッファーからデータを一括インポートするには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client (ODBC) アプリケーション プログラミング インターフェイス (API) または OLE DB **IRowsetFastLoad** インターフェイスのいずれかの bcp 拡張機能を使用します。  C# のデータ テーブルからデータを一括インポートするには、ADO.NET 一括コピー API (**SqlBulkCopy**) を使用します。  
  
> [!NOTE]  
>  リモート テーブルへのデータの一括インポートはサポートされていません。  
  
 データ ファイルから [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスにデータを一括インポートするときは、次のガイドラインに従ってください:  
  
-   使用しているユーザー アカウントに必要な権限を取得する。  
  
     **bcp** ユーティリティ、BULK INSERT ステートメント、INSERT ...SELECT * FROM OPENROWSET(BULK...) ステートメントのいずれかで使用するユーザー アカウントには、テーブル操作に必要な権限がテーブルの所有者によって割り当てられている必要があります。 各方法に必要な権限の詳細については、「[bcp ユーティリティ](../../tools/bcp-utility.md)」、「[OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)」、および「[BULK INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)」を参照してください。  
  
-   一括ログ復旧モデルを使用する。  
  
     このガイドラインは、完全復旧モデルを使用するデータベースに関するものです。 一括ログ復旧モデルは、インデックスなしテーブル (*ヒープ*) に対して一括操作を実行する場合に便利です。 一括ログ復旧では行の挿入がログに記録されないため、一括ログ復旧モデルを使用することで、トランザクション ログの領域が不足する状況を回避できます。 一括ログ復旧モデルの詳細については、「[復旧モデル &#40;SQL Server&#41;](../../relational-databases/backup-restore/recovery-models-sql-server.md)」を参照してください。  
  
     一括インポート操作の直前に一括ログ復旧モデルが使用されるようにデータベースを変更することをお勧めします。 一括インポート操作が終了したらすぐに、データベースを完全復旧モデルに戻します。 詳細については、「[データベースの復旧モデルの表示または変更 &#40;SQL Server&#41;](../../relational-databases/backup-restore/view-or-change-the-recovery-model-of-a-database-sql-server.md)」を参照してください。  
  
    > [!NOTE]  
    >  一括インポート操作時のログ記録を最小限にする方法の詳細については、「[一括インポートで最小ログ記録を行うための前提条件](../../relational-databases/import-export/prerequisites-for-minimal-logging-in-bulk-import.md)」を参照してください。  
  
-   データの一括インポート後にバックアップを行う。  
  
     単純復旧モデルを使用するデータベースの場合は、一括インポート操作後に完全バックアップまたは差分バックアップを行うことをお勧めします。 詳細については、「[データベースの完全バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-full-database-backup-sql-server.md)」または「[データベースの差分バックアップの作成 &#40;SQL Server&#41;](../../relational-databases/backup-restore/create-a-differential-database-backup-sql-server.md)」を参照してください。  
  
     一括ログ復旧モデルまたは完全復旧モデルの場合、ログ バックアップで十分です。 詳細については、「[トランザクション ログ バックアップ &#40;SQL Server&#41;](../../relational-databases/backup-restore/transaction-log-backups-sql-server.md)」を参照してください。  
  
-   大量一括インポートのパフォーマンスを向上するために、テーブル インデックスを削除する。  
  
     このガイドラインは、テーブル内の既存のデータ量に比べて大量のデータをインポートするときに関するものです。 この場合、一括インポート操作を実行する前にテーブルからインデックスを削除すると、パフォーマンスが大幅に向上します。  
  
    > [!NOTE]  
    >  テーブル内の既存のデータ量に比べて少量のデータを読み込む場合は、インデックスを削除すると逆効果です。 インデックスの再構築に必要な時間が、一括インポート操作で節約される時間よりも長くなることがあります。  
  
-   データ ファイルにある隠し文字を検索して取り除く。  
  
     多くのユーティリティやテキスト エディターで隠し文字を表示できます。隠し文字は、通常データ ファイルの末尾にあります。 一括インポート操作のとき、ASCII データ ファイルに隠し文字があると、"予期しない NULL が見つかりました" というエラーが発生することがあります。 隠し文字をすべて検索して削除することにより、この問題を回避することができます。  
  
## 参照  
 [bcp ユーティリティを使用した一括データのインポートとエクスポート &#40;SQL Server&#41;](../../relational-databases/import-export/import-and-export-bulk-data-by-using-the-bcp-utility-sql-server.md)   
 [BULK INSERT または OPENROWSET#40;BULK...&#41; を使用した一括データのインポート #40;SQL Server&#41;](../../relational-databases/import-export/import-bulk-data-by-using-bulk-insert-or-openrowset-bulk-sql-server.md)   
 [bcp ユーティリティ](../../tools/bcp-utility.md)   
 [BULK INSERT&#40;Transact-SQL&#41;](../../t-sql/statements/bulk-insert-transact-sql.md)   
 [一括インポートまたは一括エクスポートのデータ形式 &#40;SQL Server&#41;](../../relational-databases/import-export/data-formats-for-bulk-import-or-bulk-export-sql-server.md)   
 [OPENROWSET &#40;Transact-SQL&#41;](../../t-sql/functions/openrowset-transact-sql.md)  
  
  
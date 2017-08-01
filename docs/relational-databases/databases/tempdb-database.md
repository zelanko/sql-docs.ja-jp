---
title: "tempdb データベース | Microsoft Docs"
ms.custom: 
ms.date: 03/04/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- temporary tables [SQL Server], tempdb database
- tempdb database [SQL Server], about tempdb
- temporary stored procedures [SQL Server]
- tempdb database [SQL Server]
ms.assetid: ce4053fb-e37a-4851-b711-8e504059a780
caps.latest.revision: 66
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: HT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 003196d8c30ca45c54750587c03c8d7d6e5a358d
ms.contentlocale: ja-jp
ms.lasthandoff: 07/31/2017

---
# <a name="tempdb-database"></a>tempdb データベース
  **tempdb** システム データベースは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに接続しているすべてのユーザーが使用できるグローバル リソースであり、以下のものを保持するために使用されます。  
  
-   グローバルまたはローカルな一時テーブル、一時ストアド プロシージャ、テーブル変数、カーソルなど、明示的に作成された一時的なユーザー オブジェクト。  
  
-   スプールまたは並べ替えのために中間結果を格納するための作業テーブルなど、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]が作成する内部オブジェクト。  
  
-   行のバージョン管理を伴う READ COMMITTED 分離トランザクションまたはスナップショット分離トランザクションを使用するデータベースで、データ変更トランザクションによって生成される行バージョン。  
  
-   オンライン インデックス操作、複数のアクティブな結果セット (MARS)、AFTER トリガーなどの機能に対してデータ変更トランザクションによって生成される行バージョン。  
  
 **tempdb** 内の操作は、最低限必要な情報だけがログに記録されます。 これにより、トランザクションをロールバックできます。 **が起動されるたびに** tempdb [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] が再作成され、システムが常にデータベースのクリーンなコピーで起動されるようにします。 一時テーブルと一時ストアド プロシージャは、切断時に自動的に削除され、システムのシャットダウン時にアクティブな接続はありません。 そのため、 **tempdb** には、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のあるセッションから別のセッションに保存されるものは一切含まれません。 **tempdb**では、バックアップ操作と復元操作は実行できません。  
  
## <a name="physical-properties-of-tempdb"></a>tempdb の物理プロパティ  
 次の表は、 **tempdb** のデータ ファイルとログ ファイルの初期構成値の一覧です。 これらのファイルのサイズは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のエディションによって多少異なる場合があります。  
  
|ファイル|論理名|物理名|初期サイズ|ファイル拡張|  
|----------|------------------|-------------------|------------------|-----------------|  
|プライマリ データ|tempdev|tempdb.mdf|8 MB|ディスクがいっぱいになるまで 64 MB ずつ自動拡張|  
|セカンダリ データ ファイル*|temp#|tempdb_mssql_#.ndf|8 MB|ディスクがいっぱいになるまで 64 MB ずつ自動拡張|  
|Log|templog|templog.ldf|8 MB|最大 2 TB まで 64 MB ずつ自動拡張|  
  
 \* ファイルの数は、コンピューター上の (論理) コアの数によって異なります。 値はコア数または 8 のどちらか小さい方になります。   
データ ファイルの数の既定値は、 [KB 2154845](https://support.microsoft.com/en-us/kb/2154845/)の一般的なガイドラインに基づいています。  
  
## <a name="performance-improvements-in-tempdb"></a>tempdb でのパフォーマンスの強化  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]では、 **tempdb** のパフォーマンスは以下の方法で強化されています。  
  
-   一時テーブルとテーブル変数をキャッシュできます。 キャッシュを使用することで、一時オブジェクトを削除および作成する操作を非常に高速に実行でき、ページ割り当ての競合が減少します。  
  
-   割り当てページ ラッチ プロトコルが強化されています。 これにより、使用される UP (更新) ラッチの数が減少します。  
  
-   **tempdb** に対するログ記録のオーバーヘッドが削減されています。 これにより、 **tempdb** ログ ファイルでのディスク I/O 帯域幅の消費量が減少します。  
  
-   セットアップによって、新しいインスタンスのインストール中に複数の tempdb データ ファイルが追加されます。 この操作を実行するには、 **[データベース エンジンの構成]** セクションの新しい UI 入力コントロールまたはコマンド ライン パラメーター /SQLTEMPDBFILECOUNT を使用します。 既定では、セットアップ時に、CPU 数または 8 のいずれか小さい方と同数の tempdb ファイルが追加されます。  
  
-   複数の **tempdb** データ ファイルがある場合は、拡張設定に応じて、すべてのファイルが同時に同量ずつ自動拡張されます。  トレース フラグ 1117 は必須ではなくなりました。  
  
-   **tempdb** 内のすべての割り当てで単一エクステントが使用されます。 トレース フラグ 1118 は必須ではなくなりました。  
  
-   プライマリ ファイル グループの場合は、AUTOGROW_ALL_FILES プロパティがオンで、プロパティは変更できません。  
  
### <a name="moving-the-tempdb-data-and-log-files"></a>tempdb のデータ ファイルとログ ファイルの移動  
 **tempdb** データ ファイルとログ ファイルを移動するには、「 [システム データベースの移動](../../relational-databases/databases/move-system-databases.md)」を参照してください。  
  
### <a name="database-options"></a>データベース オプション  
 **tempdb** データベースの各データベース オプションの既定値とそのオプションを変更できるかどうかを次の表に示します。 これらのオプションの現在の設定を表示するには、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md) カタログ ビューを使用します。  
  
|データベース オプション|既定値|変更可否|  
|---------------------|-------------------|---------------------|  
|ALLOW_SNAPSHOT_ISOLATION|OFF|はい|  
|ANSI_NULL_DEFAULT|OFF|はい|  
|ANSI_NULLS|OFF|はい|  
|ANSI_PADDING|OFF|はい|  
|ANSI_WARNINGS|OFF|はい|  
|ARITHABORT|OFF|はい|  
|AUTO_CLOSE|OFF|いいえ|  
|AUTO_CREATE_STATISTICS|ON|はい|  
|AUTO_SHRINK|OFF|いいえ|  
|AUTO_UPDATE_STATISTICS|ON|はい|  
|AUTO_UPDATE_STATISTICS_ASYNC|OFF|はい|  
|CHANGE_TRACKING|OFF|いいえ|  
|CONCAT_NULL_YIELDS_NULL|OFF|はい|  
|CURSOR_CLOSE_ON_COMMIT|OFF|はい|  
|CURSOR_DEFAULT|GLOBAL|はい|  
|データベース可用性オプション|ONLINE<br /><br /> MULTI_USER<br /><br /> READ_WRITE|いいえ<br /><br /> いいえ<br /><br /> いいえ|  
|DATE_CORRELATION_OPTIMIZATION|OFF|はい|  
|DB_CHAINING|ON|いいえ|  
|ENCRYPTION|OFF|いいえ|  
|MIXED_PAGE_ALLOCATION|OFF|いいえ|  
|NUMERIC_ROUNDABORT|OFF|はい|  
|PAGE_VERIFY|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新規インストールの場合は CHECKSUM<br /><br /> [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のアップグレードの場合は NONE|はい|  
|PARAMETERIZATION|SIMPLE|はい|  
|QUOTED_IDENTIFIER|OFF|はい|  
|READ_COMMITTED_SNAPSHOT|OFF|いいえ|  
|RECOVERY|SIMPLE|いいえ|  
|RECURSIVE_TRIGGERS|OFF|はい|  
|Service Broker のオプション|ENABLE_BROKER|はい|  
|TRUSTWORTHY|OFF|いいえ|  
  
 これらのデータベース オプションの説明は、「[ALTER DATABASE の SET オプション &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql-set-options.md)」を参照してください。  
  
## <a name="restrictions"></a>制限  
 **tempdb** データベースでは、次の操作は実行できません。  
  
-   ファイル グループの追加。  
  
-   データベースのバックアップまたは復元。  
  
-   照合順序の変更。 既定の照合順序はサーバーの照合順序です。  
  
-   データベース所有者の変更。 **tempdb** は **sa**が所有します。  
  
-   データベース スナップショットの作成。  
  
-   データベースの削除。  
  
-   データベースからの **guest** ユーザーの削除。  
  
-   変更データ キャプチャの有効化。  
  
-   データベース ミラーリングへの参加。  
  
-   プライマリ ファイル グループ、プライマリ データ ファイル、またはログ ファイルの削除。  
  
-   データベース名またはプライマリ ファイル グループ名の変更。  
  
-   DBCC CHECKALLOC の実行。  
  
-   DBCC CHECKCATALOG の実行。  
  
-   データベースの OFFLINE への設定。  
  
-   データベースまたはプライマリ ファイル グループの READ_ONLY への設定。  
  
## <a name="permissions"></a>権限  
 すべてのユーザーが tempdb 内に一時オブジェクトを作成できます。 ユーザーは追加の権限を付与されない限り、自分で作成したオブジェクトにしかアクセスできません。 ユーザーが tempdb を使用できないように tempdb への接続権限を取り消すことはできますが、一部のルーチン処理で tempdb を使用する必要があるためお勧めしません。  
  
## <a name="related-content"></a>関連コンテンツ  
 [インデックスの SORT_IN_TEMPDB オプション](../../relational-databases/indexes/sort-in-tempdb-option-for-indexes.md)  
  
 [システム データベース](../../relational-databases/databases/system-databases.md)  
  
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)  
  
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)  
  
 [データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)  
  
## <a name="see-also"></a>参照  
 [SQL Server 2005 での tempdb の使用](http://go.microsoft.com/fwlink/?LinkId=81216)  
  
  


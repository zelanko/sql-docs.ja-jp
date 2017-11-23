---
title: "データベースの復元 (並列データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d915bfc1-e392-4a3a-9d94-08682cf3c864
caps.latest.revision: "8"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 4cd72d13f4c953f9b15963655d437709bfc71fa7
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="restore-database-parallel-data-warehouse"></a>データベース (並列データ ウェアハウス) を復元します。
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  復元、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]にデータベースのバックアップからユーザー データベース、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスです。 によって作成されたバックアップからデータベースを復元、 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)][データベースのバックアップ &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md)コマンド。 バックアップを使用して操作と復元操作を災害復旧計画を作成したり、データベースを別の 1 つのアプライアンスに移動します。  
  
> [!NOTE]  
>  Master の復元には、アプライアンスのログイン情報の復元が含まれます。 Master データベースを復元するを使用して、 [master データベース &#40; を復元TRANSACT-SQL と #41 です。](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md)  ページで、 **Configuration Manager**ツールです。 コントロールのノードへのアクセスを持つ管理者は、この操作を実行できます。  
  
 詳細については[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースのバックアップ「のバックアップと復元」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
      Restore the master database  
-- Use the Configuration Manager tool.  
  
Restore a full user database backup.  
RESTORE DATABASE database_name   
    FROM DISK = '\\UNC_path\full_backup_directory'  
[;]  
  
Restore a full user database backup and then a differential backup.  
RESTORE DATABASE database_name  
    FROM DISK = '\\UNC_path\differential_backup_directory'   
    WITH [ ( ] BASE = '\\UNC_path\full_backup_directory' [ ) ]   
[;]  
  
Restore header information for a full or differential user database backup.  
RESTORE HEADERONLY   
    FROM DISK = '\\UNC_path\backup_directory'  
[;]  
```  
  
## <a name="arguments"></a>引数  
 データベースの復元*database_name*  
 ユーザー データベースと呼ばれるデータベースを復元することを指定*database_name*です。 復元されたデータベースでは、バックアップされているソース データベースとは異なる名前を持つことができます。 *database_name*先アプライアンス上のデータベースとして存在することはできません。 詳細について許可されたデータベースの名前に「オブジェクトの名前付け規則」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 ユーザー データベースを復元するデータベースの完全バックアップを復元し、アプライアンスに必要に応じて差分バックアップを復元します。 ユーザー データベースの復元には、復元するデータベース ユーザー、およびデータベース ロールが含まれています。  
  
 FROM DISK = '\\\\*UNC_path*\\*backup_directory*'  
 元のディレクトリとネットワーク パス[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップ ファイルが復元されます。 たとえば、FROM DISK = '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup' です。  
  
 *backup_directory*  
 完全バックアップまたは差分バックアップを格納するディレクトリの名前を指定します。 たとえば、完全または差分バックアップに対して RESTORE HEADERONLY 操作を実行できます。  
  
 *full_backup_directory*  
 完全バックアップを格納するディレクトリの名前を指定します。  
  
 *differential_backup_directory*  
 差分バックアップを格納するディレクトリの名前を指定します。  
  
-   パスとバックアップ ディレクトリは、既に存在する必要があり、完全修飾の汎用名前付け規則 (UNC) パスとして指定する必要があります。  
  
-   バックアップ ディレクトリへのパスがローカル パスにすることはできません、上のいずれかの場所をすることはできません、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスのノードです。  
  
-   バックアップ ディレクトリの名前と UNC パスの最大長は、200 文字です。  
  
-   サーバーまたはホストは、IP アドレスとして指定する必要があります。  
  
 RESTORE HEADERONLY  
 1 人のユーザー データベースのバックアップ ヘッダー情報のみを返すように指定します。 他のフィールドの間では、ヘッダーには、バックアップ、およびバックアップの名前のテキストの説明が含まれます。 バックアップ名は、バックアップ ファイルを格納するディレクトリの名前と同じである必要はありません。  
  
 RESTORE HEADERONLY の結果は、後でパターン化、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] RESTORE HEADERONLY の結果します。 結果は、50 以上の列で使用されるすべて[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。 内の列の詳細については、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] RESTORE HEADERONLY の結果を参照してください[RESTORE HEADERONLY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/restore-statements-headeronly-transact-sql.md).  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **CREATE ANY DATABASE**権限です。  
  
 アクセスして、バックアップ ディレクトリから読み取る権限を持つ Windows アカウントが必要です。 Windows アカウント名とパスワードを格納する必要がありますも[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。  
  
1.  確認する資格情報は既にを使用して[sys.dm_pdw_network_credentials &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md).  
  
2.  を追加または資格情報を更新するには使用[sp_pdw_add_network_credentials (& a) #40 です。SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md).  
  
3.  資格情報を削除する[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を使用して[sp_pdw_remove_network_credentials (& a) #40 です。SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
## <a name="error-handling"></a>エラー処理  
 データベースの復元コマンドは、次の条件下でエラーが得られます。  
  
-   既に復元するデータベースの名前は、ターゲット アプライアンスに存在します。 これを回避するには、一意のデータベースの名前を選択または復元を実行する前に、既存のデータベースを削除します。  
  
-   バックアップ ディレクトリにバックアップ ファイルの無効なセットが存在します。  
  
-   ログイン権限は、データベースを復元するのに十分ではありません。  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップ ファイルが配置されているネットワークの場所に適切なアクセス許可がありませんでした。  
  
-   バックアップ ディレクトリのネットワークの場所が存在しないかは使用できません。  
  
-   コンピューティング ノードまたはノードのコントロールに十分なディスク領域があります。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]復元を開始する前に十分なディスク領域がアプライアンスに存在するとは限りません。 そのため、RESTORE DATABASE ステートメントの実行中にディスク領域不足エラーを生成することができます。 ディスク領域の不足が発生すると[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]復元をロールバックします。  
  
-   データベースが復元されるターゲット アプライアンスには、データベースがバックアップされたソース アプライアンスよりも少ないコンピューティング ノードがあります。  
  
-   トランザクション内から、データベースの復元が試行されます。  
  
## <a name="general-remarks"></a>全般的な解説  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースの復元の成功率を追跡します。 データベースの差分バックアップを復元する前に[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースの完全復元が正常に完了したことを確認します。  
  
 復元後、ユーザー データベースは、データベース互換性レベル 120 があります。 これはすべてのデータベースは元の互換性レベルに関係なく当てはまります。  
  
 **使用コンピューティング ノードの数が多いアプライアンスへの復元**  
実行[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)再配布のトランザクション ログが増加するため、大きい方に小さいアプライアンスからデータベースを復元した後です。  

使用コンピューティング ノードの数が多いアプライアンスにバックアップを復元すると、コンピューティング ノードの数に比例して、割り当てられているデータベースのサイズが大きくなります。  
  
たとえば、60 GB を復元するデータベースは、2 つのノードのアプライアンス (ノードあたり 30 GB) から 6 ノード アプライアンスに[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]6 ノード アプライアンス上 180 GB のデータベース (6 ノード 30 GB を持つ 1 つのノード) を作成します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ソースの構成と一致する 2 つのノードには、最初に、データベースを復元し、6 つのすべてのノードにデータを再分配します。  
  
 再配布後にすべての計算ノードは、実際の低いデータと小さいソース アプライアンス上のすべての計算ノードよりも多くの空き領域に含まれます。 追加の領域を使用して、データベースにデータを追加します。 使用することができます、復元されたデータベースのサイズが大きい場合、必要以上、 [ALTER DATABASE &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/alter-database-parallel-data-warehouse.md)データベース ファイルのサイズを縮小します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 これらの制限事項と制約を使用して、ソース アプライアンスは、アプライアンス元となるデータベースのバックアップが作成され、ターゲット アプライアンスは、データベースを復元するアプライアンスです。  
  
 データベースの復元は自動的に再構築されません統計。  
  
 データベースの復元またはデータベースのバックアップを 1 つだけのステートメントは、アプライアンスの特定の時点で実行できます。 複数のバックアップと復元ステートメントが同時に送信された場合、アプライアンスはキューに配置し、いずれかの処理時、します。  
  
 のみをデータベースのバックアップを復元することができます、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]同数またはソース アプライアンスよりも多くのコンピューティング ノードを持つターゲット アプライアンスです。 ターゲットのアプライアンスは、ソース アプライアンスよりも少ないコンピューティング ノードを持つことはできません。  
  
 アプライアンスを持つ SQL Server 2008 R2 のハードウェアのあるアプライアンスに SQL Server 2012 PDW ハードウェアで作成されたバックアップを復元することはできません。 これは、アプライアンスが最初に SQL Server 2008 R2 PDW ハードウェアで購入した、SQL Server 2012 PDW ソフトウェアを実行している場合であっても true を保持します。  
  
## <a name="locking"></a>ロック  
 データベース オブジェクトの排他ロックを取得します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-restore-examples"></a>A. 単純な復元の例  
 次の例への完全バックアップの復元、`SalesInvoices2013`データベース。 バックアップ ファイルが格納されている、 \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full ディレクトリ。 SalesInvoices2013 データベースにすでに存在するターゲット アプライアンスまたは、このコマンドはエラーで失敗します。  
  
```  
RESTORE DATABASE SalesInvoices2013  
FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="b-restore-a-full-and-differential-backup"></a>B. 完全および差分バックアップを復元します。  
 次の例 SalesInvoices2013 データベースへのフルし、差分バックアップを復元します。  
  
 格納されている完全バックアップからデータベースの完全バックアップを復元します '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full' ディレクトリ。 復元が正常に完了すると、差分バックアップは SalesInvoices2013 データベースに復元します。  差分バックアップが格納されている、'\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff' ディレクトリ。  
  
```  
RESTORE DATABASE SalesInvoices2013  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH BASE = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
  
```  
  
### <a name="c-restoring-the-backup-header"></a>C. バックアップ ヘッダーの復元  
 この例は、データベースのバックアップ ヘッダー情報を復元 '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full' です。 Invoices2013Full バックアップの情報の 1 つの行に、コマンドの結果。  
  
```  
RESTORE HEADERONLY  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
```  
  
 ターゲット復元アプライアンスは、バックアップを復元する前に、ソース バックアップ アプライアンスと互換性のあるかどうかを確認したり、バックアップの内容を確認するヘッダー情報を使用できます。  
  
## <a name="see-also"></a>参照  
 [データベースのバックアップ &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md)  
  
  

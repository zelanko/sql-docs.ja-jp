---
title: RESTORE DATABASE (Parallel Data Warehouse) | Microsoft Docs
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: d915bfc1-e392-4a3a-9d94-08682cf3c864
caps.latest.revision: 8
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 0fb3c753e4bde29eb9b5cbb5f287fc18d03a117a
ms.sourcegitcommit: e77197ec6935e15e2260a7a44587e8054745d5c2
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2018
ms.locfileid: "37969274"
---
# <a name="restore-database-parallel-data-warehouse"></a>RESTORE DATABASE (Parallel Data Warehouse)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  データベース バックアップから [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] アプライアンスに、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ユーザー データベースを復元します。 データベースは、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)][BACKUP DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md) コマンドによって以前に作成されたバックアップから復元されます。 バックアップ操作および復元操作を使用してディザスター リカバリー計画を作成したり、アプライアンス間でデータベースを移動したりします。  
  
> [!NOTE]  
>  master データベースの復元には、アプライアンスのログイン情報の復元が含まれます。 master データベースを復元するには、**Configuration Manager** ツールの [[master データベースの復元 (Transact-SQL)]](../../relational-databases/backup-restore/restore-the-master-database-transact-sql.md) ページを使用します。 制御ノードへのアクセス許可を持つ管理者は、この操作を実行することができます。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベース バックアップの詳細については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の 「バックアップと復元」に関するセクションをご覧ください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 RESTORE DATABASE *database_name*  
 ユーザー データベースを *database_name* と呼ばれるデータベースに復元するように指定します。 復元するデータベースには、バックアップされているソース データベースと異なる名前を付けることができます。 *database_name* は、復元先のアプライアンス上にデータベースとしてまだ存在することができません。 使用可能なデータベース名の詳細については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]の「オブジェクトの名前付け規則」を参照してください。  
  
 ユーザー データベースを復元すると、アプライアンスに対して、データベースの完全バックアップが復元され、その後、必要応じて差分バックアップが復元されます。 ユーザー データベースの復元には、データベース ユーザーとデータベース ロールの復元が含まれます。  
  
 FROM DISK = '\\\\*UNC_path*\\*backup_directory*'  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] によって復元されるバックアップ ファイルが置かれているネットワーク パスとディレクトリ。 たとえば、FROM DISK = '\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup'。  
  
 *backup_directory*  
 完全バックアップまたは差分バックアップが格納されているディレクトリの名前を指定します。 たとえば、完全バックアップまたは差分バックアップに対して RESTORE HEADERONLY 操作を実行することができます。  
  
 *full_backup_directory*  
 完全バックアップが格納されたディレクトリの名前を指定します。  
  
 *differential_backup_directory*  
 差分バックアップが格納されたディレクトリの名前を指定します。  
  
-   パスとバックアップ ディレクトリが既に存在し、これらが完全に修飾された汎用名前付け規則 (UNC) パスとして指定されている必要があります。  
  
-   バックアップ ディレクトリのパスにはローカル パスを指定できません。[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] アプライアンス ノード上の場所とすることもできません。  
  
-   UNC パスとバックアップ ディレクトリ名の最大長は 200 文字です。  
  
-   サーバーまたはホストは IP アドレスとして指定する必要があります。  
  
 RESTORE HEADERONLY  
 ユーザー データベースの 1 つのバックアップに関するヘッダー情報のみを返すように指定します。 特に、ヘッダー フィールドにはバックアップに関するテキストの説明と、バックアップの名前が含まれます。 バックアップ名は、バックアップ ファイルを格納するディレクトリの名前と同じである必要はありません。  
  
 RESTORE HEADERONLY の結果は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] RESTORE HEADERONLY の結果の後でパターン化されます。 結果には 50 を超える列が含まれます。ただし、全部が [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] で使用されるわけではありません。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] RESTORE HEADERONLY の結果に含まれる列の説明については、[RESTORE HEADERONLY &#40;TRANSACT-SQL&#41;](../../t-sql/statements/restore-statements-headeronly-transact-sql.md) を参照してください。  
  
## <a name="permissions"></a>アクセス許可  
 **CREATE ANY DATABASE** アクセス許可が必要です。  
  
 バックアップ ディレクトリにアクセスし、そこから読み取るための権限を有する Windows アカウントが必要です。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] に Windows アカウント名とパスワードを保存する必要もあります。  
  
1.  資格情報が既にあることを確認するには、[sys.dm_pdw_network_credentials &#40;TRANSACT-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) を使用します。  
  
2.  資格情報を追加または更新するには、[sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) を使用してください。  
  
3.  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] からネットワーク資格情報を削除するには、[sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md) を使用してください。  
  
## <a name="error-handling"></a>エラー処理  
 RESTORE DATABASE を実行すると、次の条件下でエラーが発生します。  
  
-   復元するデータベースの名前が、ターゲット アプライアンス上に既に存在しています。 名前の衝突を回避するには、一意のデータベース名を選択するか、または復元を実行する前に既存のデータベースを削除します。  
  
-   バックアップ ディレクトリ内に無効なバックアップ ファイル セットが存在します。  
  
-   データベースを復元するにはログイン権限が不十分です。  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] には、バックアップが保存されているネットワーク上の場所にアクセスする適切な権限がありません。  
  
-   バックアップ ディレクトリ用のネットワーク上の場所が存在しないか、その場所が使用できません。  
  
-   計算ノードまたは制御コントロール上のディスク領域が不足しています。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] では、復元を開始する前に、アプライアンス上に十分なディスク領域が存在するかどうかを確認しません。 そのため、RESTORE DATABASE ステートメントの実行中にディスク領域不足エラーが生成される可能性があります。 ディスク領域の不足が発生すると、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は復元をロールバックします。  
  
-   データベースを復元するターゲット アプライアンスにある計算ノードの数が、データベースがバックアップされたソース アプライアンス上の計算ノードの数と比べて少なくなっています。  
  
-   データベースの復元は、トランザクション内から試行されます。  
  
## <a name="general-remarks"></a>全般的な解説  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は、データベースの復元が成功したかどうかを追跡します。 データベースの差分バックアップを復元する前に、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は、データベースの完全復元が正常に完了していることを確認します。  
  
 復元後、ユーザー データベースのデータベース互換性レベルは 120 となります。 これは、元の互換性レベルに関係なく、すべてのデータベースに当てはまります。  
  
 **より多くの計算ノードを備えたアプライアンスへの復元**  
小型のアプライアンスから大型のアプライアンスにデータベースを復元すると、再割り当てによってトランザクション ログが増えるため、[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) を実行します。  

より多くの計算ノードを備えたアプライアンスにバックアップを復元すると、計算ノードの数に比例して、割り当てられるデータベースのサイズが大きくなります。  
  
たとえば、2 つのノードを備えたアプライアンス (ノードあたり 30 GB) から 6 つのノードを備えたアプライアンスに 60 GB のデータベースを復元する場合、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は、6 つのノードを備えたアプライアンス上に 180 GB のデータベース (6 ノード、ノードあたり 30 GB) を作成します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] はまず 2 つのノードに復元することでソースの構成と一致させ、次に 6 つのノードすべてにデータを再割り当てします。  
  
 再割り当て後の各計算ノードでは、小さい方のソース アプライアンス上の各計算ノードと比べて、含まれる実際のデータが少なくなり、空き領域が大きくなります。 追加の領域を使用して、データベースにデータを追加します。 復元されたデータベースのサイズが必要以上に大きい場合は、[ALTER DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/alter-database-transact-sql.md?&tabs=sqlpdw) を使用してデータベース ファイルのサイズを縮小することができます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 以下の制限事項と制約において、ソース アプライアンスとはデータベースのバックアップが作成されたアプライアンスであり、ターゲット アプライアンスとはデータベースの復元先のアプライアンスです。  
  
 データベースの復元によって、統計は自動的に再構築されません。  
  
 アプライアンス上で一度に実行できる RESTORE DATABASE ステートメントまたは BACKUP DATABASE ステートメントは 1 つだけです。 複数のバックアップ ステートメントと復元ステートメントが同時に送信された場合、アプライアンスはそれらをキューに配置し、一度に 1 つずつ処理します。  
  
 データベースのバックアップの復元先は、ソース アプライアンスと同数またはそれより多くのノードを備える [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] ターゲット アプライアンスである必要があります。 ソース アプライアンスより計算ノード数が少ないアプライアンスをターゲットにすることはできません。  
  
 SQL Server 2012 PDW のハードウェアを備えるアプライアンスで作成したバックアップを、SQL Server 2008 R2 のハードウェアを備えるアプライアンスに復元することはできません。 この制約は、当初 SQL Server 2008 R2 PDW のハードウェアを備えたアプライアンスを購入し、今はこのアプライアンスで SQL Server 2012 PDW のソフトウェアを実行している場合であっても適用されます。  
  
## <a name="locking"></a>ロック  
 DATABASE オブジェクトに対して排他的ロックを実行します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-simple-restore-examples"></a>A. RESTORE の単純な例  
 次の例では、完全バックアップを `SalesInvoices2013` データベースに復元します。 バックアップ ファイルは、\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full ディレクトリに格納されています。 SalesInvoices2013 データベースはターゲット アプライアンス上に存在することがまだ許可されていないので、このコマンドを実行しても失敗しエラーが返されます。  
  
```  
RESTORE DATABASE SalesInvoices2013  
FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="b-restore-a-full-and-differential-backup"></a>B. 完全および差分バックアップを復元します。  
 次の例では、完全バックアップを復元してから、差分バックアップを SalesInvoices2013 データベースに復元します。  
  
 データベースの完全バックアップは、'\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full' ディレクトリに格納されている完全バックアップから復元されます。 この復元が正常に完了すると、差分バックアップが SalesInvoices2013 データベースに復元されます。  差分バックアップは、'\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff' ディレクトリに格納されています。  
  
```  
RESTORE DATABASE SalesInvoices2013  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH BASE = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
  
```  
  
### <a name="c-restoring-the-backup-header"></a>C. バックアップ ヘッダーの復元  
 この例では、データベース バックアップ '\\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full' のヘッダー情報を復元します。 コマンドを実行すると、Invoices2013Full バックアップに関する情報を含む行が 1 つ生成されます。  
  
```  
RESTORE HEADERONLY  
    FROM DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full'  
[;]  
```  
  
 ヘッダー情報を使用すれば、バックアップの内容を確認したり、バックアップの復元を試みる前にターゲット復元アプライアンスが、ソース バックアップ アプライアンスと互換性があるかどうかを確認したりすることができます。  
  
## <a name="see-also"></a>参照  
 [BACKUP DATABASE &#40;Parallel Data Warehouse&#41;](../../t-sql/statements/backup-database-parallel-data-warehouse.md)  
  
  

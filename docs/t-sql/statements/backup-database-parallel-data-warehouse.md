---
title: BACKUP DATABASE (並列データ ウェアハウス) | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: pdw
ms.reviewer: ''
ms.suite: sql
ms.technology: t-sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: 73c8d465-b36b-4727-b9f3-368e98677c64
caps.latest.revision: 11
author: CarlRabeler
ms.author: carlrab
manager: craigg
monikerRange: '>= aps-pdw-2016 || = sqlallproducts-allversions'
ms.openlocfilehash: 41ad9d69b045a149bf6adad58f16f881ccc5d98e
ms.sourcegitcommit: 05e18a1e80e61d9ffe28b14fb070728b67b98c7d
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/04/2018
ms.locfileid: "37783483"
---
# <a name="backup-database-parallel-data-warehouse"></a>BACKUP DATABASE (並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベースのバックアップを作成し、アプライアンスから離れた、ユーザーが指定したネットワーク上の場所に保存します。 ディザスター リカバリーには、あるいはアプライアンス間でデータベースをコピーするには、このステートメントと [RESTORE DATABASE &#40;並列データ ウェアハウス&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md) を使用してください。  
  
 **開始する前に**、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の「Acquire and Configure a Backup Server」 (バックアップ サーバーを入手し、構成する) をご覧ください。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] には、2 種類のバックアップがあります。 *データベースの完全バックアップ*では、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベース全体をバックアップします。 *差分バックアップ*では、最後の完全バックアップ以降の変更のみをバックアップします。 ユーザー データベースのバックアップには、データベース ユーザーとデータベース ロールが含まれます。 master データベースのバックアップにはログインが含まれます。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] データベース バックアップの詳細については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の「Backup and Restore」 (バックアップと復元) をご覧ください。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則 &#40;Transact-SQL&#41;](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
      Create a full backup of a user database or the master database.  
BACKUP DATABASE database_name  
    TO DISK = '\\UNC_path\backup_directory'  
    [ WITH [ ( ]  <with_options> [ ,...n ]  [ ) ] ]  
[;]  
  
Create a differential backup of a user database.  
BACKUP DATABASE database_name  
    TO DISK = '\\UNC_path\backup_directory'  
    WITH [ ( ] DIFFERENTIAL   
    [ , <with_options> [ ,...n ] [ ) ]  
[;]  
  
<with_options> ::=  
    DESCRIPTION = 'text'  
    | NAME = 'backup_name'  
  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 バックアップを作成するデータベースの名前。 データベースには、master データベースかユーザー データベースを指定できます。  
  
 TO DISK = '\\\\*UNC_path*\\*backup_directory*'  
 ネットワーク パスとディレクトリ。ここに [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] によってバックアップ ファイルが書き込まれます。 たとえば、'\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup' です。  
  
-   バックアップ ディレクトリ名のパスが既に存在し、完全修飾 UNC (汎用名前付け規則) パスとして指定されている必要があります。  
  
-   バックアップ ディレクトリ *backup_directory* は、バックアップ コマンドの実行前に存在することはできません。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] によってバックアップ ディレクトリが作成されます。  
  
-   バックアップ ディレクトリのパスにはローカル パスを指定できません。[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] アプライアンス ノード上の場所にすることもできません。  
  
-   UNC パスとバックアップ ディレクトリ名の最大長は 200 文字です。  
  
-   サーバーまたはホストは IP アドレスとして指定する必要があります。  これはホストまたはサーバー名として指定できません。  
  
 DESCRIPTION = **'***text***'**  
 バックアップの説明テキストを指定します。 テキストの最大長は 255 文字です。  
  
 説明はメタデータに格納されます。バックアップ ヘッダーが RESTORE HEADERONLY で復元されるときに表示されます。  
  
 NAME = **'***backup _name***'**  
 バックアップの名前を指定します。 バックアップ名には、データベース名とは異なる名前を指定できます。  
  
-   名前の長さは最大 128 文字です。  
  
-   パスを含めることはできません。  
  
-   先頭の文字はアルファベット、数字、アンダースコア (_) のいずれかにする必要があります。 特殊文字としてはアンダースコア (\_)、ハイフン (-)、スペース ( ) が許可されます。 バックアップ名の最後の文字をスペースにすることはできません。  
  
-   指定の場所に *backup_name* が既に存在する場合、ステートメントは失敗します。  
  
 この名前はメタデータに格納されます。バックアップ ヘッダーが RESTORE HEADERONLY で復元されるときに表示されます。  
  
 DIFFERENTIAL  
 ユーザー データベースの差分バックアップを実行します。 省略した場合、データベースの完全バックアップが選択されます。 差分バックアップの名前は、完全バックアップの名前に一致する必要がありません。 差分バックアップとそれに対応する完全バックアップを追跡記録するために、同じ名前に 'full' または 'diff' を付けることを検討してください。  
  
 例 :  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerFull';`  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerDiff' WITH DIFFERENTIAL;`  
  
## <a name="permissions"></a>アクセス許可  
 **BACKUP DATABASE** 許可または **db_backupoperator** 固定データベース ロールのメンバーシップが必要です。 master データベースは、**db_backupoperator** 固定データベース ロールに追加された標準ユーザーではバックアップできません。 master データベースをバックアップできるのは、**sa**、ファブリック管理者、または **sysadmin** 固定サーバー ロールのメンバーに限られます。  
  
 バックアップ ディレクトリにアクセスし、作成や書き込みを行うことが許可された Windows アカウントが必要です。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] に Windows アカウント名とパスワードを保存する必要もあります。 これらのネットワーク資格情報を [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] に追加するには、[sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) ストアド プロシージャを使用します。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] の資格情報を管理する方法については、「[セキュリティ](#Security)」セクションをご覧ください。  
  
## <a name="error-handling"></a>エラー処理  
 次の条件下での BACKUP DATABASE エラー:  
  
-   バックアップの実行に必要なアクセス許可がユーザーにありません。  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] には、バックアップが保存されるネットワーク上の場所にアクセスする権限がありません。  
  
-   データベースが存在しません。  
  
-   ターゲット ディレクトリがネットワーク共有に既に存在します。  
  
-   ターゲット ネットワーク共有が利用できません。  
  
-   ターゲット ネットワーク共有には、バックアップのための領域が十分にありません。 BACKUP DATABASE コマンドは、バックアップの開始前に十分なディスク領域があることを確認しません。BACKUP DATABASE の実行中、ディスク容量不足エラーが生成されます。 ディスク容量不足が発生すると、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は BACKUP DATABASE コマンドをロールバックします。 データベースのサイズを減らすには、[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) を実行します。  
  
-   トランザクション内でバックアップを開始しようとします。  
  
## <a name="general-remarks"></a>全般的な解説  
 データベース バックアップを実行する前に、[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md) を使用し、データベースのサイズを減らします。 
 
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] バックアップは、同じディレクトリ内で複数のファイルのセットとして保存されます。  
  
 通常、差分バックアップは完全バックアップよりも短時間で完了します。完全バックアップよりも頻繁に実行できます。 複数の差分バックアップが同じ完全バックアップに基づくとき、各差分バックアップには、前の差分バックアップのすべての変更が含まれます。  
  
 BACKUP コマンドをキャンセルした場合、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] はターゲット ディレクトリとバックアップのために作成されたあらゆるファイルを削除します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] で共有へのネットワーク接続が失われると、ロールバックを完了できません。  
  
 完全バックアップと差分バックアップは別々のディレクトリに保存されます。 完全バックアップと差分バックアップが同じバックアップに属することを指定するために名前付け規則が強制されることはありません。 独自の名前付け規則で追跡できます。 あるいは、WITH DESCRIPTION オプションで説明を追加し、RESTORE HEADERONLY ステートメントで説明を取得するという方法でも追跡できます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 master データベースは差分バックアップできません。 master データベースでは、完全バックアップのみ可能です。  
  
 バックアップ ファイルは、[RESTORE DATABASE &#40;並列データ ウェアハウス&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md) ステートメントを利用し、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] アプライアンスにバックアップを復元するのに適した形式でのみ保存されます。  
  
 データやユーザー情報を SMP [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データベースに移動するために、バックアップと BACKUP DATABASE ステートメントを使用することはできません。 この機能については、リモート テーブル コピー機能を使用できます。 詳細については、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)] の "Remote Table Copy" (リモート テーブル コピー) をご覧ください。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] では [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ技術を利用し、データベースをバックアップし、復元します。 バックアップ圧縮を使用するために、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] バックアップ オプションが事前構成されています。 圧縮、チェックサム、ブロック サイズ、バッファー カウントなど、バックアップ オプションを設定することはできません。  
  
 アプライアンスで一度に実行できるデータベース バックアップまたは復元は 1 つに限られます。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は、現在のバックアップまたは復元コマンドが完了するまで、バックアップまたは復元コマンドを待ち行列に入れます。  
  
 バックアップを復元するためのターゲット アプライアンスには、ソース アプライアンスと同じ数の計算ノードが含まれている必要があります。 ターゲット アプライアンスにはソース アプライアンスより多くの計算ノードが含まれていても構いませんが、少ないことは許可されません。  
  
 バックアップはアプライアンスから離れた場所に保存されるため、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] はバックアップの場所や名前を追跡しません。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] はデータベース バックアップの成功または失敗を追跡します。  
  
 差分バックアップは、前回の完全バックアップが正常に完了した場合にのみ許可されます。 たとえば、月曜日に Sales データベースの完全バックアップを作成し、バックアップが正常に完了したとします。 火曜日にも Sales データベースの完全バックアップを作成するが失敗します。 この失敗の後、月曜日の完全バックアップに基づいて差分バックアップを作成することはできません。 差分バックアップを作成するには、最初に完全バックアップを正常に作成する必要があります。  
  
## <a name="metadata"></a>メタデータ  
 これらの動的管理ビューには、すべてのバックアップ操作、復元操作、読み込み操作に関する情報が含まれています。 情報は、システムの再起動の間で永続化します。  
  
-   [sys.pdw_loader_backup_runs &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md)  
  
## <a name="performance"></a>[パフォーマンス]  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] では、バックアップを実行するために、最初にメタデータをバックアップし、それから計算ノードに保存されているデータベース データの並列バックアップを実行します。 データは各計算ノードから直接、バックアップ ディレクトリにコピーされます。 計算ノードからバックアップ ディレクトリにデータを最も効率的に移動するために、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] では、同時にデータをコピーする計算ノードの数が制御されます。  
  
## <a name="locking"></a>ロック  
 DATABASE オブジェクトに ExclusiveUpdate ロックを実行します。  
  
##  <a name="Security"></a> セキュリティ  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] バックアップはアプライアンスに格納されません。 そのため、IT チームは、バックアップ セキュリティのあらゆる面の管理を担当します。 これには、バックアップ データのセキュリティ、バックアップの保存に使用されるサーバーのセキュリティ、バックアップ サーバーを [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] アプライアンスに接続するネットワーク インフラストラクチャのセキュリティなどの管理が含まれます。  
  
 **ネットワーク資格情報の管理**  
  
 バックアップ ディレクトリへのネットワーク アクセスは、標準 Windows ファイル共有セキュリティに基づきます。 バックアップを実行する前に、バックアップ ディレクトリに [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] の信頼性を証明するための Windows アカウントを作成または指定する必要があります。 この Windows アカウントには、バックアップ ディレクトリにアクセスし、作成や書き込みを行うための許可を与える必要があります。  
  
> [!IMPORTANT]  
>  データのセキュリティ リスクを緩和するために、バックアップ操作と復元操作を実行する目的のためだけに Windows アカウントを 1 つ用意することをお勧めします。 そのアカウントのアクセス許可をバックアップの場所に限定します。  
  
 [sp_pdw_add_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md) ストアド プロシージャを実行し、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] にユーザー名とパスワードを保存する必要があります。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] では Windows Credential Manager を利用し、計算ノードにユーザー名とパスワードを保存し、復号します。 資格情報は BACKUP DATABASE コマンドでバックアップされません。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] からネットワーク資格情報を削除する方法については、「[sp_pdw_remove_network_credentials &#40;SQL Data Warehouse&#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md)」を参照してください。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] に保存されているネットワーク資格情報を一覧表示するには、[sys.dm_pdw_network_credentials &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md) 動的管理ビューを使用してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-add-network-credentials-for-the-backup-location"></a>A. バックアップ場所のネットワーク資格情報を追加する  
 バックアップを作成するには、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] にバックアップ ディレクトリの読み取り/書き込み許可を与える必要があります。 次の例は、ユーザーの資格情報を追加する方法です。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] では、これらの資格情報を格納し、バックアップ操作と復元操作に利用します。  
  
> [!IMPORTANT]  
>  セキュリティ上の理由から、バックアップ専用のドメイン アカウントを 1 つ作成することをお勧めします。  
  
```  
EXEC sp_pdw_add_network_credentials 'xxx.xxx.xxx.xxx', 'domain1\backupuser', '*****';  
```  
  
### <a name="b-remove-network-credentials-for-the-backup-location"></a>B. バックアップ場所のネットワーク資格情報を削除する  
 次の例は、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)] からドメイン ユーザーの資格情報を削除する方法です。  
  
```  
EXEC sp_pdw_remove_network_credentials 'xxx.xxx.xxx.xxx';  
```  
  
### <a name="c-create-a-full-backup-of-a-user-database"></a>C. ユーザー データベースの完全バックアップを作成する  
 次の例では、Invoices ユーザー データベースの完全バックアップを作成します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は Invoices2013 ディレクトリを作成し、バックアップ ファイルを \\\10.192.63.147\backups\yearly\Invoices2013Full ディレクトリに保存します。  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="d-create-a-differential-backup-of-a-user-database"></a>D. ユーザー データベースの差分バックアップを作成する  
 次の例では、差分バックアップを作成します。Invoices データベースの前回の完全バックアップ以降に行われたすべての変更が含まれます。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)] は \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff ディレクトリを作成し、それにファイルが保存されます。 'Invoices 2013 differential backup' というバックアップの説明がヘッダー情報と共に格納されます。  
  
 差分バックアップは、Invoices の前回の完全バックアップが正常に完了した場合にのみ正常に実行されます。  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH DIFFERENTIAL,   
    DESCRIPTION = 'Invoices 2013 differential backup';  
```  
  
### <a name="e-create-a-full-backup-of-the-master-database"></a>E. master データベースの完全バックアップを作成する  
 次の例では、master データベースの完全バックアップを作成し、ディレクトリ '\\\10.192.63.147\backups\2013\daily\20130722\master' にそれを格納します。  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master';  
```  
  
### <a name="f-create-a-backup-of-appliance-login-information"></a>F. アプライアンス ログイン情報のバックアップを作成する  
 master データベースにはアプライアンス ログイン情報が保存されます。 アプライアンス ログイン情報をバックアップするには、master をバックアップする必要があります。  
  
 次の例では、master データベースの完全バックアップを作成します。  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master'  
WITH (   
    DESCRIPTION = 'Master Backup 20130722',  
    NAME = 'login-backup'  
)  
;  
```  
  
## <a name="see-also"></a>参照  
 [RESTORE DATABASE &#40;並列データ ウェアハウス&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
  

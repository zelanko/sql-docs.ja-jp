---
title: "データベースのバックアップ (並列データ ウェアハウス) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 73c8d465-b36b-4727-b9f3-368e98677c64
caps.latest.revision: "11"
author: barbkess
ms.author: barbkess
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ced03c90d0f30a1e8749d09f00d293bdee53b06e
ms.sourcegitcommit: 66bef6981f613b454db465e190b489031c4fb8d3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="backup-database-parallel-data-warehouse"></a>データベースのバックアップ (並列データ ウェアハウス)
[!INCLUDE[tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md](../../includes/tsql-appliesto-xxxxxx-xxxx-xxxx-pdw-md.md)]

  バックアップを作成、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースおよびユーザー指定のネットワークの場所にアプライアンス オフ バックアップを保存します。 このステートメントで使用する[データベースの復元 &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)災害復旧、または 1 つのアプライアンスからデータベースをコピーします。  
  
 **開始する前に**を取得し、バックアップ サーバーの構成」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 バックアップの 2 種類があります[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。 A*データベースの完全バックアップ*全体のバックアップは、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベース。 A*データベースの差分バックアップ*最後の完全バックアップ以降に行われた変更にはのみが含まれます。 ユーザー データベースのバックアップには、データベース ユーザー、およびデータベース ロールが含まれています。 Master データベースのバックアップには、ログインが含まれています。  
  
 詳細については[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースのバックアップ「のバックアップと復元」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
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
 バックアップを作成する対象のデータベースの名前。 データベースには、master データベースまたはユーザー データベースを指定できます。  
  
 ディスクを = '\\\\*UNC_path*\\*backup_directory*'  
 ネットワーク パスとするディレクトリ[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップ ファイルを記述します。 たとえば、'\\\xxx.xxx.xxx.xxx\backups\2012\Monthly\08.2012.Mybackup' です。  
  
-   バックアップ ディレクトリの名前をパスでは、既に存在する必要があり、完全修飾の汎用名前付け規則 (UNC) パスとして指定する必要があります。  
  
-   バックアップ ディレクトリ*backup_directory*、backup コマンドを実行する前に存在する必要があります。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップ ディレクトリを作成します。  
  
-   バックアップ ディレクトリへのパスがローカル パスにすることはできません、上のいずれかの場所をすることはできません、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスのノードです。  
  
-   バックアップ ディレクトリの名前と UNC パスの最大長は、200 文字です。  
  
-   サーバーまたはホストは、IP アドレスとして指定する必要があります。  これは、ホストまたはサーバー名として指定できません。  
  
 説明 = **'***テキスト***'**  
 バックアップの説明テキストを指定します。 テキストの最大長は、255 文字です。  
  
 説明は、メタデータは格納され、RESTORE HEADERONLY とバックアップ ヘッダーを復元するときに表示されます。  
  
 名前 = **'***バックアップ名 (_n)***'**  
 バックアップの名前を指定します。 バックアップ名は、データベース名を異なっていてもかまいません。  
  
-   名前の長さは最大 128 文字です。  
  
-   パスを含めることはできません。  
  
-   アルファベットまたは数字の文字またはアンダー スコア (_) で始まる必要があります。 許可されている特殊な文字はアンダー スコア (\_)、ハイフン (-) またはスペース ()。 バックアップ名は、空白文字で終わることはできません。  
  
-   場合、ステートメントは失敗*バックアップ*指定した場所に既に存在します。  
  
 この名前は、メタデータは格納され、RESTORE HEADERONLY とバックアップ ヘッダーを復元するときに表示されます。  
  
 DIFFERENTIAL  
 ユーザー データベースの差分バックアップを実行することを指定します。 省略した場合、既定では、データベースの完全バックアップです。 差分バックアップの名前は、完全バックアップの名前に一致する必要はありません。 追跡するため、差分バックアップとその対応する完全バックアップには、同じ名前の '完全' または 'diff' 追加の使用を検討します。  
  
 例:  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerFull';`  
  
 `BACKUP DATABASE Customer TO DISK = '\\xxx.xxx.xxx.xxx\backups\CustomerDiff' WITH DIFFERENTIAL;`  
  
## <a name="permissions"></a>Permissions  
 必要があります、 **BACKUP DATABASE**権限またはメンバーシップ、 **db_backupoperator**固定データベース ロール。 追加された通常のユーザーでは、マスター データベースをバックアップすることはできません、 **db_backupoperator**固定データベース ロール。 Master データベース バックアップのみ可能するによって**sa**、ファブリック管理者、またはのメンバー、 **sysadmin**固定サーバー ロール。  
  
 アクセス、作成、およびバックアップのディレクトリに書き込むアクセス許可を持つ Windows アカウントが必要です。 Windows アカウント名とパスワードを格納する必要がありますも[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]します。 これらのネットワーク資格情報を追加する[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を使用して、 [sp_pdw_add_network_credentials (& a) #40 です。SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)ストアド プロシージャです。  
  
 資格情報の管理の詳細については[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を参照してください、[セキュリティ](#Security)セクションです。  
  
## <a name="error-handling"></a>エラー処理  
 次の条件下でバックアップ データベース エラー:  
  
-   ユーザーの権限は、バックアップを実行するのに十分ではありません。  
  
-   [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップが格納されるネットワークの場所に適切なアクセス許可がありませんでした。  
  
-   データベースが存在しません。  
  
-   ターゲット ディレクトリは、ネットワーク共有に既に存在します。  
  
-   ターゲット ネットワーク共有は使用できません。  
  
-   ターゲット ネットワーク共有には、バックアップに必要な領域がありません。 データベースのバックアップ コマンドは、データベースのバックアップの実行中にディスク領域不足エラーを生成できるように、バックアップを開始する前に十分なディスク領域が存在することを確認できません。 ディスク領域の不足が発生すると[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースのバックアップ コマンドをロールバックします。 データベースのサイズを削減するには実行[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)  
  
-   トランザクション内でのバックアップを開始しようとしてください。  
  
## <a name="general-remarks"></a>全般的な解説  
 データベース バックアップを実行する前に、使用[DBCC SHRINKLOG (Azure SQL Data Warehouse)](../../t-sql/database-console-commands/dbcc-shrinklog-azure-sql-data-warehouse.md)データベースのサイズを小さくします。 
 
 A[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップが同じディレクトリ内の複数のファイルのセットとして保存します。  
  
 通常、差分バックアップは、完全バックアップよりも時間が短くより頻繁に実行できます。 複数の差分バックアップは、同一の完全バックアップに基づいている場合、各差分バックアップは、前回の差分バックアップにすべての変更を含めます。  
  
 バックアップ コマンドをキャンセルした場合[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ターゲット ディレクトリと、バックアップ用に作成されたファイルは削除されます。 場合[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]ネットワーク接続を失うと、共有にロールバックを完了できません。  
  
 完全バックアップと差分バックアップは、別々 のディレクトリに格納されます。 名前付け規則は、完全バックアップと差分バックアップが一緒に属していることを指定するのには適用されません。 これを独自の名前付け規則を追跡できます。 代わりに、説明を追加する説明とオプションを使用して、説明を取得する RESTORE HEADERONLY ステートメントを使用して、これを追跡することができます。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 Master データベースの差分バックアップを実行することはできません。 Master データベースの完全バックアップのみがサポートされています。  
  
 バックアップを復元するためだけに適切な形式でバックアップ ファイルが格納されている、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスを使用して、[データベースの復元 &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)ステートメントです。  
  
 SMP にデータまたはユーザーの情報を転送する BACKUP DATABASE ステートメントでのバックアップを使用することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベース。 この機能については、リモート テーブルのコピー機能を使用できます。 詳細については、「リモート テーブルのコピー」を参照してください、[!INCLUDE[pdw-product-documentation](../../includes/pdw-product-documentation-md.md)]です。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]使用して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ テクノロジをバックアップおよびデータベースを復元します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]バックアップ オプションは、バックアップの圧縮を使用する構成済みです。 圧縮、チェックサム、ブロック サイズとバッファー カウントなどのバックアップのオプションを設定することはできません。  
  
 1 つだけのデータベースのバックアップまたは復元は、特定の時点でアプライアンスで実行できます。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]キューに現在のバックアップまで backup または restore コマンドまたは restore コマンドが完了します。  
  
 バックアップを復元するためのターゲット アプライアンス ソース アプライアンスとして少なくとも多くのコンピューティング ノードが必要です。 ターゲットは、ソース アプライアンス、複数のコンピューティング ノードを持つことができますが、コンピューティング ノードを少なくすることはできません。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]場所を追跡しないと、バックアップが格納されるため、バックアップの名前が、アプライアンスをオフします。  
  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]データベースのバックアップの成否を追跡します。  
  
 差分バックアップは、前回の完全バックアップが正常に完了した場合にのみ使用できます。 たとえば、月曜日 Sales データベースの完全バックアップを作成することと、バックアップが正常に完了します。 火曜日には、Sales データベースの完全バックアップを作成し、失敗した場合します。 この障害の後、月曜日の完全バックアップに基づいた差分バックアップを作成することはできません。 まず、差分バックアップを作成する前に成功した完全バックアップを作成する必要があります。  
  
## <a name="metadata"></a>メタデータ  
 これらの動的管理ビューは、すべてのバックアップの復元に関する情報が含まれてし、操作を読み込みます。 情報は、システムの再起動の間で永続化します。  
  
-   [sys.pdw_loader_backup_runs &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-runs-transact-sql.md)  
  
-   [sys.pdw_loader_backup_run_details &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-loader-backup-run-details-transact-sql.md)  
  
-   [sys.pdw_loader_run_stages &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-pdw-loader-run-stages-transact-sql.md)  
  
## <a name="performance"></a>パフォーマンス  
 バックアップを実行する[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]メタデータ、その後の最初のバックアップを作成は、コンピューティング ノードに格納されているデータベースのデータの並列バックアップを実行します。 データは、各コンピューティング ノードから直接、バックアップ ディレクトリにコピーされます。 コンピューティング ノードから、バックアップ ディレクトリにデータを移動するための最適なパフォーマンスを実現するために[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]同時にデータをコピーであるコンピューティング ノードの数を制御します。  
  
## <a name="locking"></a>ロック  
 データベース オブジェクトの ExclusiveUpdate ロックを取得します。  
  
##  <a name="Security"></a> セキュリティ  
 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップは、アプライアンス上は格納されません。 そのため、社内の IT チームは、バックアップのセキュリティのすべての側面を管理するため、します。 たとえば、これが含まれています、バックアップ データのセキュリティ、バックアップを保存するために使用するサーバーのセキュリティとは、バックアップ サーバーに接続するネットワーク インフラストラクチャのセキュリティを管理する、[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]アプライアンスです。  
  
 **ネットワーク資格情報を管理します。**  
  
 バックアップ ディレクトリへのネットワーク アクセスは、標準の Windows ファイル共有セキュリティに基づいています。 バックアップを実行する前に作成またはの認証に使用される Windows アカウントを指定する必要があります。[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]バックアップ ディレクトリにします。 この windows アカウントにアクセスし、作成、および、バックアップ ディレクトリに書き込むアクセス許可が必要です。  
  
> [!IMPORTANT]  
>  データのセキュリティ上のリスクを減らすためには、バックアップを実行するためだけの 1 つの Windows アカウントを指定して、復元操作することお勧めします。 バックアップの場所とこれ以外の場所へのアクセス許可がある場合は、このアカウントを許可します。  
  
 ユーザー名とパスワードを保存する必要があります[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を実行して、 [sp_pdw_add_network_credentials (& a) #40 です。SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-add-network-credentials-sql-data-warehouse.md)ストアド プロシージャです。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]保存し、コントロールのノードとコンピューティング ノードのユーザー名とパスワードを暗号化するには、Windows 資格情報マネージャーを使用します。 資格情報は、データベースのバックアップ コマンドではバックアップされません。  
  
 ネットワーク資格情報を削除する[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を参照してください[sp_pdw_remove_network_credentials (& a) #40 です。SQL Data Warehouse &#41;](../../relational-databases/system-stored-procedures/sp-pdw-remove-network-credentials-sql-data-warehouse.md).  
  
 格納されているすべてのネットワーク資格情報を一覧表示する[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]を使用して、 [sys.dm_pdw_network_credentials &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-pdw-network-credentials-transact-sql.md)動的管理ビュー。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-add-network-credentials-for-the-backup-location"></a>A. バックアップの場所のネットワーク資格情報を追加します。  
 バックアップを作成する[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]のバックアップ ディレクトリへの読み取り/書き込みアクセス許可が必要です。 次の例では、ユーザーの資格情報を追加する方法を示します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]これらの資格情報を格納し、バックアップに使用する操作と復元操作です。  
  
> [!IMPORTANT]  
>  セキュリティ上の理由から、バックアップを実行するためだけの 1 つのドメイン アカウントを作成することをお勧めします。  
  
```  
EXEC sp_pdw_add_network_credentials 'xxx.xxx.xxx.xxx', 'domain1\backupuser', '*****';  
```  
  
### <a name="b-remove-network-credentials-for-the-backup-location"></a>B. バックアップの場所のネットワーク資格情報を削除します。  
 次の例からドメイン ユーザーの資格情報を削除する方法を示しています。[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]です。  
  
```  
EXEC sp_pdw_remove_network_credentials 'xxx.xxx.xxx.xxx';  
```  
  
### <a name="c-create-a-full-backup-of-a-user-database"></a>C. ユーザー データベースの完全バックアップを作成します。  
 次の例では、請求書のユーザー データベースの完全バックアップを作成します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]Invoices2013 ディレクトリを作成しするバックアップ ファイルを保存、 \\\10.192.63.147\backups\yearly\Invoices2013Full ディレクトリ。  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Full';  
```  
  
### <a name="d-create-a-differential-backup-of-a-user-database"></a>D. ユーザー データベースの差分バックアップを作成します。  
 次の例では、請求書データベースの最後の完全バックアップ以降に行われたすべての変更を含む差分バックアップを作成します。 [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]作成されます、 \\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff ディレクトリにファイルが保存されます。 説明 '差分バックアップの請求書 2013年' は、バックアップ ヘッダー情報を含む保存されます。  
  
 請求書の最後の完全バックアップが正常に完了した場合、差分バックアップは正常に実行のみです。  
  
```  
BACKUP DATABASE Invoices TO DISK = '\\xxx.xxx.xxx.xxx\backups\yearly\Invoices2013Diff'  
    WITH DIFFERENTIAL,   
    DESCRIPTION = 'Invoices 2013 differential backup';  
```  
  
### <a name="e-create-a-full-backup-of-the-master-database"></a>E. Master データベースの完全バックアップを作成します。  
 次の例は、master データベースの完全バックアップを作成し、ディレクトリに格納 '\\\10.192.63.147\backups\2013\daily\20130722\master' です。  
  
```  
BACKUP DATABASE master TO DISK = '\\xxx.xxx.xxx.xxx\backups\2013\daily\20130722\master';  
```  
  
### <a name="f-create-a-backup-of-appliance-login-information"></a>F. アプライアンスのログイン情報のバックアップを作成します。  
 Master データベースでは、アプライアンスのログイン情報を格納します。 アプライアンスのログイン情報をバックアップするには、バックアップ マスターにする必要があります。  
  
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
 [データベースの復元 &#40;です。並列データ ウェアハウス&#41;](../../t-sql/statements/restore-database-parallel-data-warehouse.md)  
  
  

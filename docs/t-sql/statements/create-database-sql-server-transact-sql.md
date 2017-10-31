---
title: "データベースの作成 (SQL Server TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DATABASE_TSQL
- DATABASE
- CONTAINMENT_TSQL
- CREATE DATABASE
- CREATE_DATABASE_TSQL
- CONTAINS_FILESTREAM_TSQL
- CONTAINS FILESTREAM
- CONTAINMENT
dev_langs:
- TSQL
helpviewer_keywords:
- snapshots [SQL Server database snapshots], creating
- databases [SQL Server], creating
- model database [SQL Server], database creation
- mounted drives [SQL Server]
- CREATE DATABASE
- CREATE DATABASE statement
- file creation [SQL Server]
- creating databases
- containment
- filegroups [SQL Server], database creation
- database creation [SQL Server], CREATE DATABASE statement
- moving databases
- attaching databases [SQL Server], CREATE DATABASE...FOR ATTACH
ms.assetid: 29ddac46-7a0f-4151-bd94-75c1908c89f8
caps.latest.revision: 212
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: aecf422ca2289b2a417147eb402921bb8530d969
ms.openlocfilehash: de8574d6d4f2322c63743828b7b8a03d4e6fa576
ms.contentlocale: ja-jp
ms.lasthandoff: 10/24/2017

---
# <a name="create-database-sql-server-transact-sql"></a>CREATE DATABASE (SQL Server Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいデータベースとデータベースを格納するファイルを作成するか、データベース スナップショットを作成するか、以前作成されたデータベースのデタッチされたファイルからデータベースをアタッチします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
      Create a database  
CREATE DATABASE database_name   
[ CONTAINMENT = { NONE | PARTIAL } ]  
[ ON   
      [ PRIMARY ] <filespec> [ ,...n ]   
      [ , <filegroup> [ ,...n ] ]   
      [ LOG ON <filespec> [ ,...n ] ]   
]   
[ COLLATE collation_name ]  
[ WITH  <option> [,...n ] ]  
[;]  
  
<option> ::=  
{  
      FILESTREAM ( <filestream_option> [,...n ] )  
    | DEFAULT_FULLTEXT_LANGUAGE = { lcid | language_name | language_alias }  
    | DEFAULT_LANGUAGE = { lcid | language_name | language_alias }  
    | NESTED_TRIGGERS = { OFF | ON }  
    | TRANSFORM_NOISE_WORDS = { OFF | ON}  
    | TWO_DIGIT_YEAR_CUTOFF = <two_digit_year_cutoff>   
    | DB_CHAINING { OFF | ON }  
    | TRUSTWORTHY { OFF | ON }  
}  
  
<filestream_option> ::=  
{  
      NON_TRANSACTED_ACCESS = { OFF | READ_ONLY | FULL }  
    | DIRECTORY_NAME = 'directory_name'   
}  
  
<filespec> ::=   
{  
(  
    NAME = logical_file_name ,  
    FILENAME = { 'os_file_name' | 'filestream_path' }   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB | % ] ]  
)  
}  
  
<filegroup> ::=   
{  
FILEGROUP filegroup name [ [ CONTAINS FILESTREAM ] [ DEFAULT ] | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    <filespec> [ ,...n ]  
}  
  
<service_broker_option> ::=  
{  
    ENABLE_BROKER  
  | NEW_BROKER  
  | ERROR_BROKER_CONVERSATIONS  
}  
  
```  
  
```  
  
      Attach a database  
CREATE DATABASE database_name   
    ON <filespec> [ ,...n ]   
    FOR { { ATTACH [ WITH <attach_database_option> [ , ...n ] ] }  
        | ATTACH_REBUILD_LOG }  
[;]  
  
<attach_database_option> ::=  
{  
      <service_broker_option>  
    | RESTRICTED_USER  
    | FILESTREAM ( DIRECTORY_NAME = { 'directory_name' | NULL } )  
}  
  
```  
  
```  
  
      Create a database snapshot  
CREATE DATABASE database_snapshot_name   
    ON   
    (  
        NAME = logical_file_name,  
        FILENAME = 'os_file_name'   
    ) [ ,...n ]   
    AS SNAPSHOT OF source_database_name  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *database_name*  
 新規データベースの名前です。 データベース名は、のインスタンス内で一意である必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の規則に準拠している[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 *database_name*ログ ファイルの論理名が指定されていない場合を除き、128 文字までの最大数を指定できます。 論理ログ ファイル名が指定されていない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]生成、 *logical_file_name*と*os_file_name*にサフィックスを追加することにより、ログの*database_name*. これにより、制限*database_name*を 123 文字が生成された論理ファイル名が 128 個の文字になるようにします。  
  
 データ ファイル名が指定されていない場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用*database_name*両方と、 *logical_file_name*と同様、 *os_file_name*です。 既定のパスはレジストリから取得されます。 使用して、既定のパスを変更することができます、**サーバー プロパティ (データベースの設定 ページ)**で[!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]です。 既定のパスを変更するには、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] を再起動する必要があります。  
  
 CONTAINMENT = { NONE | PARTIAL }  

**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 データベースの包含状態を指定します。 NONE = 非包含データベース PARTIAL = 部分的包含データベース  
  
 ON  
 データベースのデータ部分の格納に使用するディスク ファイル (データ ファイル) を明示的に定義するように指定します。 後のコンマ区切り一覧と必要な\<filespec > 項目をプライマリ ファイル グループのデータ ファイルを定義します。 プライマリ ファイル グループ内のファイルの一覧の後に、省略可能なコンマ区切りのリストをできます\<ファイル グループ > ユーザーのファイル グループとそのファイルを定義する項目。  
  
 PRIMARY  
 指定する、関連付けられている\<filespec > リストは、プライマリ ファイルを定義します。 指定された最初のファイル、 \<filespec > エントリは、プライマリ ファイル グループにプライマリ ファイルになります。 データベースはプライマリ ファイルを 1 つだけ保有することができます。 詳細については、「 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)」を参照してください。  
  
 PRIMARY を指定しないと、CREATE DATABASE ステートメントに記述された最初のファイルがプライマリ ファイルになります。  
  
 LOG ON  
 データベース ログの格納に使用するディスク ファイル (ログ ファイル) を明示的に定義するように指定します。 LOG ON がのコンマ区切りの一覧に続く\<filespec > 項目をログ ファイルを定義します。 LOG ON が指定されていない場合は、1 つのログ ファイルが自動的に作成、データベース、または 512 KB のすべてのデータ ファイルのサイズの合計の 25% のサイズが、大きい方します。 このファイルは既定のログ ファイルの場所に保存されます。 この場所については、次を参照してください[を表示またはデータとログ ファイル &#40; の既定の場所を変更。SQL Server Management Studio &#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
 LOG ON はデータベース スナップショットでは指定できません。  
  
 COLLATE *collation_name*  
 データベースの既定の照合順序を指定します。 照合順序名には、Windows 照合順序名または SQL 照合順序名を指定できます。 データベースでのインスタンスの既定の照合順序が割り当てられている指定しない場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 照合順序名は、データベース スナップショットでは指定できません。  
  
 照合順序名は、FOR ATTACH 句または FOR ATTACH_REBUILD_LOG 句と共に指定することはできません。 アタッチされたデータベースの照合順序を変更する方法についてを参照してくださいこの[Microsoft Web サイト](http://go.microsoft.com/fwlink/?linkid=16419&kbid=325335)です。  
  
 Windows と SQL 照合順序名の詳細については、次を参照してください。 [COLLATE & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/statements/collations.md).  
  
> [!NOTE]  
>  包含データベースは、非包含データベースとは異なる方法で照合されます。 参照してください[Contained Database Collations](../../relational-databases/databases/contained-database-collations.md)詳細についてはします。  
  
 \<オプション >  
 -   **\<filestream_options >** 
  
     NON_TRANSACTED_ACCESS = { **OFF** |READ_ONLY |完全}  
**適用対象**: [!INCLUDE[ssSQL11](../../includes/sssql11-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     データベースに対する非トランザクション FILESTREAM アクセスのレベルを指定します。  
  
    |値|説明|  
    |-----------|-----------------|  
    |OFF|非トランザクション アクセスは無効です。|  
    |READONLY|このデータベース内の FILESTREAM データは、非トランザクション プロセスによって読み取ることができます。|  
    |FULL|FILESTREAM FileTable に対する完全な非トランザクション アクセスは有効です。|  
  
     DIRECTORY_NAME = \<directory_name >**対象**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     Windows と互換性のあるディレクトリ名です。 この名前は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内のすべての Database_Directory 名の中で一意である必要があります。 一意性の比較では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 照合順序の設定とは関係なく、大文字と小文字は区別されません。 このオプションは、このデータベースに FileTable を作成する前に設定する必要があります。  
  
 次のオプションは、CONTAINMENT が PARTIAL に設定されている場合にのみ使用できます。 CONTAINMENT が NONE に設定されている場合、エラーが発生します。  
  
-   **DEFAULT_FULLTEXT_LANGUAGE = \<lcid > |\<言語名 > |\<言語の別名 >**  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default full-text language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-full-text-language-server-configuration-option.md) for a full description of this option.  
  
-   **DEFAULT_LANGUAGE = \<lcid > |\<言語名 > |\<言語の別名 >**  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the default language Server Configuration Option](../../database-engine/configure-windows/configure-the-default-language-server-configuration-option.md) for a full description of this option.  
  
-   **NESTED_TRIGGERS = {OFF |ON}**  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [Configure the nested triggers Server Configuration Option](../../database-engine/configure-windows/configure-the-nested-triggers-server-configuration-option.md) for a full description of this option.  
  
-   **TRANSFORM_NOISE_WORDS = {OFF |ON}**  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
     See [transform noise words Server Configuration Option](../../database-engine/configure-windows/transform-noise-words-server-configuration-option.md)for a full description of this option.  
  
-   **TWO_DIGIT_YEAR_CUTOFF = {2049 |\<1753 ~ 9999 の任意の年 >}**  
  
     年を表す 4 桁の数字。 既定値は 2049 です。 参照してください[構成 two digit year cutoff Server Configuration Option](../../database-engine/configure-windows/configure-the-two-digit-year-cutoff-server-configuration-option.md)このオプションの詳細についてはします。  
  
-   **DB_CHAINING {OFF |ON}**  
  
     ON が指定されている場合、データベースを、複数データベースの組み合わせ所有権のソース データベースまたは対象データベースとして使用できます。  
  
     OFF の場合、データベースは、複数データベースの組み合わせ所有権に参加することはできません。 既定値は OFF です。  
  
    > [!IMPORTANT]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスでは、cross db ownership chaining サーバー オプションが 0 (OFF) の場合に、この設定が認識されます。 cross db ownership chaining が 1 (ON) の場合は、このオプションの値にかかわらず、すべてのユーザー データベースが複数データベースの組み合わせ所有権に参加できます。 このオプションを使用して設定[sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
     このオプションを設定するには、sysadmin 固定サーバー ロールのメンバーシップが必要です。 master、model、tempdb のシステム データベースでは、DB_CHAINING オプションを設定することはできません。  
  
-   **信頼できる {オフ |ON}**  
  
     ON が指定されている場合、権限借用のコンテキストを使用するデータベース モジュール (ビュー、ユーザー定義関数、ストアド プロシージャなど) は、データベース外のリソースにアクセスできます。  
  
     OFF の場合、権限借用のコンテキスト内のデータベース モジュールは、データベース外のリソースにアクセスできません。 既定値は OFF です。  
  
     データベースがアタッチされている場合は常に、TRUSTWORTHY は OFF に設定されます。  
  
     既定では、msdb データベースを除くすべてのシステム データベースで TRUSTWORTHY は OFF に設定されています。 model および tempdb データベースでは、この値は変更できません。 master データベースでは、TRUSTWORTHY オプションを ON に設定しないことを強くお勧めします。  
  
     このオプションを設定するには、sysadmin 固定サーバー ロールのメンバーシップが必要です。  
  
 FOR ATTACH [WITH \< attach_database_option >] を指定して、データベースが作成される[アタッチ](../../relational-databases/databases/database-detach-and-attach-sql-server.md)既存のオペレーティング システム ファイルのセット。 必要があります、 \<filespec > エントリをプライマリ ファイルを指定します。 唯一の他の\<filespec > 必要なエントリは、データベースが最初から別のパスを持っている任意のファイルが作成または最後にアタッチします。 A \<filespec > エントリは、これらのファイルに指定してください。  
  
 FOR ATTACH では、以下のことが必要です。  
  
-   すべてのデータ ファイル (MDF および NDF) が有効であること  
  
-   ログ ファイルが複数存在する場合は、これらがすべて使用可能であること  
  
 読み取り/書き込みデータベースに現在利用できないログ ファイルが 1 つある場合、アタッチ操作の前に、ユーザーも、開かれたトランザクションもない状態でデータベースをシャットダウンすると、FOR ATTACH は自動的にログ ファイルを再構築し、プライマリ ファイルを更新します。 これに対し、読み取り専用データベースの場合、プライマリ ファイルを更新できないため、ログは再構築されません。 したがって、ログが利用できない読み取り専用データベースをアタッチする場合、ログ ファイルまたはファイルを FOR ATTACH 句に指定する必要があります。  
  
> [!NOTE]  
>  新しいバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] で作成したデータベースは、それ以前のバージョンでアタッチすることはできません。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、アタッチされるデータベースの一部であるすべてのフルテキスト ファイルは、データベースと共にアタッチされます。 フルテキスト カタログの新しいパスを指定するには、フルテキストのオペレーティング システム ファイル名を含めずに新しい場所を指定します。 詳細については、「例」を参照してください。  
  
 「ディレクトリ名」の FILESTREAM オプションを含むデータベースをアタッチする、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスが求められます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Database_Directory 名が一意であることを確認します。 しない場合は、アタッチ操作がエラーで失敗"FILESTREAM Database_Directory 名\<名 > この SQL Server インスタンスで一意ではありません"です。 このエラーは、省略可能なパラメーターを回避する*directory_name*でこの操作に渡す必要があります。  
  
 FOR ATTACH はデータベース スナップショットでは指定できません。  
  
 FOR ATTACH は RESTRICTED_USER オプションを指定できます。 RESTRICTED_USER モードでは、db_owner 固定データベース ロールと、dbcreator 固定サーバー ロールおよび sysadmin 固定サーバー ロールのメンバーのみが、データベースに接続できます。ただし、接続ユーザー数に制限はありません。 修飾されていないユーザーによる試行が拒否されます。  
  
 データベースで使用する場合[!INCLUDE[ssSB](../../includes/sssb-md.md)]、使用、WITH \<service_broker_option >、FOR ATTACH 句で。 
  
 \<service_broker_option > コントロール[!INCLUDE[ssSB](../../includes/sssb-md.md)]メッセージ配信および[!INCLUDE[ssSB](../../includes/sssb-md.md)]データベースの識別子。 [!INCLUDE[ssSB](../../includes/sssb-md.md)]オプションは、FOR ATTACH 句を使用する場合にのみ指定できます。  
  
 ENABLE_BROKER  
 指定したデータベースに対して [!INCLUDE[ssSB](../../includes/sssb-md.md)] を有効にします。 つまり、メッセージ配信が開始され、is_broker_enabled に設定されている、sys.databases カタログ ビューの場合は true です。 データベースは、既存の [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子を保持します。  
  
 NEW_BROKER  
 sys.databases と復元されたデータベースの両方に新しい service_broker_guid 値を作成し、すべてのメッセージ交換エンドポイントをクリーンアップして終了します。 ブローカーは有効ですが、リモートのメッセージ交換エンドポイントにメッセージは送信されません。 古いを参照するルート[!INCLUDE[ssSB](../../includes/sssb-md.md)]識別子は、新しい識別子で再作成する必要があります。  
  
 ERROR_BROKER_CONVERSATIONS  
 データベースがアタッチまたは復元されていることを示すエラーと共に、すべてのメッセージ交換を終了します。 ブローカーはこの操作が完了するまで無効になり、その後、有効になります。 データベースは、既存の [!INCLUDE[ssSB](../../includes/sssb-md.md)] 識別子を保持します。  
  
 レプリケートされたデータベースをアタッチするとき、そのデータベースがデタッチではなくコピーされたものである場合は、次の点を考慮してください。  
  
-   元のデータベースと同じサーバー インスタンスおよびバージョンにデータベースをアタッチする場合は、必要な追加手順はありません。  
  
-   場合は、同じサーバー インスタンスにデータベースをアタッチする場合は、実行する必要があります、アップグレードされたバージョン[sp_vupgrade_replication](../../relational-databases/system-stored-procedures/sp-vupgrade-replication-transact-sql.md)アタッチ操作が完了した後にレプリケーションをアップグレードします。  
  
-   実行する必要があります、バージョンにかかわらず、別のサーバー インスタンスにデータベースをアタッチする場合[sp_removedbreplication](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)アタッチ操作が完了した後にレプリケーションを削除します。  
  
> [!NOTE]  
>  動作をアタッチ、 **vardecimal**ストレージ形式が、[!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)]以上にアップグレードする必要があります[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]Service Pack 2 です。 以前のバージョンに vardecimal ストレージ形式を使用してデータベースをアタッチすることはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 詳細については、 **vardecimal**ストレージ形式を参照してください[データ圧縮](../../relational-databases/data-compression/data-compression.md)です。  
  
 データベースが最初に [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]の新しいインスタンスにアタッチまたは復元されるとき、データベース マスター キー (サービス マスター キーにより暗号化されたもの) のコピーはまだサーバーに格納されていません。 **OPEN MASTER KEY** を使用して、データベース マスター キー (DMK) を暗号化解除する必要があります。 DMK の暗号化が解除されると、 **ALTER MASTER KEY REGENERATE** ステートメントを使用して、サービス マスター キー (SMK) で暗号化された DMK のコピーをサーバーに提供することにより、将来、自動的に暗号化解除することも可能となります。 データベースを以前のバージョンからアップグレードした場合、新しい AES アルゴリズムを使用するように DMK を再作成する必要があります。 DMK を再作成する方法については、「[ALTER MASTER KEY &#40;Transact-SQL&#41;](../../t-sql/statements/alter-master-key-transact-sql.md)」を参照してください。 DMK キーを再作成して AES にアップグレードするのに必要な時間は、DMK によって保護されているオブジェクトの数によって異なります。 DMK キーを再作成して AES にアップグレードする作業は、1 回限りで済み、今後のキー ローテーション方法には影響を与えません。 使用してデータベースをアップグレードする方法については、アタッチを参照してください[データベースを使用してデタッチしアタッチ &#40; のアップグレードTRANSACT-SQL と #41 です。](../../relational-databases/databases/upgrade-a-database-using-detach-and-attach-transact-sql.md).  
  
 **セキュリティに関する注意**不明または信頼できないソースからデータベースをアタッチしないことをお勧めします。 こうしたデータベースには、意図しない [!INCLUDE[tsql](../../includes/tsql-md.md)] コードを実行したり、スキーマまたは物理データベース構造を変更してエラーを発生させるような、悪意のあるコードが含まれている可能性があります。 不明または信頼できないソースからデータベースを使用する前に実行[DBCC CHECKDB](../../t-sql/database-console-commands/dbcc-checkdb-transact-sql.md)非稼働サーバー上のデータベースにもストアド プロシージャやデータベースの他のユーザー定義コードなどのコードを確認します。  
  
> [!NOTE]  
>  **TRUSTWORTHY**と**DB_CHAINING**オプションには影響が及ぶことないデータベースをアタッチするときにがします。  
  
 FOR ATTACH_REBUILD_LOG  
 既存のオペレーティング システム ファイルのセットをアタッチすることによりデータベースを作成するように指定します。 このオプションは読み取り/書き込みデータベースに限定されます。 必要があります、  *\<filespec >*エントリをプライマリ ファイルを指定します。 1 つ以上のトランザクション ログ ファイルが見つからない場合、ログ ファイルは再構築されます。 Attach_rebuild_log を指定では、新しい、1 MB のログ ファイルが自動的に作成されます。 このファイルは既定のログ ファイルの場所に保存されます。 この場所については、次を参照してください[を表示またはデータとログ ファイル &#40; の既定の場所を変更。SQL Server Management Studio &#41;](../../database-engine/configure-windows/view-or-change-the-default-locations-for-data-and-log-files.md).  
  
> [!NOTE]  
>  ログ ファイルが利用可能な場合は、[!INCLUDE[ssDE](../../includes/ssde-md.md)]はログ ファイルを再構築せず、それらのファイルを使用します。  
  
 FOR ATTACH_REBUILD_LOG では、以下のことが必要です。  
  
-   データベースのクリーン シャットダウン  
  
-   すべてのデータ ファイル (MDF および NDF) が有効であること  
  
> [!IMPORTANT]  
>  この操作により、連続したログ バックアップが中断されます。 操作が完了したら、データベース全体のバックアップを行うことをお勧めします。 詳細については、「 [BACKUP &#40;Transact-SQL&#41;](../../t-sql/statements/backup-transact-sql.md)」を参照してください。  
  
 通常、FOR ATTACH_REBUILD_LOG は、大きなログを持つ読み取り/書き込みデータベースを別のサーバーにコピーする場合に使用します。このようなサーバーでは、コピーしたデータベースが、多くの場合読み取り操作に使用されます (または読み取り操作でのみ使用されます)。このため、元のデータベースほどログ領域を必要としません。  
  
 FOR ATTACH_REBUILD_LOG はデータベース スナップショットでは指定できません。  
  
 アタッチして、データベースのデタッチに関する詳細については、次を参照してください。[データベースのデタッチとアタッチ & #40 です。SQL Server &#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md).  
  
 \<filespec >  
 ファイル プロパティを制御します。  
  
 名前*logical_file_name*  
 ファイルの論理名を指定します。 NAME は、FOR ATTACH 句の 1 つを指定する場合以外に、FILENAME が指定されるときに必要です。 FILESTREAM ファイル グループの名前を PRIMARY にすることはできません。  
  
 *logical_file_name*  
 使用される論理名は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルを参照するときにします。 *Logical_file_name* 、規則に準拠しているデータベース内で一意である必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 この名前は、文字定数、UNICODE 定数、標準の識別子、区切られた識別子のいずれでもかまいません。  
  
 ファイル名 { **'***os_file_name***'** | **'***filestream_path* **'** }  
 オペレーティング システムの (物理) ファイル名を指定します。  
  
 **'** *os_file_name* **'**  
 ファイルを作成する際にオペレーティング システムが使用するパスとファイル名です。 ファイルは、次のデバイスのいずれかに存在する必要があります。 ローカル サーバーを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされている記憶域エリア ネットワーク (SAN)、または iSCSI ベースのネットワーク。 指定したパスは、CREATE DATABASE ステートメントを実行する前に存在する必要があります。 詳細については、「解説」の「データベース ファイルとファイル グループ」を参照してください。  
  
 ファイルに対して UNC パスが指定されている場合は、SIZE、MAXSIZE、および FILEGROWTH パラメーターを設定できます。  
  
 ファイルが未処理のパーティション上にある場合*os_file_name*既存のパーティションのドライブ文字のみを指定する必要があります。 1 つの未処理のパーティションに作成できるのは 1 つのデータ ファイルだけです。  
  
 ファイルが読み取り専用のセカンダリ ファイルであるか、データベースが読み取り専用である場合を除き、データ ファイルを圧縮ファイル システム上に置かないでください。 ログ ファイルは、圧縮ファイル システム上に置くことはできません。  
  
 **'** *filestream_path* **'**  
 FILESTREAM ファイル グループの場合、FILENAME は FILESTREAM データが格納されるパスを参照します。 最後のフォルダーまでのパスが存在する必要がありますが、最後のフォルダーは存在できません。 たとえば、パス C:\MyFiles\MyFilestreamData を指定する場合は、ALTER DATABASE を実行するとき、C:\MyFiles は既に存在している必要がありますが、MyFilestreamData フォルダーは存在してはなりません。  
  
 ファイル グループとファイル (`<filespec>`) は、同じステートメントで作成する必要があります。  
  
 SIZE プロパティおよび FILEGROWTH プロパティは、FILESTREAM ファイル グループには適用されません。  
  
 サイズ*サイズ*  
 ファイルのサイズを指定します。  
  
 サイズにすることはできない時に指定された、 *os_file_name*は UNC パスとして指定します。 SIZE は、FILESTREAM ファイル グループには適用されません。  
  
 *サイズ*  
 ファイルの初期サイズです。  
  
 ときに*サイズ*プライマリ ファイルが指定されていない、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] model データベースのプライマリ ファイルのサイズが使用されます。 モデルの既定のサイズは 8 MB (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) または 1 MB (以前のバージョン)。 セカンダリ データ ファイルまたはログ ファイルを指定するが*サイズ*、ファイルが指定されていない、[!INCLUDE[ssDE](../../includes/ssde-md.md)]ファイルは、8 MB (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]) または 1 MB (以前のバージョン)。 なお、プライマリ ファイルに対して指定するサイズは、model データベースのプライマリ ファイルのサイズ以上である必要があります。  
  
 サフィックスとして、KB、MB、GB、または TB を使用できます。 既定値は MB です。 整数を指定します。小数を含めないでください。 *サイズ*整数値です。 2,147,483,647 を超える値に対しては、より大きな単位を使用してください。  
  
 MAXSIZE *max_size*  
 ファイルのサイズの上限を指定します。 MAXSIZE をすることはできない時に指定された、 *os_file_name*は UNC パスとして指定します。  
  
 *max_size*  
 ファイルの最大サイズです。 サフィックスとして、KB、MB、GB、および TB を使用できます。 既定値は MB です。 整数を指定します。小数を含めないでください。 場合*max_size*が指定されていない、ディスクがいっぱいになるまでに、ファイルが拡張されます。 *Max_size*整数値です。 2,147,483,647 を超える値に対しては、より大きな単位を使用してください。  
  
 UNLIMITED  
 ディスクがいっぱいになるまでファイルを拡張するように指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、無制限に拡張するファイル固有のログの最大サイズは 2 TB で、データ ファイルの最大サイズは 16 TB です。  
  
> [!NOTE]  
>  FILESTREAM コンテナーに対してこのオプションを指定した場合、最大サイズはありません。 ディスクがいっぱいになるまでファイル サイズが拡張します。  
  
 FILEGROWTH *growth_increment*  
 ファイルを自動拡張するときの増加量を指定します。 ファイルの FILEGROWTH の設定を MAXSIZE の設定より大きくすることはできません。 FILEGROWTH をすることはできない時に指定された、 *os_file_name*は UNC パスとして指定します。 FILEGROWTH は、FILESTREAM ファイル グループには適用されません。  
  
 *growth_increment*  
 新しい領域が必要とされるたびにファイルに追加される領域の容量です。  
  
 値は MB、KB、GB、TB または % の単位で指定できます。 サフィックス MB、KB、または % を付けないで数値を指定した場合の既定値は MB です。 % を指定すると、1 回の増加量は、増加時のファイル サイズに指定されたパーセンテージを掛けた値になります。 指定されたサイズが、最も近い 64 KB に丸められ、最小値は 64 KB です。  
  
 0 は、自動拡張がオフで、領域を追加できないことを示します。  
  
 FILEGROWTH が指定されていない場合、既定値です。  
  
|バージョン|[既定値]|  
|-------------|--------------------|  
|先頭[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|データ 64 MB です。 ログ ファイルの 64 MB です。|  
|先頭[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|データ 1 MB です。 ログ ファイルを 10% です。|  
|前のバージョン[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|データ 10% です。 ログ ファイルを 10% です。|  
  
 \<ファイル グループ >  
 ファイル グループ プロパティを制御します。 ファイル グループは、データベース スナップショットでは指定できません。  
  
 ファイル グループ*filegroup_name*  
 ファイル グループの論理名です。  
  
 *filegroup_name*  
 *filegroup_name*データベース内で一意である必要があり、システムによって提供される名前ある PRIMARY や PRIMARY_LOG にすることはできません。 この名前は、文字定数、UNICODE 定数、標準の識別子、区切られた識別子のいずれでもかまいません。 名前は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。  
  
 CONTAINS FILESTREAM  
 ファイル グループで FILESTREAM バイナリ ラージ オブジェクト (BLOB) をファイル システムに格納することを指定します。  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ファイル グループでメモリ最適化データをファイル システムに格納することを指定します。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。 MEMORY_OPTIMIZED_DATA ファイル グループは、1 つのデータベースにつき 1 つしか許可されません。 メモリ最適化データを格納するファイル グループを作成するコード サンプルでは、次を参照してください。[メモリ最適化テーブルおよびネイティブ コンパイル ストアド プロシージャの作成](../../relational-databases/in-memory-oltp/creating-a-memory-optimized-table-and-a-natively-compiled-stored-procedure.md)です。  
  
 DEFAULT  
 指定されたファイル グループが、データベースの既定のファイル グループであることを指定します。  
  
 *database_snapshot_name*  
 新規データベース スナップショットの名前です。 データベース スナップショット名は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意であり、識別子のルールに従っている必要があります。 *database_snapshot_name*最大 128 文字まで指定できます。  
  
 ON **(**名前 **=**  *logical_file_name***、** FILENAME **='** *os_file_name***')** [ **、**.*n* ]  
 データベース スナップショットを作成するには、ソース データベースのファイルのリストを指定します。 スナップショットが機能するためには、すべてのデータ ファイルは個別に指定する必要があります。 ただし、データベース スナップショットにログ ファイルは指定できません。 FILESTREAM ファイル グループは、データベース スナップショットではサポートされていません。 CREATE DATABASE ON 句に FILESTREAM データ ファイルが含まれていると、ステートメントが失敗してエラーが発生します。  
  
 名とファイル名とその値の説明は、それと同等の説明を参照してください\<filespec > 値。  
  
> [!NOTE]  
>  他のデータベース スナップショットを作成するときに\<filespec > オプションおよびキーワード PRIMARY は許可されません。  
  
 AS SNAPSHOT OF *source_database_name*  
 作成するデータベースがで指定されたソース データベースのデータベース スナップショット*source_database_name*です。 スナップショットとソース データベースは同じインスタンス上に存在する必要があります。  
  
 詳細については、「解説」の「データベース スナップショット」を参照してください。  
  
## <a name="remarks"></a>解説  
 [Master データベース](../../relational-databases/databases/master-database.md)バックアップするか、ユーザー データベースを作成、変更、または削除されるたびにします。  
  
 CREATE DATABASE ステートメントは自動コミット モード (既定のトランザクション管理モード) で実行する必要があり、明示的または暗黙的なトランザクション モードでは許可されません。  
  
 1 つの CREATE DATABASE ステートメントを使用して、データベースおよびデータベースを格納するファイルを作成することができます。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、次の手順を使用して CREATE DATABASE ステートメントを実装します。  
  
1.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のコピーを使用して、 [model データベース](../../relational-databases/databases/model-database.md)データベースとそのメタデータを初期化します。  
  
2.  Service Broker GUID がデータベースに割り当てられます。  
  
3.  [!INCLUDE[ssDE](../../includes/ssde-md.md)]をデータベース内の領域の使用方法を記録する内部データを含むページ以外の空のページで、データベースの残りの部分を入力します。  
  
 インスタンスには、最大 32,767 個のデータベースを指定できます [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 各データベースには、データベース内で特殊な操作を実行できる所有者が存在します。 所有者はデータベースを作成するユーザーです。 使用して、データベース所有者を変更できる[sp_changedbowner](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)です。  

一部のデータベース機能は、機能によって異なります。 または、データベースの完全な機能をファイル システムで機能を表示します。 ファイル システムの機能セットに依存する機能のいくつかの例は次のとおりです。
- DBCC CHECKDB
- FileStream
- VSS とファイルのスナップショットを使用してオンライン バックアップ
- データベース スナップショットの作成
- メモリ最適化データ ファイル グループ
   
## <a name="database-files-and-filegroups"></a>データベース ファイルとファイル グループ  
 各データベースには、少なくとも 2 つのファイルには、*プライマリ ファイル*と*トランザクション ログ ファイル*とには、少なくとも 1 つのファイル グループ。 各データベースに、最大 32,767 のファイルと 32,767 のファイル グループを指定できます。  
  
 データベースを作成する際に、データ ファイルのサイズは、データベースに記述されるデータの最大量を基に可能な限り大きく設定しておきます。  
  
 記憶域の記憶域エリア ネットワーク (SAN)、iSCSI ベースのネットワークまたはローカルに接続されたディスクを使用することをお勧め、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を最適化するためのデータベース ファイル、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パフォーマンスと信頼性です。  
  
## <a name="database-snapshots"></a>データベース スナップショット  
 読み取り専用、静的なビューを作成する CREATE DATABASE ステートメントを使用することができます、*データベース スナップショット*の*ソース データベース*です。 データベース スナップショットは、スナップショットが作成された時点で存在していたソース データベースと、トランザクション的に一貫性があります。 ソース データベースは複数のスナップショットを持つことができます。  
  
> [!NOTE]  
>  データベース スナップショットを作成する際、CREATE DATABASE ステートメントは、ログ ファイル、オフライン ファイル、復元ファイル、および現存しないファイルを参照することはできません。  
  
 データベース スナップショットの作成に失敗した場合、スナップショットは問題ありになります、削除する必要があります。 詳細については、次を参照してください。 [DROP DATABASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-database-transact-sql.md).  
  
 各スナップショットは、削除されるまで、DROP DATABASE を使用して保持されます。  
  
 詳細については、「[データベース スナップショット &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)」を参照してください。  
  
## <a name="database-options"></a>データベース オプション  
 データベースを作成するたびに、いくつかのデータベース オプションが自動的に設定されます。 これらのオプションの一覧は、次を参照してください。 [ALTER DATABASE SET Options & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql-set-options.md).  
  
## <a name="the-model-database-and-creating-new-databases"></a>model データベースと新しいデータベースの作成  
 内のすべてのユーザー定義オブジェクト、 [model データベース](../../relational-databases/databases/model-database.md)新しく作成されたすべてのデータベースにコピーされます。 テーブル、ビュー、ストアド プロシージャ、データ型など、あらゆるオブジェクトを model データベースに追加し、新しく作成されたすべてのデータベースに含めることができます。  
  
 CREATE database *database_name*ステートメントなしで指定されたサイズ パラメーターを追加、プライマリ データ ファイルには、モデル データベースで、プライマリ ファイルと同じサイズが行われます。  
  
 FOR ATTACH が指定されていない限り、すべての新しいデータベースは、model データベースからデータベース オプションの設定を継承します。 たとえば、auto shrink データベース オプションに設定されている**true**モデルおよびすべての新しいデータベースを作成します。 model データベースのオプションを変更すると、これらの新しいオプション設定が、作成する新規のデータベースで使用されます。 model データベースの操作の変更は、既存のデータベースには影響を与えません。 CREATE DATABASE ステートメントで FOR ATTACH を指定すると、新しいデータベースは元のデータベースからデータベース オプションの設定を継承します。  
  
## <a name="viewing-database-information"></a>データベース情報の表示  
 カタログ ビュー、システム関数、およびシステム ストアド プロシージャを使用して、データベース、ファイルおよびファイル グループについての情報を返すことができます。 詳細については、「[システム ビュー &#40;Transact-SQL&#41;](http://msdn.microsoft.com/library/35a6161d-7f43-4e00-bcd3-3091f2015e90)」を参照してください。  
  
## <a name="permissions"></a>Permissions  
 CREATE DATABASE、CREATE ANY DATABASE、または ALTER ANY DATABASE の各権限が必要です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンス上のディスク使用量を管理するため、通常、データベースを作成する権限をいくつかのログイン アカウントに制限します。  
  
 次の例は、データベース ユーザー Fay にデータベースを作成する権限を与えます。  
  
```  
USE master;  
GO  
GRANT CREATE DATABASE TO [Fay];  
GO  
```  
  
### <a name="permissions-on-data-and-log-files"></a>データおよびログ ファイルに対する権限  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、特定の権限が各データベースのデータとログ ファイルに設定します。 次の操作がデータベースに適用されるたびに、次の権限が設定されます。  
  
|||  
|-|-|  
|Created|変更して新しいファイルを追加|  
|アタッチ|バックアップ|  
|デタッチ|復元|  
  
 この権限は、開く権限のあるディレクトリにファイルが存在する場合に、そのファイルが誤って書き換えられるのを防ぎます。  
  
> [!NOTE]  
>  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssExpressEd2005](../../includes/ssexpressed2005-md.md)] では、データ ファイルとログ ファイルの権限は設定されません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-creating-a-database-without-specifying-files"></a>A. ファイルを指定せずにデータベースを作成する  
 次の例では、`mytest` データベースを作成し、対応するプライマリ ファイルおよびトランザクション ログ ファイルを作成します。 ステートメントがあるないのため\<filespec > 項目、プライマリ データベース ファイルは、モデル データベースのプライマリ ファイルのサイズ。 トランザクション ログは、512KB、またはプライマリ データ ファイルのサイズの 25% の値の大きい方に設定されます。 MAXSIZE が指定されていないため、ファイルはディスク上のすべての使用可能な領域いっぱいまで拡張することができます。 この例では、`mytest` という名前のデータベースが既に存在する場合はそれを削除してから、`mytest` データベースを作成する方法も示します。  
  
```  
USE master;  
GO  
CREATE DATABASE mytest;  
GO  
-- Verify the database files and sizes  
SELECT name, size, size*1.0/128 AS [Size in MBs]   
FROM sys.master_files  
WHERE name = N'mytest';  
GO  
  
```  
  
### <a name="b-creating-a-database-that-specifies-the-data-and-transaction-log-files"></a>B. データ ファイルとトランザクション ログ ファイルを指定してデータベースを作成する  
 次の例は、データベースを作成`Sales`です。 PRIMARY キーワードがない使用されるため、最初のファイル (`Sales_dat`) がプライマリ ファイルとなります。 `Sales_dat` ファイルの SIZE パラメーターに MB も KB も指定されていないため、ファイルは MB を使用し、メガバイト単位で割り当てられます。 `Sales_log` ファイルは、`SIZE` パラメーターに `MB` サフィックスが明示的に指定されているため、メガバイト単位で割り当てられます。  
  
```tsql  
USE master;  
GO  
CREATE DATABASE Sales  
ON   
( NAME = Sales_dat,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\saledat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="c-creating-a-database-by-specifying-multiple-data-and-transaction-log-files"></a>C. 複数のデータ ファイルとトランザクション ログ ファイルを指定してデータベースを作成する  
 次の例では、3 つの `Archive` のデータ ファイルと 2 つの `100-MB` のトランザクション ログ ファイルがある `100-MB` データベースを作成します。 プライマリ ファイルはリストの最初のファイルであり、`PRIMARY` キーワードによって明示的に指定されます。 次のトランザクション ログ ファイルが指定された、`LOG ON`キーワード。 内のファイルで使用される拡張子に注意してください、`FILENAME`オプション:`.mdf`プライマリ データ ファイルを使用`.ndf`セカンダリ データ ファイルを使用し、`.ldf`トランザクション ログ ファイルを使用します。 この例にデータベースを格納する、`D:`の代わりにドライブを`master`データベース。  
  
```tsql  
USE master;  
GO  
CREATE DATABASE Archive   
ON  
PRIMARY    
    (NAME = Arch1,  
    FILENAME = 'D:\SalesData\archdat1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch2,  
    FILENAME = 'D:\SalesData\archdat2.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
    ( NAME = Arch3,  
    FILENAME = 'D:\SalesData\archdat3.ndf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20)  
LOG ON   
   (NAME = Archlog1,  
    FILENAME = 'D:\SalesData\archlog1.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20),  
   (NAME = Archlog2,  
    FILENAME = 'D:\SalesData\archlog2.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 200,  
    FILEGROWTH = 20) ;  
GO  
```  
  
### <a name="d-creating-a-database-that-has-filegroups"></a>D. ファイル グループのあるデータベースを作成する  
 次の例は、データベースを作成`Sales`次のファイル グループを含みます。  
  
-   プライマリ ファイル グループのファイルを`Spri1_dat`と`Spri2_dat`です。 これらのファイルの FILEGROWTH 増加量は、`15%` に指定されています。  
  
-   名前のファイル グループ`SalesGroup1`ファイルと`SGrp1Fi1`と`SGrp1Fi2`です。  
  
-   名前のファイル グループ`SalesGroup2`ファイルと`SGrp2Fi1`と`SGrp2Fi2`です。  
  
 この例では、データ ファイルとログ ファイルは、パフォーマンスを向上させるために別のディスクに格納します。  
  
```tsql  
USE master;  
GO  
CREATE DATABASE Sales  
ON PRIMARY  
( NAME = SPri1_dat,  
    FILENAME = 'D:\SalesData\SPri1dat.mdf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
( NAME = SPri2_dat,  
    FILENAME = 'D:\SalesData\SPri2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 15% ),  
FILEGROUP SalesGroup1  
( NAME = SGrp1Fi1_dat,  
    FILENAME = 'D:\SalesData\SG1Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp1Fi2_dat,  
    FILENAME = 'D:\SalesData\SG1Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
FILEGROUP SalesGroup2  
( NAME = SGrp2Fi1_dat,  
    FILENAME = 'D:\SalesData\SG2Fi1dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 ),  
( NAME = SGrp2Fi2_dat,  
    FILENAME = 'D:\SalesData\SG2Fi2dt.ndf',  
    SIZE = 10,  
    MAXSIZE = 50,  
    FILEGROWTH = 5 )  
LOG ON  
( NAME = Sales_log,  
    FILENAME = 'E:\SalesLog\salelog.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 25MB,  
    FILEGROWTH = 5MB ) ;  
GO  
```  
  
### <a name="e-attaching-a-database"></a>E. データベースをアタッチする  
 次の例では、例 D で作成された `Archive` データベースをデタッチしてから、`FOR ATTACH` 句を使用してこのデータベースをアタッチします。 `Archive`複数のデータに定義されたファイルとログ ファイルです。 ただし、作成された後に、ファイルの場所が変更されていないため、プライマリ ファイルのみがで指定する、`FOR ATTACH`句。 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] 以降では、アタッチされているデータベースの一部であるフルテキスト ファイルは、データベースと共にアタッチされます。  
  
```tsql  
USE master;  
GO  
sp_detach_db Archive;  
GO  
CREATE DATABASE Archive  
      ON (FILENAME = 'D:\SalesData\archdat1.mdf')   
      FOR ATTACH ;  
GO  
```  
  
### <a name="f-creating-a-database-snapshot"></a>F. データベース スナップショットを作成する  
 次の例は、データベース スナップショットを作成`sales_snapshot0600`です。 データベース スナップショットは読み取り専用であるため、ログ ファイルは指定できません。 構文に準拠して、ソース データベース内のすべてのファイルが指定され、ファイル グループは指定されません。  
  
 この例のソース データベースは、`Sales`例 D で作成されたデータベース  
  
```tsql  
USE master;  
GO  
CREATE DATABASE sales_snapshot0600 ON  
    ( NAME = SPri1_dat, FILENAME = 'D:\SalesData\SPri1dat_0600.ss'),  
    ( NAME = SPri2_dat, FILENAME = 'D:\SalesData\SPri2dt_0600.ss'),  
    ( NAME = SGrp1Fi1_dat, FILENAME = 'D:\SalesData\SG1Fi1dt_0600.ss'),  
    ( NAME = SGrp1Fi2_dat, FILENAME = 'D:\SalesData\SG1Fi2dt_0600.ss'),  
    ( NAME = SGrp2Fi1_dat, FILENAME = 'D:\SalesData\SG2Fi1dt_0600.ss'),  
    ( NAME = SGrp2Fi2_dat, FILENAME = 'D:\SalesData\SG2Fi2dt_0600.ss')  
AS SNAPSHOT OF Sales ;  
GO  
```  
  
### <a name="g-creating-a-database-and-specifying-a-collation-name-and-options"></a>G. データベースを作成し、照合順序名とオプションを指定する  
 次の例は、データベースを作成`MyOptionsTest`です。 照合順序名が指定され、`TRUSTYWORTHY` および `DB_CHAINING` オプションが `ON` に設定されます。  
  
```tsql  
USE master;  
GO  
IF DB_ID (N'MyOptionsTest') IS NOT NULL  
DROP DATABASE MyOptionsTest;  
GO  
CREATE DATABASE MyOptionsTest  
COLLATE French_CI_AI  
WITH TRUSTWORTHY ON, DB_CHAINING ON;  
GO  
--Verifying collation and option settings.  
SELECT name, collation_name, is_trustworthy_on, is_db_chaining_on  
FROM sys.databases  
WHERE name = N'MyOptionsTest';  
GO  
  
```  
  
### <a name="h-attaching-a-full-text-catalog-that-has-been-moved"></a>H. 移動されたフルテキスト カタログをアタッチする  
 次の例は、フルテキスト カタログをアタッチ`AdvWksFtCat`と共に、`AdventureWorks2012`データとログ ファイルです。 この例では、フルテキスト カタログは、既定の場所から新しい場所、`c:\myFTCatalogs` に移されます。 データおよびログ ファイルは、それぞれの既定の場所に残ります。  
  
```tsql  
USE master;  
GO  
--Detach the AdventureWorks2012 database  
sp_detach_db AdventureWorks2012;  
GO  
-- Physically move the full text catalog to the new location.  
--Attach the AdventureWorks2012 database and specify the new location of the full-text catalog.  
CREATE DATABASE AdventureWorks2012 ON   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_data.mdf'),   
    (FILENAME = 'c:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\AdventureWorks2012_log.ldf'),  
    (FILENAME = 'c:\myFTCatalogs\AdvWksFtCat')  
FOR ATTACH;  
GO  
```  
  
### <a name="i-creating-a-database-that-specifies-a-row-filegroup-and-two-filestream-filegroups"></a>I. 1 つの ROW ファイル グループと 2 つの FILESTREAM ファイル グループを指定してデータベースを作成する  
 次の例を作成、`FileStreamDB`データベース。 データベースは、1 つの ROW ファイル グループと 2 つの FILESTREAM ファイル グループを使用して作成されます。 各ファイル グループには、1 つのファイルが含まれます。  
  
-   `FileStreamDB_data`行のデータが含まれています。 これには、既定のパスを指定した 1 つのファイル `FileStreamDB_data.mdf` が含まれます。  
  
-   `FileStreamPhotos`FILESTREAM データが含まれています。 これには、`FSPhotos` (`C:\MyFSfolder\Photos` にある) と `FSPhotos2` (`D:\MyFSfolder\Photos` にある) の 2 つの FILESTREAM データ コンテナーが含まれます。 また、既定の FILESTREAM ファイル グループとしてマークします。  
  
-   `FileStreamResumes`FILESTREAM データが含まれています。 これには、1 つの FILESTREAM データ コンテナー `FSResumes` (`C:\MyFSfolder\Resumes` にある) が含まれます。  
  
```tsql  
USE master;  
GO  
-- Get the SQL Server data path.  
DECLARE @data_path nvarchar(256);  
SET @data_path = (SELECT SUBSTRING(physical_name, 1, CHARINDEX(N'master.mdf', LOWER(physical_name)) - 1)  
                  FROM master.sys.master_files  
                  WHERE database_id = 1 AND file_id = 1);  
  
 -- Execute the CREATE DATABASE statement.   
EXECUTE ('CREATE DATABASE FileStreamDB  
ON PRIMARY   
    (  
    NAME = FileStreamDB_data   
    ,FILENAME = ''' + @data_path + 'FileStreamDB_data.mdf''  
    ,SIZE = 10MB  
    ,MAXSIZE = 50MB  
    ,FILEGROWTH = 15%  
    ),  
FILEGROUP FileStreamPhotos CONTAINS FILESTREAM DEFAULT  
    (  
    NAME = FSPhotos  
    ,FILENAME = ''C:\MyFSfolder\Photos''  
-- SIZE and FILEGROWTH should not be specified here.  
-- If they are specified an error will be raised.  
, MAXSIZE = 5000 MB  
    ),  
    (  
      NAME = FSPhotos2  
      , FILENAME = ''D:\MyFSfolder\Photos''  
      , MAXSIZE = 10000 MB  
     ),  
FILEGROUP FileStreamResumes CONTAINS FILESTREAM  
    (  
    NAME = FileStreamResumes  
    ,FILENAME = ''C:\MyFSfolder\Resumes''  
    )   
LOG ON  
    (  
    NAME = FileStream_log  
    ,FILENAME = ''' + @data_path + 'FileStreamDB_log.ldf''  
    ,SIZE = 5MB  
    ,MAXSIZE = 25MB  
    ,FILEGROWTH = 5MB  
    )'  
);  
GO  
```  
  
### <a name="j-creating-a-database-that-has-a-filestream-filegroup-with-multiple-files"></a>J. 複数のファイルを含む FILESTREAM ファイル グループのあるデータベースを作成する  
 次の例を作成、`BlobStore1`データベース。 1 つの row ファイル グループと、1 つの FILESTREAM ファイル グループとデータベースが作成された`FS`です。 FILESTREAM ファイル グループには、2 つのファイルが含まれています。`FS1`と`FS2`です。 その後 `FS3` という 3 つ目のファイルが FILESTREAM ファイルグループに追加されると、データベースが変更されます。  
  
```tsql  
USE master;  
GO  
  
CREATE DATABASE [BlobStore1]  
CONTAINMENT = NONE  
ON PRIMARY   
(   
    NAME = N'BlobStore1',   
    FILENAME = N'C:\BlobStore\BlobStore1.mdf',  
    SIZE = 100MB,  
    MAXSIZE = UNLIMITED,  
    FILEGROWTH = 1MB  
),   
FILEGROUP [FS] CONTAINS FILESTREAM DEFAULT   
(  
    NAME = N'FS1',  
    FILENAME = N'C:\BlobStore\FS1',  
    MAXSIZE = UNLIMITED  
),   
(  
    NAME = N'FS2',  
    FILENAME = N'C:\BlobStore\FS2',  
    MAXSIZE = 100MB  
)  
LOG ON   
(  
    NAME = N'BlobStore1_log',  
    FILENAME = N'C:\BlobStore\BlobStore1_log.ldf',  
    SIZE = 100MB,  
    MAXSIZE = 1GB,  
    FILEGROWTH = 1MB  
);  
GO  
  
ALTER DATABASE [BlobStore1]  
ADD FILE  
(  
    NAME = N'FS3',  
    FILENAME = N'C:\BlobStore\FS3',  
    MAXSIZE = 100MB  
)  
TO FILEGROUP [FS];  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [データベースのデタッチとアタッチ &#40;SQL Server&#41;](../../relational-databases/databases/database-detach-and-attach-sql-server.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_changedbowner & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-changedbowner-transact-sql.md)   
 [sp_detach_db & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-detach-db-transact-sql.md)   
 [sp_removedbreplication & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-removedbreplication-transact-sql.md)   
 [Database Snapshots &#40;SQL Server&#41;](../../relational-databases/databases/database-snapshots-sql-server.md)   
 [データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)   
 [データベース](../../relational-databases/databases/databases.md)   
 [バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)  



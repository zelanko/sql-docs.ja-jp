---
title: "ALTER DATABASE の File および Filegroup オプション (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/07/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ADD FILE
- ADD_FILE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- deleting files
- removing files
- deleting filegroups
- file modifications [SQL Server]
- databases [SQL Server], size
- relocating files
- databases [SQL Server], modifying
- file additions [SQL Server], ALTER DATABASE
- file moving [SQL Server]
- default filegroups
- ALTER DATABASE statement, files and filegroups
- initializing files [SQL Server]
- database files [SQL Server]
- moving files
- filegroups [SQL Server], deleting
- adding filegroups
- adding files
- database filegroups [SQL Server]
- adding log files
- modifying files
- filegroups [SQL Server], adding
- file initialization [SQL Server]
- files [SQL Server], deleting
- files [SQL Server], adding
- databases [SQL Server], moving
ms.assetid: 1f635762-f7aa-4241-9b7a-b51b22292b07
caps.latest.revision: 61
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: fdd1f2aaab4e4aeeced6eb069255adba5b333abf
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-database-transact-sql-file-and-filegroup-options"></a>ALTER DATABASE (TRANSACT-SQL) の File および Filegroup オプション 
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ファイルおよびファイル グループ内のデータベースに関連付けられている変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 データベースに対するファイルやファイル グループの追加と削除、およびデータベースおよびデータベースのファイルやファイル グループの属性の変更を行います。 その他の ALTER DATABASE オプションについては、次を参照してください。 [ALTER DATABASE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/alter-database-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
ALTER DATABASE database_name   
{  
    <add_or_modify_files>  
  | <add_or_modify_filegroups>  
}  
[;]  
  
<add_or_modify_files>::=  
{  
    ADD FILE <filespec> [ ,...n ]   
        [ TO FILEGROUP { filegroup_name } ]  
  | ADD LOG FILE <filespec> [ ,...n ]   
  | REMOVE FILE logical_file_name   
  | MODIFY FILE <filespec>  
}  
  
<filespec>::=   
(  
    NAME = logical_file_name    
    [ , NEWNAME = new_logical_name ]   
    [ , FILENAME = {'os_file_name' | 'filestream_path' | 'memory_optimized_data_path' } ]   
    [ , SIZE = size [ KB | MB | GB | TB ] ]   
    [ , MAXSIZE = { max_size [ KB | MB | GB | TB ] | UNLIMITED } ]   
    [ , FILEGROWTH = growth_increment [ KB | MB | GB | TB| % ] ]   
    [ , OFFLINE ]  
)   
  
<add_or_modify_filegroups>::=  
{  
    | ADD FILEGROUP filegroup_name   
        [ CONTAINS FILESTREAM | CONTAINS MEMORY_OPTIMIZED_DATA ]  
    | REMOVE FILEGROUP filegroup_name   
    | MODIFY FILEGROUP filegroup_name  
        { <filegroup_updatability_option>  
        | DEFAULT  
        | NAME = new_filegroup_name   
        | { AUTOGROW_SINGLE_FILE | AUTOGROW_ALL_FILES }  
        }  
}  
<filegroup_updatability_option>::=  
{  
    { READONLY | READWRITE }   
    | { READ_ONLY | READ_WRITE }  
}  
  
```  
  
## <a name="arguments"></a>引数  
**\<add_or_modify_files >:: =**
  
 追加、削除、または変更するファイルを指定します。  
  
 *database_name*  
 変更するデータベースの名前を指定します。  
  
 ADD FILE  
 データベースにファイルを追加します。  
  
 ファイル グループに { *filegroup_name* }  
 指定されたファイルを追加するファイル グループを指定します。 表示するには、現在のファイル グループとファイル グループは現在の既定値を使用して、 [sys.filegroups](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)カタログ ビューです。  
  
 ADD LOG FILE  
 指定されたデータベースにログ ファイルを追加します。  
  
 REMOVE FILE *logical_file_name*  
 インスタンスの論理ファイルの説明を削除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]物理ファイルを削除します。 ファイルが空でない場合は削除できません。  
  
 *logical_file_name*  
 使用される論理名は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ファイルを参照するときにします。  
  
> [!WARNING]  
>  FILE_SNAPSHOT のあるデータベース ファイルを削除する関連付けられているバックアップは成功しますが、関連付けられたスナップショットを参照するデータベース ファイルのバックアップを無効化を回避するのには削除されません。 ファイルでは、切り捨てられますが、FILE_SNAPSHOT のバックアップをそのままの状態に保つために物理的に削除されません。 詳細については、「 [Microsoft Azure Blob Storage サービスを使用した SQL Server のバックアップと復元](../../relational-databases/backup-restore/sql-server-backup-and-restore-with-microsoft-azure-blob-storage-service.md)」を参照してください。 **適用されます**:[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)します。  
  
 MODIFY FILE  
 変更するファイルを指定します。 1 つだけ\<filespec > プロパティを一度に変更できます。 常にで名前を指定する必要があります、 \<filespec > を変更するファイルを識別します。 SIZE を指定する場合、ファイルの現在のサイズより新しいサイズの方が大きくなければなりません。  
  
 データ ファイルまたはログ ファイルの論理名を変更するには、変更するファイルの論理名を `NAME` 句で指定し、`NEWNAME` 句にそのファイルの新しい論理名を指定します。 例:  
  
```  
MODIFY FILE ( NAME = logical_file_name, NEWNAME = new_logical_name )   
```  
  
 データ ファイルまたはログ ファイルを別の場所に移動するには、`NAME` 句にファイルの現在の論理名を指定し、`FILENAME` 句に新しいパスとオペレーティング システム ファイル名を指定します。 例:  
  
```  
MODIFY FILE ( NAME = logical_file_name, FILENAME = ' new_path/os_file_name ' )  
```  
  
 フルテキスト カタログを移動する場合は、FILENAME 句に新しいパスだけを指定します。 オペレーティング システム ファイル名は指定しないでください。  
  
 詳細については、次を参照してください。[データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)です。  
  
 FILESTREAM ファイル グループの場合、NAME をオンラインで変更できます。 FILENAME はオンラインで変更できますが、コンテナーを物理的に再配置し、サーバーをシャットダウンして再起動するまで、変更は有効になりません。  
  
 FILESTREAM ファイルを OFFLINE に設定できます。 FILESTREAM ファイルをオフラインにすると、その親ファイル グループがオフラインとして内部的にマークされるため、そのファイル グループ内の FILESTREAM データへのアクセスはすべて失敗します。  
  
> [!NOTE]  
>  \<add_or_modify_files > オプションは、包含データベースで使用できません。
  
 **\<filespec >:: =**  
  
 ファイル プロパティを制御します。  
  
 名前*logical_file_name*  
 ファイルの論理名を指定します。  
  
 *logical_file_name*  
 ファイルを参照するときに [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスで使用される論理名を指定します。  
  
 NEWNAME *new_logical_file_name*  
 ファイルの新しい論理名を指定します。  
  
 *new_logical_file_name*  
 既存の論理ファイル名と置換する新しい名前を指定します。 名前必要があります、データベース内で一意であるし、規則に従う[識別子](../../relational-databases/databases/database-identifiers.md)です。 この名前は、文字定数、Unicode 定数、標準の識別子、区切られた識別子のいずれでもかまいません。  
  
 ファイル名 { **'***os_file_name***'** | **'***filestream_path* **'** | **'***memory_optimized_data_path***'**}  
 オペレーティング システムの (物理) ファイル名を指定します。  
  
 ' *os_file_name* '  
 標準の (ROWS) ファイル グループの場合、ファイルの作成時にオペレーティング システムで使用されるパスとファイル名を指定します。 ファイルは、先のサーバーに存在する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]がインストールされています。 ALTER DATABASE ステートメントを実行するには、指定したパスが実際に存在するパスであることが必要です。  
  
 ファイルに対して UNC パスが指定されている場合、SIZE、MAXSIZE、および FILEGROWTH パラメーターは設定できません。  
  
> [!NOTE]  
>  システム データベースを UNC 共有ディレクトリに置くことはできません。  
  
 データ ファイルが読み取り専用のセカンダリ ファイルであるか、データベースが読み取り専用である場合を除き、データ ファイルを圧縮ファイル システム上には置かないでください。 ログ ファイルは、圧縮ファイル システム上に置くことはできません。  
  
 ファイルが未処理のパーティション上にある場合*os_file_name*既存のパーティションのドライブ文字のみを指定する必要があります。 未処理の各パーティションに配置できるファイルは、それぞれ 1 ファイルだけです。  
  
 **'** *filestream_path* **'**  
 FILESTREAM ファイル グループの場合、FILENAME は FILESTREAM データが格納されるパスを参照します。 最後のフォルダーまでのパスが存在する必要がありますが、最後のフォルダーは存在できません。 たとえば、パス C:\MyFiles\MyFilestreamData を指定する場合は、ALTER DATABASE を実行するとき、C:\MyFiles は既に存在している必要がありますが、MyFilestreamData フォルダーは存在してはなりません。  
  
 SIZE プロパティおよび FILEGROWTH プロパティは、FILESTREAM ファイル グループには適用されません。  
  
 **'** *memory_optimized_data_path* **'**  
 メモリ最適化ファイル グループでは、FILENAME はメモリ最適化データが格納されるパスを示します。 最後のフォルダーまでのパスが存在する必要がありますが、最後のフォルダーは存在できません。 たとえば、パス C:\MyFiles\MyData を指定する場合は、ALTER DATABASE を実行するとき、C:\MyFiles は既に存在している必要がありますが、MyData フォルダーは存在できません。  
  
 ファイル グループとファイル (`<filespec>`) は、同じステートメントで作成する必要があります。  
  
 SIZE、MAXSIZE、FILEGROWTH の各プロパティは、メモリ最適化ファイル グループには適用されません。  
  
 サイズ*サイズ*  
 ファイルのサイズを指定します。 サイズは、FILESTREAM ファイル グループには適用されません。  
  
 *サイズ*  
 ファイルのサイズです。  
  
 ADD FILE と共に指定すると*サイズ*ファイルの初期サイズします。 MODIFY FILE と共に指定すると*サイズ*ファイルは、新しいサイズは、現在のファイル サイズより大きくする必要があります。  
  
 ときに*サイズ*プライマリ ファイルが指定されていない、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のプライマリ ファイルのサイズを使用して、**モデル**データベース。 セカンダリ データ ファイルまたはログ ファイルが指定されている場合は*サイズ*、ファイルが指定されていない、[!INCLUDE[ssDE](../../includes/ssde-md.md)]により、ファイル 1 MB です。  
  
 KB、MB、GB、および TB の各サフィックスを使用して、キロバイト、メガバイト、ギガバイト、またはテラバイトを指定できます。 既定値は MB です。 整数を指定します。小数は含めないでください。 小数部を持つメガバイトの値を指定するには、その値に 1024 を乗算することによって、キロバイトの単位に変換します。 たとえば、1.5 MB ではなく 1536 KB と指定します (1.5 × 1024 = 1536)。  
  
 MAXSIZE { *max_size*|無制限}  
 ファイルのサイズを拡張する場合の最大サイズを指定します。  
  
 *max_size*  
 ファイルの最大サイズです。 KB、MB、GB、および TB の各サフィックスを使用して、キロバイト、メガバイト、ギガバイト、またはテラバイトを指定できます。 既定値は MB です。 整数を指定します。小数は含めないでください。 場合*max_size*が指定されていない、ディスクがいっぱいになるまでファイル サイズが大きくなります。  
  
 UNLIMITED  
 ディスクがいっぱいになるまでファイルを拡張するように指定します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、無制限に拡張するファイル固有のログの最大サイズは 2 TB で、データ ファイルの最大サイズは 16 TB です。 FILESTREAM コンテナーに対してこのオプションを指定した場合、最大サイズはありません。 ディスクがいっぱいになるまでファイル サイズが拡張します。  
  
 FILEGROWTH *growth_increment*  
 ファイルを自動拡張するときの増加量を指定します。 ファイルの FILEGROWTH の設定を MAXSIZE の設定より大きくすることはできません。 FILEGROWTH は、FILESTREAM ファイル グループには適用されません。  
  
 *growth_increment*  
 新しい領域が必要とされるたびにファイルに追加される領域の容量です。  
  
 値は MB、KB、GB、TB または % の単位で指定できます。 サフィックス MB、KB、または % を付けないで数値を指定した場合の既定値は MB です。 % を指定すると、1 回の増加量は、増加時のファイル サイズに指定されたパーセンテージを掛けた値になります。 指定されたサイズは、最も近い 64 KB 単位の値に切り上げられます。  
  
 値 0 は、自動拡張がオフに設定を追加の領域ができないことを示します。  
  
 FILEGROWTH が指定されていない場合、既定値です。  
  
|バージョン|[既定値]|  
|-------------|--------------------|  
|先頭[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]|データ 64 MB です。 ログ ファイルの 64 MB です。|  
|先頭[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|データ 1 MB です。 ログ ファイルを 10% です。|  
|前のバージョン[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]|データ 10% です。 ログ ファイルを 10% です。|  
  
 OFFLINE  
 ファイルをオフラインに設定し、ファイル グループ内のすべてのオブジェクトをアクセス不可にします。  
  
> [!CAUTION]  
>  このオプションは、ファイルは破損しているが、復元可能な場合にのみ使用してください。 OFFLINE に設定したファイルは、そのファイルをバックアップから復元することによってのみ、オンラインに設定されます。 単一ファイルの復元の詳細については、「[RESTORE &#40;Transact-SQL&#41;](../../t-sql/statements/restore-statements-transact-sql.md)」を参照してください。  
  
> [!NOTE]  
>  \<filespec > オプションは、包含データベースで使用できません。  
  
 **\<add_or_modify_filegroups >:: =**  
  
 データベースに対してファイル グループの追加、変更、または削除を行います。  
  
 ファイル グループの*filegroup_name*  
 データベースにファイル グループを追加します。  
  
 CONTAINS FILESTREAM  
 ファイル グループで FILESTREAM バイナリ ラージ オブジェクト (BLOB) をファイル システムに格納することを指定します。  
  
 CONTAINS MEMORY_OPTIMIZED_DATA  

**適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ファイル グループが、ファイル システムでメモリ最適化データを格納することを指定します。 詳細については、「[インメモリ OLTP &#40;インメモリ最適化&#41;](../../relational-databases/in-memory-oltp/in-memory-oltp-in-memory-optimization.md)」を参照してください。 MEMORY_OPTIMIZED_DATA ファイル グループは、1 つのデータベースにつき 1 つしか許可されません。 メモリ最適化テーブルを作成する場合は、ファイル グループを空にすることはできません。 ファイルが少なくとも 1 つ必要です。 *filegroup_name*パスを参照します。 最後のフォルダーまでのパスが存在する必要がありますが、最後のフォルダーは存在できません。  
  
 次の例では、xtp_db というデータベースに追加するファイル グループを作成し、そのファイル グループにファイルを追加します。 このファイル グループには、メモリ最適化データを格納します。  
  
```  
ALTER DATABASE xtp_db ADD FILEGROUP xtp_fg CONTAINS MEMORY_OPTIMIZED_DATA;  
GO  
ALTER DATABASE xtp_db ADD FILE (NAME='xtp_mod', FILENAME='d:\data\xtp_mod') TO FILEGROUP xtp_fg;  
```  
  
 ファイル グループの削除*filegroup_name*  
 データベースからファイル グループを削除します。 ファイル グループが空でない場合は削除できません。 最初に、ファイル グループからすべてのファイルを削除してください。 詳細については、次を参照してください。"REMOVE FILE。 *logical_file_name*、"このトピックで前述しました。  
  
> [!NOTE]  
>  FILESTREAM ガベージ コレクターは、FILESTREAM コンテナーからのすべてのファイルを削除するが、場合を除き、FILESTREAM コンテナーを削除する ALTER DATABASE REMOVE FILE 操作が失敗し、エラーが返されます。 このトピックの「解説」の「FILESTREAM コンテナーの削除」を参照してください。  
  
変更のファイル グループ*filegroup_name* { \<filegroup_updatability_option > |既定の |名前 **=**  *new_filegroup_name* } を READ_ONLY または READ_WRITE、ファイル グループ、データベースの既定のファイル グループの作成状態を設定して、ファイル グループを変更またはファイル グループの名前を変更します。  
  
 \<filegroup_updatability_option >  
 ファイル グループに読み取り専用、または読み取り/書き込みのプロパティを設定します。  
  
 DEFAULT  
 既定のデータベース ファイル グループを変更*filegroup_name*です。 データベース内の 1 つのファイル グループだけを、既定のファイル グループにすることができます。 詳細については、「 [Database Files and Filegroups](../../relational-databases/databases/database-files-and-filegroups.md)」を参照してください。  
  
 名前 = *new_filegroup_name*  
 ファイル グループの名前変更、 *new_filegroup_name*です。  
  
 AUTOGROW_SINGLE_FILE  
**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 グループ内のファイルが自動拡張のしきい値を満たす場合は、そのファイルのみが大きくなります。 これは既定値です。  
  
 AUTOGROW_ALL_FILES  

**適用されます**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]を通じて[現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658))
  
 グループ内のファイルが自動拡張のしきい値を満たさない場合に、ファイル グループ内のすべてのファイルが拡大されます。  
  
 **\<filegroup_updatability_option >:: =**  
  
 ファイル グループに読み取り専用、または読み取り/書き込みのプロパティを設定します。  
  
 READ_ONLY | READONLY  
 ファイル グループが読み取り専用であることを指定します。 この中のオブジェクトを更新することはできません。 プライマリ ファイル グループを読み取り専用にすることはできません。 この状態を変更するには、データベースに対する排他的アクセスが必要になります。 詳細については、SINGLE_USER 句をご覧ください。  
  
 読み取り専用データベースのデータを変更することはできないため、次のようになります。  
  
-   システム起動時に自動復旧がスキップされます。  
  
-   データベースの圧縮が不可能になります。  
  
-   読み取り専用データベースでは、ロックは発生しません。 これにより、クエリのパフォーマンスが向上することがあります。  
  
> [!NOTE]  
>  キーワード READONLY はの将来のバージョンで削除される[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では READONLY の使用は避け、現在 READONLY を使用しているアプリケーションは修正するようにしてください。 代わりに、READ_ONLY を使用してください。  
  
 READ_WRITE | READWRITE   
 ファイル グループを READ_WRITE に指定します。 ファイル グループ内のオブジェクトを更新できます。 この状態を変更するには、データベースに対する排他的アクセスが必要になります。 詳細については、SINGLE_USER 句をご覧ください。  
  
> [!NOTE]  
>  キーワード READWRITE はの将来のバージョンで削除される[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では READWRITE の使用は避け、現在 READWRITE を使用しているアプリケーションは修正するようにしてください。 代わりに、READ_WRITE を使用してください。  
  
 これらのオプションの状態を調べることで決定できます、 **is_read_only**内の列、 **sys.databases**カタログ ビューまたは**Updateability**のプロパティ、DATABASEPROPERTYEX 関数。  
  
## <a name="remarks"></a>解説  
 データベースのサイズを小さくを使用して[DBCC SHRINKDATABASE](../../t-sql/database-console-commands/dbcc-shrinkdatabase-transact-sql.md)です。  
  
 BACKUP ステートメントの実行中にファイルを追加したり削除したりすることはできません。  
  
 各データベースに、最大 32,767 のファイルと 32,767 のファイル グループを指定できます。  
  
 [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]または後で、(たとえば、オンラインまたはオフライン)、データベース ファイルの状態が管理されていない別に、データベースの状態からです。 詳細については、次を参照してください。[ファイルの状態](../../relational-databases/databases/file-states.md)です。 ファイル グループ内のファイルの状態は、ファイル グループ全体の可用性を決定します。 ファイル グループを使用可能にするには、ファイル グループ内のすべてのファイルがオンラインである必要があります。 ファイル グループがオフラインの場合、SQL ステートメントでそのファイル グループにアクセスを試行するとエラーが発生します。 SELECT ステートメントのクエリ プランを作成する場合、クエリ オプティマイザーは、オフラインのファイル グループにある非クラスター化インデックスやインデックス付きビューを回避します。 これにより、これらのステートメントは正常に実行できます。 ただし、オフラインのファイル グループに、対象テーブルのヒープやクラスター化インデックスが含まれている場合には、SELECT ステートメントは失敗します。 また、オフラインのファイル グループ内にあるインデックス付きのテーブルを変更する INSERT、UPDATE、または DELETE ステートメントは失敗します。  
  
## <a name="moving-files"></a>ファイルの移動  
 FILENAME に新しい場所を指定することにより、システムまたはユーザー定義のデータ、およびログ ファイルを移動することができます。 これは、次のようなシナリオで役立ちます。  
  
-   障害復旧。 たとえば、ハードウェア障害により、データベースが問題のあるモードになっている場合や、シャットダウンされた場合など。  
  
-   計画に従った再配置  
  
-   スケジュールされたディスク メンテナンスでの再配置。  
  
 詳細については、次を参照してください。[データベース ファイルの移動](../../relational-databases/databases/move-database-files.md)です。  
  
## <a name="initializing-files"></a>ファイルの初期化  
 既定では、データ ファイルおよびログ ファイルは、次のいずれかの操作を実行したときに、ファイルを 0 で埋め込むことにより初期化されます。  
  
-   データベースを作成します。  
  
-   既存のデータベースへのファイルの追加  
  
-   既存のファイルのサイズを大きくする  
  
-   データベースまたはファイル グループの復元  
  
 データ ファイルを瞬時に初期化できます。 そのため、このようなファイル操作を高速に実行できます。  
  
## <a name="removing-a-filestream-container"></a>FILESTREAM コンテナーの削除  
 DBCC SHRINKFILE 操作によって FILESTREAM コンテナーが空にされた場合でも、データベースは、さまざまなシステム保守上の理由から、削除されたファイルへの参照を維持する必要があります。 [sp_filestream_force_garbage_collection & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)これを行うには安全ではときに、これらのファイルを削除する FILESTREAM ガベージ コレクターを実行します。 FILESTREAM ガベージ コレクターによって FILESTREAM コンテナーからすべてのファイルが削除されない限り、ALTER DATABASE REMOVE FILE 操作で FILESTREAM コンテナーを削除する試みは失敗し、エラーが返されます。 FILESTREAM コンテナーを削除する場合は、次の手順をお勧めします。  
  
1.  実行[DBCC SHRINKFILE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)このコンテナーのアクティブなコンテンツを他のコンテナーに移動する EMPTYFILE オプションを使用します。  
  
2.  ログ バックアップが完全または一括ログ復旧モデルで作成されたことを確認します。  
  
3.  レプリケーション ログ リーダー ジョブが実行されていることを確認します (該当する場合)。  
  
4.  実行[sp_filestream_force_garbage_collection (& a) #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)を強制的にガベージ コレクターがこのコンテナーで不要なファイルを削除します。  
  
5.  REMOVE FILE オプションを指定して ALTER DATABASE を実行し、このコンテナーを削除します。  
  
6.  もう一度手順 2. ～ 4. を繰り返して、ガベージ コレクションを完了します。  
  
7.  ALTER Database...REMOVE FILE を使用して、このコンテナーを削除します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-adding-a-file-to-a-database"></a>A. データベースにファイルを追加する  
 次の例では、5 MB のデータ ファイルを[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = Test1dat2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat2.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="b-adding-a-filegroup-with-two-files-to-a-database"></a>B. 2 つのファイルから成るファイル グループをデータベースに追加する  
 次の例では、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースに `Test1FG1` ファイル グループを作成し、そのファイル グループに 5 MB のファイルを 2 つ追加します。  
  
```  
USE master  
GO  
ALTER DATABASE AdventureWorks2012  
ADD FILEGROUP Test1FG1;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD FILE   
(  
    NAME = test1dat3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat3.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1dat4,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\t1dat4.ndf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
)  
TO FILEGROUP Test1FG1;  
GO  
  
```  
  
### <a name="c-adding-two-log-files-to-a-database"></a>C. 2 つのログ ファイルをデータベースに追加する  
 次の例では、2 つの 5 MB のログ ファイル、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
ADD LOG FILE   
(  
    NAME = test1log2,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\DATA\test2log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
),  
(  
    NAME = test1log3,  
    FILENAME = 'C:\Program Files\Microsoft SQL Server\MSSQL10_50.MSSQLSERVER\MSSQL\DATA\test3log.ldf',  
    SIZE = 5MB,  
    MAXSIZE = 100MB,  
    FILEGROWTH = 5MB  
);  
GO  
  
```  
  
### <a name="d-removing-a-file-from-a-database"></a>D. データベースからファイルを削除する  
 次の例では、例 B で追加したファイルの一方を削除します。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
REMOVE FILE test1dat4;  
GO  
  
```  
  
### <a name="e-modifying-a-file"></a>E. ファイルを変更する  
次の例では、例 B で追加したファイルのうち、1 つのサイズを拡張します。  
 ALTER DATABASE MODIFY FILE コマンドを使用できますのみ大きくファイルのサイズ、ファイルのサイズを小さくする必要がある場合は、DBCC SHRINKFILE を使用する必要があります。 します。  
  
```  
USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO  
```

この例では、100 mb、データ ファイルのサイズを縮小し、その量のサイズを指定します。 

```
USE AdventureWorks2012;
GO

DBCC SHRINKFILE (AdventureWorks2012_data, 100);
GO

USE master;  
GO
  
ALTER DATABASE AdventureWorks2012   
MODIFY FILE  
(NAME = test1dat3,  
SIZE = 200MB);  
GO
```
 
  
### <a name="f-moving-a-file-to-a-new-location"></a>F. ファイルを新しい場所に移動する  
 次の例では、例 A で作成した `Test1dat2` ファイルを、新しいディレクトリに移動します。  
  
> [!NOTE]  
>  この例を実行する前に、ファイルを新しいディレクトリに物理的に移動しておく必要があります。 その後、停止してのインスタンスを起動[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]するか、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]データベースの変更を実装するには、オフラインおよびから ONLINE です。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012  
MODIFY FILE  
(  
    NAME = Test1dat2,  
    FILENAME = N'c:\t1dat2.ndf'  
);  
GO  
```  
  
### <a name="g-moving-tempdb-to-a-new-location"></a>G. tempdb を新しい場所に移動する  
 次の例では移動`tempdb`別の場所へのディスク上の現在の場所からします。 `tempdb`が再作成された、MSSQLSERVER サービスを起動するたびにログ ファイルと物理的にデータを移動する必要はありません。 これらのファイルは、MSSQLSERVER サービスが手順 3. で再開したときに作成されます。 サービスが再起動されるまで`tempdb`既存の場所に機能し続けます。  
  
1.  論理ファイル名を判断、`tempdb`データベースとディスク上の現在の場所。  
  
    ```  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    GO  
    ```  
  
2.  `ALTER DATABASE`を使用して、各ファイルの場所を変更します。  
  
    ```  
    USE master;  
    GO  
    ALTER DATABASE tempdb   
    MODIFY FILE (NAME = tempdev, FILENAME = 'E:\SQLData\tempdb.mdf');  
    GO  
    ALTER DATABASE  tempdb   
    MODIFY FILE (NAME = templog, FILENAME = 'E:\SQLData\templog.ldf');  
    GO  
    ```  
  
3.  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のインスタンスをいったん停止してから再起動します。  
  
4.  ファイルの変更を確認します。  
  
    ```  
    SELECT name, physical_name  
    FROM sys.master_files  
    WHERE database_id = DB_ID('tempdb');  
    ```  
  
5.  tempdb.mdf ファイルと templog.ldf ファイルを元の場所から削除します。  
  
### <a name="h-making-a-filegroup-the-default"></a>H. ファイル グループを既定にする  
 次の例では、`Test1FG1`既定のファイル グループは、例 B のファイル グループを作成します。 既定のファイル グループをリセットし、`PRIMARY`ファイル グループ。 なお`PRIMARY`角かっこまたは引用符で区切る必要があります。  
  
```  
USE master;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP Test1FG1 DEFAULT;  
GO  
ALTER DATABASE AdventureWorks2012   
MODIFY FILEGROUP [PRIMARY] DEFAULT;  
GO  
  
```  
  
### <a name="i-adding-a-filegroup-using-alter-database"></a>I. ALTER DATABASE を使用してファイル グループを追加する  
 次の例では、`FILEGROUP` 句が含まれる `FILESTREAM` を、`FileStreamPhotoDB` データベースに追加します。  
  
```  
--Create and add a FILEGROUP that CONTAINS the FILESTREAM clause to  
--the FileStreamPhotoDB database.  
ALTER DATABASE FileStreamPhotoDB  
ADD FILEGROUP TodaysPhotoShoot  
CONTAINS FILESTREAM;  
GO  
  
--Add a file for storing database photos to FILEGROUP   
ALTER DATABASE FileStreamPhotoDB  
ADD FILE  
(  
    NAME= 'PhotoShoot1',  
    FILENAME = 'C:\Users\Administrator\Pictures\TodaysPhotoShoot.ndf'  
)  
TO FILEGROUP TodaysPhotoShoot;  
GO  
```      
        
### <a name="j-change-filegroup-so-that-when-a-file-in-the-filegroup-meets-the-autogrow-threshold-all-files-in-the-filegroup-grow"></a>J. グループ内のファイルが自動拡張のしきい値を満たさない場合に、ファイル グループ内のすべてのファイルが拡張できるように、ファイル グループを変更します。
 次の例は、必要な生成`ALTER DATABASE`と読み取り/書き込みファイル グループを変更するステートメント、`AUTOGROW_ALL_FILES`設定します。  
  
```  
--Generate ALTER DATABASE ... MODIFY FILEGROUP statements  
--so that all read-write filegroups grow at the same time.  
SET NOCOUNT ON;

DROP TABLE IF EXISTS #tmpdbs
CREATE TABLE #tmpdbs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, isdone bit);

DROP TABLE IF EXISTS #tmpfgs
CREATE TABLE #tmpfgs (id int IDENTITY(1,1), [dbid] int, [dbname] sysname, fgname sysname, isdone bit);

INSERT INTO #tmpdbs ([dbid], [dbname], [isdone])
SELECT database_id, name, 0 FROM master.sys.databases (NOLOCK) WHERE is_read_only = 0 AND state = 0;

DECLARE @dbid int, @query VARCHAR(1000), @dbname sysname, @fgname sysname

WHILE (SELECT COUNT(id) FROM #tmpdbs WHERE isdone = 0) > 0
BEGIN
    SELECT TOP 1 @dbname = [dbname], @dbid = [dbid] FROM #tmpdbs WHERE isdone = 0

    SET @query = 'SELECT ' + CAST(@dbid AS NVARCHAR) + ', ''' + @dbname + ''', [name], 0 FROM [' + @dbname + '].sys.filegroups WHERE [type] = ''FG'' AND is_read_only = 0;'
    INSERT INTO #tmpfgs
    EXEC (@query)

    UPDATE #tmpdbs
    SET isdone = 1
    WHERE [dbid] = @dbid
END;

IF (SELECT COUNT(ID) FROM #tmpfgs) > 0
BEGIN
    WHILE (SELECT COUNT(id) FROM #tmpfgs WHERE isdone = 0) > 0
    BEGIN
        SELECT TOP 1 @dbname = [dbname], @dbid = [dbid], @fgname = fgname FROM #tmpfgs WHERE isdone = 0

        SET @query = 'ALTER DATABASE [' + @dbname + '] MODIFY FILEGROUP [' + @fgname + '] AUTOGROW_ALL_FILES;'

        PRINT @query

        UPDATE #tmpfgs
        SET isdone = 1
        WHERE [dbid] = @dbid AND fgname = @fgname
    END
END; 
GO  
```      
  
## <a name="see-also"></a>参照  
 [CREATE DATABASE &#40;SQL Server Transact-SQL&#41;](../../t-sql/statements/create-database-sql-server-transact-sql.md)   
 [DATABASEPROPERTYEX &#40;Transact-SQL&#41;](../../t-sql/functions/databasepropertyex-transact-sql.md)   
 [DROP DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/drop-database-transact-sql.md)   
 [sp_spaceused &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-spaceused-transact-sql.md)   
 [sys.databases &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.data_spaces と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-data-spaces-transact-sql.md)   
 [sys.filegroups & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [sys.master_files と #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [バイナリ ラージ オブジェクト &#40;Blob&#41; データ &#40;SQL Server&#41;](../../relational-databases/blob/binary-large-object-blob-data-sql-server.md)   
 [DBCC SHRINKFILE &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-shrinkfile-transact-sql.md)   
 [sp_filestream_force_garbage_collection &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/filestream-and-filetable-sp-filestream-force-garbage-collection.md)  
  
  


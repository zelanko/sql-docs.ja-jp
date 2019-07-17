---
title: sp_adddistributiondb (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 04/30/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: language-reference
f1_keywords:
- sp_adddistributiondb_TSQL
- sp_adddistributiondb
helpviewer_keywords:
- sp_adddistributiondb
ms.assetid: e9bad56c-d2b3-44ba-a4d7-ff2fd842e32d
author: mashamsft
ms.author: mathoma
ms.openlocfilehash: d48a41218a35e072e374e3cf99bf362397fbad23
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68072792"
---
# <a name="spadddistributiondb-transact-sql"></a>sp_adddistributiondb (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  新しいディストリビューション データベースを作成し、ディストリビューター スキーマをインストールします。 ディストリビューション データベースでは、プロシージャ、スキーマ、およびレプリケーションで使用されるメタデータを格納します。 このストアド プロシージャは、ディストリビューション データベースを作成し、必要なテーブルおよびストアド プロシージャがレプリケーション ディストリビューションを有効にする必要をインストールするには、master データベースに対して、ディストリビューターで実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_adddistributiondb [ @database= ] 'database'   
    [ , [ @data_folder= ] 'data_folder' ]   
    [ , [ @data_file= ] 'data_file' ]   
    [ , [ @data_file_size= ] data_file_size ]   
    [ , [ @log_folder= ] 'log_folder' ]   
    [ , [ @log_file= ] 'log_file' ]   
    [ , [ @log_file_size= ] log_file_size ]   
    [ , [ @min_distretention= ] min_distretention ]   
    [ , [ @max_distretention= ] max_distretention ]   
    [ , [ @history_retention= ] history_retention ]   
    [ , [ @security_mode= ] security_mode ]   
    [ , [ @login= ] 'login' ]   
    [ , [ @password= ] 'password' ]   
    [ , [ @createmode= ] createmode ]  
    [ , [ @from_scripting = ] from_scripting ] 
    [ , [ @deletebatchsize_xact = ] deletebatchsize_xact ] 
    [ , [ @deletebatchsize_cmd = ] deletebatchsize_cmd ] 
```  
  
## <a name="arguments"></a>引数  
`[ @database = ] database'` 作成するディストリビューション データベースの名前です。 *データベース*は**sysname**、既定値はありません。 指定されたデータベースは既に存在し、ディストリビューション データベースとしてマークされていない、し配布を有効にするために必要なオブジェクトがインストールされているし、データベースがディストリビューション データベースとしてマークされています。 指定したデータベースが、既にディストリビューション データベースとして有効な場合は、エラーが返されます。  
  
`[ @data_folder = ] 'data_folder'_` ディストリビューション データベース データ ファイルの格納に使用するディレクトリの名前です。 *data_folder*は**nvarchar (255)** 、既定値は NULL です。 NULL の場合、その [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスのデータ ディレクトリ、たとえば `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data` が使用されます。  
  
`[ @data_file = ] 'data_file'` データベース ファイルの名前です。 *data_file*は**nvarchar (255)** 、既定値は**データベース**します。 NULL の場合、ストアド プロシージャは、データベース名を使用してファイル名を構築します。  
  
`[ @data_file_size = ] data_file_size` メガバイト (MB) 単位で初期データ ファイルのサイズです。 *data_file_size は*s **int**、既定値は 5 MB です。  
  
`[ @log_folder = ] 'log_folder'` データベースのログ ファイルのディレクトリの名前です。 *log_folder*は**nvarchar (255)** 、既定値は NULL です。 NULL の場合のインスタンスをデータ ディレクトリ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]使用されます (たとえば、 `C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data`)。  
  
`[ @log_file = ] 'log_file'` ログ ファイルの名前です。 *log_file*は**nvarchar (255)** 、既定値は NULL です。 NULL の場合、ストアド プロシージャは、データベース名を使用してファイル名を構築します。  
  
`[ @log_file_size = ] log_file_size` メガバイト (MB) 単位で最初のログ ファイルのサイズです。 *log_file_size*は**int**、ファイルで許容されるサイズ、既定値は 0 MB には、ファイル サイズが最小のログを使用して作成することを意味[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
`[ @min_distretention = ] min_distretention` トランザクションがディストリビューション データベースから削除されるまでの時間、最小保有期間です。 *min_distretention*は**int**、既定値は 0 時間です。  
  
`[ @max_distretention = ] max_distretention` トランザクションが削除されるまでの時間、最大保有期間です。 *max_distretention*は**int**、既定値は 72 時間です。 ディストリビューションの最長保持時間より古い、レプリケートされたコマンドを受け取っていないサブスクリプションには、非アクティブのマークが付きます。このようなサブスクリプションは再初期化する必要があります。 アクティブでないサブスクリプションに対しては RAISERROR 21011 が発行されます。 値**0**レプリケートされたトランザクションをことを意味はディストリビューション データベースに格納されません。  
  
`[ @history_retention = ] history_retention` 履歴を保持する時間の数です。 *history_retention*は**int**、既定値は 48 時間です。  
  
`[ @security_mode = ] security_mode` ディストリビューターに接続するときに使用するセキュリティ モードです。 *security_mode*は**int**、既定値は 1 です。 **0**指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]認証。**1** Windows 統合認証を指定します。  
  
`[ @login = ] 'login'` ログイン名されるディストリビューターに接続するときに、ディストリビューション データベースを作成します。 これは、必要な場合*security_mode*に設定されている**0**します。 *login* のデータ型は **sysname** で、既定値は NULL です。  
  
`[ @password = ] 'password'` ディストリビューターに接続するときに、パスワードが使用されます。 これは、必要な場合*security_mode*に設定されている**0**します。 *パスワード*は**sysname**、既定値は NULL です。  
  
`[ @createmode = ] createmode` *(createmode = restore)* は**int**、既定値は 1、次の値のいずれかを指定できます。  
  
|値|説明|  
|-----------|-----------------|  
|**0**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
|**1** (既定値)|データベースの作成または既存のデータベースにあり、適用**instdist.sql**ディストリビューション データベースでレプリケーション オブジェクトを作成するファイル。|  
|**2**|[!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]|  
  
`[ @from_scripting = ] from_scripting` [!INCLUDE[ssInternalOnly](../../includes/ssinternalonly-md.md)]  
 
`[ @deletebatchsize_xact = ] deletebatchsize_xact` MSRepl_Transactions テーブルから期限切れのトランザクションのクリーンアップ時に使用されるバッチ サイズを指定します。 *deletebatchsize_xact*は**int**、既定値は 5000 です。 このパラメーターは、SQL Server 2012 SP4 および SQL Server 2016 SP2 のリリース後に、SQL Server 2017 で初めて導入されました。  

`[ @deletebatchsize_cmd = ] deletebatchsize_cmd` 有効期限が切れたコマンドの MSRepl_Commands テーブルのクリーンアップ時に使用されるバッチ サイズを指定します。 *deletebatchsize_cmd*は**int**、既定値は 2000年です。 このパラメーターは、SQL Server 2012 SP4 および SQL Server 2016 SP2 のリリース後に、SQL Server 2017 で初めて導入されました。 
 
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>コメント  
 **sp_adddistributiondb**はあらゆる種類のレプリケーションで使用します。 ただし、このストアド プロシージャは、ディストリビューター側でのみ動作します。  
  
 実行してディストリビューターを構成する必要があります[sp_adddistributor](../../relational-databases/system-stored-procedures/sp-adddistributor-transact-sql.md)実行する前に**sp_adddistributiondb**します。  
  
 実行**sp_adddistributor**実行する前に**sp_adddistributiondb**します。  
  
## <a name="example"></a>例  
  
```  
-- This script uses sqlcmd scripting variables. They are in the form  
-- $(MyVariable). For information about how to use scripting variables    
-- on the command line and in SQL Server Management Studio, see the   
-- "Executing Replication Scripts" section in the topic  
-- "Programming Replication Using System Stored Procedures".  
  
-- Install the Distributor and the distribution database.  
DECLARE @distributor AS sysname;  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
DECLARE @directory AS nvarchar(500);  
DECLARE @publicationDB AS sysname;  
-- Specify the Distributor name.  
SET @distributor = $(DistPubServer);  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
-- Specify the replication working directory.  
SET @directory = N'\\' + $(DistPubServer) + '\repldata';  
-- Specify the publication database.  
SET @publicationDB = N'AdventureWorks2012';   
  
-- Install the server MYDISTPUB as a Distributor using the defaults,  
-- including autogenerating the distributor password.  
USE master  
EXEC sp_adddistributor @distributor = @distributor;  
  
-- Create a new distribution database using the defaults, including  
-- using Windows Authentication.  
USE master  
EXEC sp_adddistributiondb @database = @distributionDB,   
    @security_mode = 1;  
GO  
  
-- Create a Publisher and enable AdventureWorks2012 for replication.  
-- Add MYDISTPUB as a publisher with MYDISTPUB as a local distributor  
-- and use Windows Authentication.  
DECLARE @distributionDB AS sysname;  
DECLARE @publisher AS sysname;  
-- Specify the distribution database.  
SET @distributionDB = N'distribution';  
-- Specify the Publisher name.  
SET @publisher = $(DistPubServer);  
  
USE [distribution]  
EXEC sp_adddistpublisher @publisher=@publisher,   
    @distribution_db=@distributionDB,   
    @security_mode = 1;  
GO  
  
```  
  
## <a name="permissions"></a>アクセス許可  
 メンバーのみ、 **sysadmin**固定サーバー ロールが実行できる**sp_adddistributiondb**します。  
  
## <a name="see-also"></a>関連項目  
 [パブリッシングとディストリビューションの構成](../../relational-databases/replication/configure-publishing-and-distribution.md)   
 [sp_changedistributiondb &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changedistributiondb-transact-sql.md)   
 [sp_dropdistributiondb &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-dropdistributiondb-transact-sql.md)   
 [sp_helpdistributiondb &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpdistributiondb-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [[ディストリビューションの構成]](../../relational-databases/replication/configure-distribution.md)  
  
  

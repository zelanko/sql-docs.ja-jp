---
title: sp_add_data_file_recover_suspect_db (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/16/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_add_data_file_recover_suspect_db
- sp_add_data_file_recover_suspect_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_add_data_file_recover_suspect_db
ms.assetid: b25262aa-a228-48b7-8739-6581c760b171
caps.latest.revision: 51
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 13c08441680744d38f870fc5b6ebd5d7a1e20c91
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="spadddatafilerecoversuspectdb-transact-sql"></a>sp_add_data_file_recover_suspect_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ファイル グループの領域が不足していたため (エラー 1105)、データベースの復旧を完了できなかったときに、データ ファイルをファイル グループに追加します。 ファイルが追加された後、このストアド プロシージャは未復旧の設定をオフにして、データベースの復旧を完了します。 パラメーターは、ALTER DATABASE の場合と同じ*database_name*ファイルを追加します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_add_data_file_recover_suspect_db [ @dbName= ] 'database'   
    , [ @filegroup = ] 'filegroup_name'   
    , [ @name = ] 'logical_file_name'   
    , [ @filename= ] 'os_file_name'   
    , [ @size = ] 'size'   
    , [ @maxsize = ] 'max_size'   
    , [ @filegrowth = ] 'growth_increment'  
```  
  
## <a name="arguments"></a>引数  
 [ **@dbName=** ] **'***database* **'**  
 データベースの名前です。 *データベース*は**sysname**、既定値はありません。  
  
 [ **@filegroup=** ] **'***filegroup_name* **'**  
 ファイルを追加するファイル グループを指定します。 *filegroup_name*は**nvarchar (260)** を既定値は NULL には、プライマリ ファイルを示します。  
  
 [ **@name=** ] **'***logical_file_name* **'**  
 ファイルを参照するために [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]で使用される名前を指定します。 サーバー内で一意な名前を指定する必要があります。 *logical_file_name*は**nvarchar (260)**、既定値はありません。  
  
 [ **@filename=** ] **'***os_file_name* **'**  
 オペレーティング システムが使用するファイルのパスとファイル名を指定します。 ファイルは[!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンス上に存在している必要があります。 *os_file_name*は**nvarchar (260)**、既定値はありません。  
  
 [ **@size=** ] **'***size* **'**  
 ファイルの初期サイズです。 *サイズ*は**nvarchar (20)**、既定値は NULL です。 整数を指定します。小数を含めないでください。 サフィックス MB、KB を使用してメガバイト、キロバイトを指定できます。 既定値は MB です。 最小値は 512 KB です。 場合*サイズ*が指定されていない、既定値は 1 MB です。  
  
 [ **@maxsize=** ] **'***max_size* **'**  
 ファイルを拡張できる最大サイズを指定します。 *max_size*は**nvarchar (20)**、既定値は NULL です。 整数を指定します。小数を含めないでください。 サフィックス MB、KB を使用してメガバイト、キロバイトを指定できます。 既定値は MB です。  
  
 場合*max_size*が指定されていない、ディスクがいっぱいになるまで、ファイルが拡張されます。 ディスク容量の上限まで近づくと、[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows アプリケーション ログが管理者に対して警告を発します。  
  
 [  **@filegrowth=** ] **' * * * growth_increment* **'**  
 新しい領域が必要とされるたびにファイルに追加される領域の容量を指定します。 *growth_increment*は**nvarchar (20)**、既定値は NULL です。 値に 0 を指定した場合、ファイルの拡張は行われません。 整数を指定します。小数を含めないでください。 値は MB、KB、またはパーセント (%) の単位で指定できます。 % を指定すると、増加量が、増分値の発生時に、ファイルのサイズの比率を指定します。 サフィックス MB、KB、または % を付けないで数値を指定した場合の既定値は MB です。  
  
 場合*growth_increment* null、既定値は 10%、および最小値は 64 KB です。 指定されたサイズは、最も近い 64 KB 単位の値に切り上げられます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 なし  
  
## <a name="permissions"></a>権限  
 メンバーに権限は、既定の実行、 **sysadmin**固定サーバー ロール。 この権限は譲渡できません。  
  
## <a name="examples"></a>使用例  
 次の例では、データベース`db1`ファイル グループに十分な領域 (エラー 1105)、復旧中に問題ありとして`fg1`です。  
  
```  
USE master;  
GO  
EXEC sp_add_data_file_recover_suspect_db db1, fg1, file2,  
    'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Data\db1_file2.mdf', '1MB';  
```  
  
## <a name="see-also"></a>参照  
 [ALTER DATABASE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-database-transact-sql.md)   
 [sp_add_log_file_recover_suspect_db &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-add-log-file-recover-suspect-db-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

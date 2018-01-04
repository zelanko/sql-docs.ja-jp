---
title: "sp_kill_filestream_non_transacted_handles (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_kill_filestream_non_transacted_handles_TSQL
- sp_kill_filestream_non_transacted_handles
dev_langs: TSQL
helpviewer_keywords: sp_kill_filestream_non_transacted_handles
ms.assetid: 7188353e-ab29-49a0-8f25-7fb8ab122589
caps.latest.revision: "13"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 2d06550f0a9cd322e26acfa8f29890833c15f947
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="filestream-and-filetable---spkillfilestreamnontransactedhandles"></a>Filestream および FileTable - sp_kill_filestream_non_transacted_handles
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  FileTable データに対する非トランザクション ファイル ハンドルを閉じます。  
  
## <a name="syntax"></a>構文  
  
```sql  
sp_kill_filestream_non_transacted_handles [[ @table_name = ] ‘table_name’, [[ @handle_id = ] @handle_id]]  
```  
  
## <a name="arguments"></a>引数  
 *table_name*  
 非トランザクション ハンドルを閉じるテーブルの名前。  
  
 渡すことができます*table_name*せず*handle_id* FileTable に対する非トランザクション ハンドルを開くすべてを閉じます。  
  
 値に NULL を渡すことが*table_name*現在のデータベース内のすべての Filetable の非トランザクション ハンドルを開くすべてを閉じます。 NULL は既定値です。  
  
 *handle_id*  
 閉じる個々のハンドルのオプションの ID です。 取得することができます、 *handle_id*から、 [sys.dm_filestream_non_transacted_handles &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md)動的管理ビュー。 各 ID は [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンス内で一意です。 指定した場合*handle_id*の値を指定する必要も*table_name*です。  
  
 値に NULL を渡すことが*handle_id*を閉じますすべての開いている非トランザクション ハンドルで指定された FileTable *table_name*です。 NULL は既定値です。  
  
## <a name="return-code-value"></a>リターン コード値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
 [なし] :  
  
## <a name="general-remarks"></a>全般的な解説  
 *Handle_id*で必要な**sp_kill_filestream_non_transacted_handles** session_id またはその他で使用されている作業の単位に関連しない**kill**コマンド。  
  
 詳細については、「 [FileTable の管理](../../relational-databases/blob/manage-filetables.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 開いている非トランザクション ファイル ハンドルのについては、動的管理ビューに対してクエリ[sys.dm_filestream_non_transacted_handles &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-dynamic-management-views/sys-dm-filestream-non-transacted-handles-transact-sql.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 必要があります**VIEW DATABASE STATE**からファイル ハンドルを取得するアクセス許可、 **sys.dm_FILESTREAM_non_transacted_handles**動的管理ビューを実行し、 **sp_kill_filestream_non_transacted_handles**です。  
  
## <a name="examples"></a>使用例  
 次の例を呼び出す方法を示して**sp_kill_filestream_non_transacted_handles**を FileTable データに対する非トランザクション ファイル ハンドルを閉じます。  
  
```sql  
-- Close all open handles in the current database.  
sp_kill_filestream_non_transacted_handles  
  
-- Close all open handles in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = ’myFileTable’  
  
-- Close a specific handle in myFileTable.  
sp_kill_filestream_non_transacted_handles @table_name = ’myFileTable’, @handle_id = 0xFFFAAADD  
```  
  
 次の例は、スクリプトを使用して取得する方法を示しています、 *handle_id*して閉じます。  
  
```sql  
DECLARE @handle_id varbinary(16);  
DECLARE @table_name sysname;  
  
SELECT TOP 1 @handle_id = handle_id, @table_name = Object_name(table_id)  
FROM sys.dm_FILESTREAM_non_transacted_handles;  
  
EXEC sp_kill_filestream_non_transacted_handles @dbname, @table_name, @handle_id;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [FileTable の管理](../../relational-databases/blob/manage-filetables.md)  
  
  

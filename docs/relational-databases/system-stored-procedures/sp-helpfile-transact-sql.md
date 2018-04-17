---
title: sp_helpfile を実行 (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpfile
- sp_helpfile_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfile
ms.assetid: 1546e0ae-5a99-4e01-9eb9-d147fa65884c
caps.latest.revision: 23
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 6c0d246c2ed8ea670f2d8c2fc05bca828ce152ca
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpfile-transact-sql"></a>sp_helpfile (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに関連付けられたファイルの物理名と属性を返します。 このストアド プロシージャを使用して、サーバーに接続するか、またはサーバーから切断するファイルの名前を決定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpfile [ [ @filename= ] 'name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@filename =** ] **'***name***'**  
 データベース内のファイルの論理名を指定します。 *名前*は**sysname**、既定値は NULL です。 場合*名前*が指定されていない、現在のデータベース内のすべてのファイルの属性が返されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**name**|**sysname**|論理ファイル名です。|  
|**fileid**|**smallint**|ファイルの数値識別子。 場合は返されません*名前*が指定されている*です。*|  
|**filename**|**nchar(260)**|物理ファイル名|  
|**filegroup**|**sysname**|ファイルが属するファイル グループです。<br /><br /> NULL = ファイルは、ログ ファイルです。 ログ ファイルはファイル グループのメンバーにはなりません。|  
|**size**|**nvarchar(15)**|ファイル サイズ (KB 単位) です。|  
|**maxsize**|**nvarchar(15)**|ファイルの最大拡張サイズです。 このフィールドの値が UNLIMITED である場合、ディスクがいっぱいになるまでファイルを拡張できることを示します。|  
|**growth**|**nvarchar(15)**|ファイルを拡張するときの増分です。 これは、新しい領域が必要になるたびにファイルに追加される容量を示します。<br /><br /> 0 = ファイルのサイズは固定されており、容量を追加することはできません。|  
|**使用状況**|**varchar (9)**|データ ファイルの場合、値は**'data only'**と、値は、ログ ファイルの**'ログのみ'**です。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、内のファイルに関する情報を返します[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]です。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfile;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfilegroup &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfilegroup-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース ファイルとファイル グループ](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  

---
title: sp_helpfilegroup (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpfilegroup_TSQL
- sp_helpfilegroup
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpfilegroup
ms.assetid: 619716b5-95dc-4538-82ae-4b90b9da8ebc
caps.latest.revision: 35
author: edmacauley
ms.author: edmaca
manager: craigg
ms.openlocfilehash: 61e297999776254e85372c4b6ce25927396fdff6
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33260788"
---
# <a name="sphelpfilegroup-transact-sql"></a>sp_helpfilegroup (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースに関連付けられたファイル グループの名前と属性を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpfilegroup [ [ @filegroupname = ] 'name' ]  
```  
  
## <a name="arguments"></a>引数  
 [ **@filegroupname =** ] **'***name***'**  
 データベース内のファイル グループの論理名を指定します。 *名前*は**sysname**、既定値は NULL です。 場合*名前*が指定されていない、現在のデータベース内のすべてのファイル グループが一覧表示され、設定、結果セット セクションに表示される最初の結果のみが表示されます。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**groupname**|**sysname**|ファイル グループの名前。|  
|**groupid**|**smallint**|数値ファイル グループ識別子です。|  
|**filecount**|**int**|ファイル グループ内のファイル数です。|  
  
 場合*名前*は指定すると、ファイル グループ内の各ファイルの 1 つの行が返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**file_in_group**|**sysname**|ファイル グループ内のファイルの論理名です。|  
|**fileid**|**smallint**|数値ファイル識別子です。|  
|**filename**|**nchar(260)**|ディレクトリ パスを含むファイルの物理名です。|  
|**size**|**nvarchar(15)**|ファイル サイズ (KB 単位) です。|  
|**maxsize**|**nvarchar(15)**|ファイルの最大サイズ。<br /><br /> この値は、ファイルのサイズの上限です。 このフィールドの値が UNLIMITED である場合、ディスクがいっぱいになるまでファイルを拡張できることを示します。|  
|**growth**|**nvarchar(15)**|ファイルを拡張するときの増分です。 これは、新しい領域が必要するたびに、ファイルに追加される領域の量を示します。<br /><br /> 0 = ファイルのサイズは固定されており、容量を追加することはできません。|  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-returning-all-filegroups-in-a-database"></a>A. データベース内のすべてのファイル グループを返す  
 次の例は、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースのファイル グループに関する情報を返します。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup;  
GO  
```  
  
### <a name="b-returning-all-files-in-a-filegroup"></a>B. ファイル グループ内のすべてのファイルを返す  
 次の例は、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] サンプル データベースの `PRIMARY` ファイル グループにあるすべてのファイルの情報を返します。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_helpfilegroup 'PRIMARY';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sp_helpfile &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helpfile-transact-sql.md)   
 [sys.database_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-database-files-transact-sql.md)   
 [sys.master_files &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-master-files-transact-sql.md)   
 [sys.filegroups &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-filegroups-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース ファイルとファイル グループ](../../relational-databases/databases/database-files-and-filegroups.md)  
  
  

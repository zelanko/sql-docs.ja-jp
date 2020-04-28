---
title: sp_helpindex (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_helpindex_TSQL
- sp_helpindex
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpindex
ms.assetid: c7f73ba0-ec35-4b10-aa5f-f1487e51fbf7
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 17e43f9739b0306a42c4c454cf93fdf92b255177
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68122527"
---
# <a name="sp_helpindex-transact-sql"></a>sp_helpindex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  テーブルまたはビューのインデックスに関する情報をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpindex [ @objname = ] 'name'  
```  
  
## <a name="arguments"></a>引数  
`[ @objname = ] 'name'`ユーザー定義テーブルまたはビューの修飾名または修飾され名を指定します。 引用符は、テーブルまたはビューの修飾名を指定したときにのみ必要です。 データベース名を含む完全修飾名を指定する場合は、データベース名を現在のデータベースの名前にする必要があります。 *名前*は**nvarchar (776)**,、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**index_name**|**sysname**|インデックス名。|  
|**index_description**|**varchar (210)**|インデックスが配置されているファイルグループを含むインデックスの説明。|  
|**index_keys**|**nvarchar (2078)**|インデックスの作成で使用するテーブルまたはビュー内の列。|  
  
 降順のインデックス付き列は、名前の後にマイナス記号 (-) を付けて結果セットに一覧表示されます。既定の昇順のインデックス列は、名前だけで一覧表示されます。  
  
## <a name="remarks"></a>Remarks  
 UPDATE STATISTICS の NORECOMPUTE オプションを使用してインデックスが設定されている場合、その情報は**index_description**列に含まれます。  
  
 **sp_helpindex**は、順序付け可能インデックス列のみを公開します。そのため、XML インデックスや空間インデックスに関する情報は公開されません。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>例  
 次の例では、`Customer` テーブルのインデックスの種類に関するレポートを表示します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpindex N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;のストアドプロシージャのデータベースエンジン](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [SQL&#41;&#40;Transact-sql のインデックス](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [index_columns &#40;Transact-sql&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [システムストアドプロシージャ &#40;Transact-sql&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  

---
title: sp_helpindex (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_helpindex_TSQL
- sp_helpindex
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helpindex
ms.assetid: c7f73ba0-ec35-4b10-aa5f-f1487e51fbf7
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 16cfecbfdc412cbdb3518b4f658f7993ba17b853
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43101674"
---
# <a name="sphelpindex-transact-sql"></a>sp_helpindex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  テーブルまたはビューのインデックスに関する情報をレポートします。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpindex [ @objname = ] 'name'  
```  
  
## <a name="arguments"></a>引数  
 [ **@objname=** ] **'***name***'**  
 ユーザー定義テーブルやビューの、修飾付きまたは修飾なしの名前を指定します。 引用符は、テーブルまたはビューの修飾名を指定したときにのみ必要です。 データベース名を含む完全修飾名を指定する場合、データベース名は現在のデータベースの名前である必要があります。 *名前*は**nvarchar (776)**、既定値はありません。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**index_name**|**sysname**|インデックスの名前。|  
|**index_description**|**varchar(210)**|インデックスがあるファイル グループを含むインデックスの説明。|  
|**index_keys**|**nvarchar (2078)**|インデックスの作成で使用するテーブルまたはビュー内の列。|  
  
 降順のインデックス列は結果セットに表示され、列名の後にマイナス記号 (-) が付けられます。既定の昇順のインデックス列の場合は、その名前だけが表示されます。  
  
## <a name="remarks"></a>コメント  
 その情報が含まれている UPDATE STATISTICS の NORECOMPUTE オプションを使用してインデックスが設定されている場合、 **index_description**列。  
  
 **sp_helpindex**は順序付け可能なインデックス列だけを公開します。 したがって、これは公開されません XML インデックスまたは空間インデックスに関する情報。  
  
## <a name="permissions"></a>アクセス許可  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、`Customer` テーブルのインデックスの種類に関するレポートを表示します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpindex N'Sales.Customer';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [sys.indexes &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-indexes-transact-sql.md)   
 [sys.index_columns &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-index-columns-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [UPDATE STATISTICS &#40;Transact-SQL&#41;](../../t-sql/statements/update-statistics-transact-sql.md)  
  
  

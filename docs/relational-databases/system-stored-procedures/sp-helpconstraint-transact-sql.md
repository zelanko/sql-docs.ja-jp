---
title: "sp_helpconstraint (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_helpconstraint
- sp_helpconstraint_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helpconstraint
ms.assetid: 29d6cd36-535d-4765-bca8-62f9d9886ff5
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: dbd28705c736817c224762b1535acd34a22dc15e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelpconstraint-transact-sql"></a>sp_helpconstraint (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  すべての制約について、制約の種類、ユーザー定義名またはシステムから提供されている名前、制約が定義されている列、制約の定義式 (DEFAULT 制約と CHECK 制約の場合) などの一覧を返します。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helpconstraint [ @objname = ] 'table'   
     [ , [ @nomsg = ] 'no_message' ]   
```  
  
## <a name="arguments"></a>引数  
 [  **@objname=** ] **'***テーブル***'**  
 制約情報が返されるテーブルの名前です。 指定したテーブルは現在のデータベースに対してローカルである必要があります。 *テーブル*は**nvarchar (776)**、既定値はありません。  
  
 [  **@nomsg=**] **'***no_message***'**  
 テーブル名を出力する省略可能なパラメーターです。 *no_message*は**varchar (5)**、既定値は**msg**です。**nomsg**出力を抑制します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 **sp_helpconstraint**主キーに参加している場合は、降順のインデックス付き列を表示します。 降順のインデックス列は結果セットに表示され、列名の後にマイナス記号 (-) が付けられます。 既定の昇順のインデックス列の場合は、その名前だけが表示されます。  
  
## <a name="remarks"></a>解説  
 実行する**sp_help***テーブル*指定されたテーブルに関するすべての情報をレポートします。 制約情報だけを表示する**sp_helpconstraint**です。  
  
## <a name="permissions"></a>Permissions  
 ロール **public** のメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 この例では、`Product` テーブルの制約をすべて表示します。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helpconstraint 'Production.Product';  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sys.key_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-key-constraints-transact-sql.md)   
 [sys.check_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-check-constraints-transact-sql.md)   
 [sys.default_constraints &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-default-constraints-transact-sql.md)  
  
  

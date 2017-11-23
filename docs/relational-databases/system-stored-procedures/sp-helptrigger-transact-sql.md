---
title: "sp_helptrigger (TRANSACT-SQL) |Microsoft ドキュメント"
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
- sp_helptrigger
- sp_helptrigger_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_helptrigger
ms.assetid: e486d39b-771d-488d-a786-7136433a2203
caps.latest.revision: "37"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4065e8af5f1fc16a819a40aa1ec34b0a75e51c2e
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="sphelptrigger-transact-sql"></a>sp_helptrigger (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のデータベースにある、指定したテーブルに定義されている DML トリガーの種類を返します。 sp_helptrigger は DDL トリガーでは使用できません。 クエリ、[システム ストアド プロシージャ](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)カタログ ビューを代わりにします。  
  
||  
|-|  
|**適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]。|  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helptrigger [ @tabname = ] 'table'   
     [ , [ @triggertype = ] 'type' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@tabname=** ] **'***テーブル***'**  
 トリガー情報を返す現在のデータベース内にあるテーブルの名前を指定します。 *テーブル*は**nvarchar (776)**、既定値はありません。  
  
 [  **@triggertype=** ] **'***型***'**  
 情報を返す DML トリガーの種類を指定します。 *型*は**char (6)**、既定値は NULL、これらの値のいずれかを指定できます。  
  
|値|Description|  
|-----------|-----------------|  
|**DELETE**|DELETE トリガー情報を返します。|  
|**INSERT**|INSERT トリガー情報を返します。|  
|**UPDATE**|UPDATE トリガー情報を返します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
 次の表は、結果セットに表示される情報です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**trigger_name**|**sysname**|トリガーの名前。|  
|**trigger_owner**|**sysname**|トリガーが定義されたテーブルの所有者の名前。|  
|**isupdate**|**int**|1 = UPDATE トリガー。<br /><br /> 0 = UPDATE トリガー以外。|  
|**isdelete**|**int**|1 = DELETE トリガー。<br /><br /> 0 = DELETE トリガー以外。|  
|**isinsert**|**int**|1 = INSERT トリガー。<br /><br /> 0 = INSERT トリガー以外。|  
|**isafter**|**int**|1 = AFTER トリガー。<br /><br /> 0 = AFTER トリガー以外。|  
|**isinsteadof**|**int**|1 = INSTEAD OF トリガー。<br /><br /> 0 = INSTEAD OF トリガー以外。|  
|**trigger_schema**|**sysname**|トリガーが属するスキーマの名前。|  
  
## <a name="permissions"></a>Permissions  
 必要があります[Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)テーブルに対する権限。  
  
## <a name="examples"></a>使用例  
 次の例では実行`sp_helptrigger`でトリガーに関する情報を生成するために、`Person.Person`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
EXEC sp_helptrigger 'Person.Person';  
```  
  
## <a name="see-also"></a>参照  
 [データベース エンジンのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

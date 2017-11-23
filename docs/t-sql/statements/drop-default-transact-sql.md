---
title: "ドロップ既定 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/10/2017
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- DROP_DEFAULT_TSQL
- DROP DEFAULT
dev_langs: TSQL
helpviewer_keywords:
- DROP DEFAULT statement
- defaults [SQL Server], removing
ms.assetid: d2d3af25-8877-46ba-95d9-1844961d97ee
caps.latest.revision: "43"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 271155983d1fe6b1315235846f72e38d812b349c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="drop-default-transact-sql"></a>DROP DEFAULT (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  1 つ以上のユーザー定義のデフォルトを現在のデータベースから削除します。  
  
> [!IMPORTANT]  
>  DROP DEFAULT は、次のバージョンで削除予定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では、DROP DEFAULT の使用は避け、現在このオプションを使用しているアプリケーションは修正するようにしてください。 代わりに、既定の定義の DEFAULT キーワードを使用して作成できる[ALTER TABLE](../../t-sql/statements/alter-table-transact-sql.md)または[CREATE TABLE](../../t-sql/statements/create-table-transact-sql.md)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
DROP DEFAULT [ IF EXISTS ] { [ schema_name . ] default_name } [ ,...n ] [ ; ]  
```  
  
## <a name="arguments"></a>引数  
 *場合に存在します。*  
 **適用対象**: [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ([!INCLUDE[ssSQL15](../../includes/sssql15-md.md)] から [現在のバージョン](http://go.microsoft.com/fwlink/p/?LinkId=299658)まで)。  
  
 条件付きでは既に存在する場合にのみ、既定値を削除します。  
  
 *schema_name*  
 デフォルトが所属するスキーマの名前を指定します。  
  
 *default_name*  
 既存のデフォルトの名前です。 存在するための既定値の一覧を表示するには、次のように実行します。 **sp_help**です。 既定値は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 デフォルトのスキーマ名の指定は省略可能です。  
  
## <a name="remarks"></a>解説  
 既定値を削除する前に実行することで、既定値をバインド解除**sp_unbindefault**既定値は現在列または別名データ型にバインドされている場合。  
  
 NULL 値が許容される列からデフォルトを削除した後、行を追加しその値を明示的に指定しなかった場合、その位置には NULL が挿入されます。 NOT NULL 列からデフォルトを削除した後、行を追加しその値を明示的に指定しなかった場合は、エラー メッセージが返されます。 これらの行は、通常の INSERT ステートメントの動作の一部として後で追加されます。  
  
## <a name="permissions"></a>Permissions  
 DROP DEFAULT を実行するには、少なくとも、デフォルトが属するスキーマに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-dropping-a-default"></a>A. デフォルトを削除する  
 デフォルトが列または別名データ型にバインドされていない場合は、DROP DEFAULT を使うだけで削除できます。 次の例では、ユーザーが作成した既定の名前付き`datedflt`します。  
  
```  
USE AdventureWorks2012;  
GO  
IF EXISTS (SELECT name FROM sys.objects  
         WHERE name = 'datedflt'   
            AND type = 'D')  
   DROP DEFAULT datedflt;  
GO  
```  
  
 以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]次の構文を使用することができます。  
  
```  
DROP DEFAULT IF EXISTS datedflt;  
GO  
```  
  
### <a name="b-dropping-a-default-that-has-been-bound-to-a-column"></a>B. 列にバインドされたデフォルトを削除する  
 次の例では、`EmergencyContactPhone` テーブルの `Contact` 列に関連付けられているデフォルトをアンバインドし、デフォルト `phonedflt` を削除します。  
  
```  
USE AdventureWorks2012;  
GO  
   BEGIN   
      EXEC sp_unbindefault 'Person.Contact.Phone'  
      DROP DEFAULT phonedflt  
   END;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [CREATE DEFAULT &#40;Transact-SQL&#41;](../../t-sql/statements/create-default-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_unbindefault &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-unbindefault-transact-sql.md)  
  
  

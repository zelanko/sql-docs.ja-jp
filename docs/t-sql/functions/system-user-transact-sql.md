---
title: "SYSTEM_USER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SYSTEM_USER_TSQL
- SYSTEM_USER
dev_langs: TSQL
helpviewer_keywords:
- current user names
- system-supplied user names [SQL Server]
- users [SQL Server], logins
- logins [SQL Server], identification name
- current system user names
- SYSTEM_USER function
- inserting system user name into table
- system usernames [SQL Server]
- users [SQL Server], names
ms.assetid: 565984cd-60c6-4df7-83ea-2349b838ccb2
caps.latest.revision: "44"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 070e6a1b7d2e739b3f2b1f4c594ffdecd25fcb85
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="systemuser-transact-sql"></a>SYSTEM_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  現在のログインに既定値が指定されていない場合に、システム提供の値をテーブルに挿入します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SYSTEM_USER  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nchar**  
  
## <a name="remarks"></a>解説  
 SYSTEM_USER 関数は、CREATE TABLE および ALTER TABLE ステートメント内で DEFAULT 制約と共に使用できます。 標準的な関数としても使用できます。  
  
 ユーザー名とログイン名が異なる場合、SYSTEM_USER ではログイン名が返されます。  
  
 現在のユーザーにログオンしている場合[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows 認証を使用すると、SYSTEM_USER が形式で Windows ログインの識別名を返します:*ドメイン*\\*user_login_name*. 現在のユーザーが SQL Server 認証によって [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にログインした場合は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ログインの識別名が返されます。たとえば、`WillisJo` としてログインしたユーザーの場合は `WillisJo` が返されます。  
  
 SYSTEM_USER では、現在の実行コンテキストの名前が返されます。 EXECUTE AS ステートメントを使用してコンテキストが切り替えられていた場合、SYSTEM_USER では権限が借用されたコンテキストの名前が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-systemuser-to-return-the-current-system-user-name"></a>A. SYSTEM_USER を使用して現在のシステム ユーザー名を返す  
 次の例で、`char`変数の現在の値を格納する`SYSTEM_USER`の変数、インストールし、変数に格納されている値を出力します。  
  
```  
DECLARE @sys_usr char(30);  
SET @sys_usr = SYSTEM_USER;  
SELECT 'The current system user is: '+ @sys_usr;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
----------------------------------------------------------
The current system user is: WillisJo

(1 row(s) affected)
 ```  
  
### <a name="b-using-systemuser-with-default-constraints"></a>B. SYSTEM_USER を DEFAULT 制約と共に使用する  
 次の例では、テーブルを作成し、`SYSTEM_USER` 列の `DEFAULT` 制約として `SRep_tracking_user` を使用します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE Sales.Sales_Tracking  
(  
    Territory_id int IDENTITY(2000, 1) NOT NULL,  
    Rep_id  int NOT NULL,  
    Last_sale datetime NOT NULL DEFAULT GETDATE(),  
    SRep_tracking_user varchar(30) NOT NULL DEFAULT SYSTEM_USER  
);  
GO  
INSERT Sales.Sales_Tracking (Rep_id)  
VALUES (151);  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (293, '19980515');  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (27882, '19980620');  
INSERT Sales.Sales_Tracking (Rep_id)  
VALUES (21392);  
INSERT Sales.Sales_Tracking (Rep_id, Last_sale)  
VALUES (24283, '19981130');  
GO  
```  
  
 すべての情報を選択する次のクエリ、`Sales_Tracking`テーブル。  
  
```  
SELECT * FROM Sales_Tracking ORDER BY Rep_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Territory_id Rep_id Last_sale            SRep_tracking_user
-----------  ------ -------------------- ------------------
2000         151    Mar 4 1998 10:36AM   ArvinDak
2001         293    May 15 1998 12:00AM  ArvinDak
2003         21392  Mar 4 1998 10:36AM   ArvinDak
2004         24283  Nov 3 1998 12:00AM   ArvinDak
2002         27882  Jun 20 1998 12:00AM  ArvinDak
  
(5 row(s) affected)
 ```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-systemuser-to-return-the-current-system-user-name"></a>C: では、SYSTEM_USER を使用して、現在のシステム ユーザー名を取得するには  
 次の例は、の現在の値を返します`SYSTEM_USER`です。  
  
```  
SELECT SYSTEM_USER;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-user-transact-sql.md)   
 [SESSION_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/session-user-transact-sql.md)   
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [ユーザーと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-transact-sql.md)  
  
  


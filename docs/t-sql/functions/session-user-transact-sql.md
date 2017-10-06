---
title: "SESSION_USER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SESSION_USER_TSQL
- SESSION_USER
dev_langs:
- TSQL
helpviewer_keywords:
- usernames [SQL Server]
- current user names
- sessions [SQL Server], user names
- displaying user names
- viewing user names
- SESSION_USER function
ms.assetid: 3dbe8532-31b6-4862-8b2a-e58b00b964de
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 88b9d27bfc084e341712c374c54098984c0f3e95
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="sessionuser-transact-sql"></a>SESSION_USER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在のデータベースに含まれる現在のコンテキストのユーザー名を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SESSION_USER  
```  
  
## <a name="return-types"></a>戻り値の型  
 **nvarchar (128)**  
  
## <a name="remarks"></a>解説  
 SESSION_USER は、DEFAULT 制約と共に CREATE TABLE または ALTER TABLE ステートメント内で使用するか、標準の関数として使用します。 SESSION_USER は、既定値が指定されていなければテーブルに挿入できます。 この関数は引数をとりません。 SESSION_USER はクエリで使用できます。  
  
 コンテキスト切り替え後に SESSION_USER が呼び出された場合、SESSION_USER では借用したコンテキストのユーザー名が返されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-sessionuser-to-return-the-user-name-of-the-current-session"></a>A. SESSION_USER を使用して現在のセッションのユーザー名を返す  
 次の例として、変数を宣言する`nchar`の現在の値を割り当てます`SESSION_USER`、その変数をして、テキストの説明の変数を出力します。  
  
```  
DECLARE @session_usr nchar(30);  
SET @session_usr = SESSION_USER;  
SELECT 'This session''s current user is: '+ @session_usr;  
GO  
```  
  
 セッション ユーザーが `Surya` の場合の結果セットは次のとおりです。  
  
 ```
--------------------------------------------------------------
This session's current user is: Surya

(1 row(s) affected)
```  
  
### <a name="b-using-sessionuser-with-default-constraints"></a>B. SESSION_USER を DEFAULT 制約とを使用します。  
 次の例では、荷物の受領記録者の名前に対し、`SESSION_USER` を `DEFAULT` 制約として使用するテーブルを作成します。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE deliveries3  
(  
 order_id int IDENTITY(5000, 1) NOT NULL,  
 cust_id  int NOT NULL,  
 order_date smalldatetime NOT NULL DEFAULT GETDATE(),  
 delivery_date smalldatetime NOT NULL DEFAULT   
    DATEADD(dd, 10, GETDATE()),  
 received_shipment nchar(30) NOT NULL DEFAULT SESSION_USER  
);  
GO  
```  
  
 テーブルに追加されたレコードに対して、現在のユーザーのユーザー名が設定されます。 この例では`Wanida`、 `Sylvester`、および`Alejandro`荷物の受領を確認してください。 `EXECUTE AS` を使用してユーザー コンテキストを切り替えることでも、同様の機能を実現できます。  
  
```  
EXECUTE AS USER = 'Wanida'  
INSERT deliveries3 (cust_id)  
VALUES (7510);  
INSERT deliveries3 (cust_id)  
VALUES (7231);  
REVERT;  
EXECUTE AS USER = 'Sylvester'  
INSERT deliveries3 (cust_id)  
VALUES (7028);  
REVERT;  
EXECUTE AS USER = 'Alejandro'  
INSERT deliveries3 (cust_id)  
VALUES (7392);  
INSERT deliveries3 (cust_id)  
VALUES (7452);  
REVERT;  
GO  
```  
  
 次のクエリでは、`deliveries3` テーブルからすべての情報を選択します。  
  
```  
SELECT order_id AS 'Order #', cust_id AS 'Customer #',   
   delivery_date AS 'When Delivered', received_shipment   
   AS 'Received By'  
FROM deliveries3  
ORDER BY order_id;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```
Order #   Customer #  When Delivered       Received By
--------  ----------  -------------------  -----------
5000      7510        2005-03-16 12:02:14  Wanida
5001      7231        2005-03-16 12:02:14  Wanida
5002      7028        2005-03-16 12:02:14  Sylvester
5003      7392        2005-03-16 12:02:14  Alejandro
5004      7452        2005-03-16 12:02:14  Alejandro

(5 row(s) affected)
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="c-using-sessionuser-to-return-the-user-name-of-the-current-session"></a>C: SESSION_USER を使用して、現在のセッションのユーザー名を返す  
 次の例では、現在のセッションのセッションのユーザーを返します。  
  
```  
SELECT SESSION_USER;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [CURRENT_TIMESTAMP & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-timestamp-transact-sql.md)   
 [CURRENT_USER と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/current-user-transact-sql.md)   
 [SYSTEM_USER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/system-user-transact-sql.md)   
 [システム関数 &#40;Transact-SQL&#41;](../../relational-databases/system-functions/system-functions-for-transact-sql.md)   
 [ユーザーと #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-transact-sql.md)   
 [USER_NAME & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/user-name-transact-sql.md)  
  
  



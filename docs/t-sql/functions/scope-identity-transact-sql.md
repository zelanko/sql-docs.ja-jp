---
title: "SCOPE_IDENTITY (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/06/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SCOPE_IDENTITY
- SCOPE_IDENTITY_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- identity columns [SQL Server], SCOPE_IDENTITY function
- SCOPE_IDENTITY function
- last-inserted identity values
- identity values [SQL Server], last-inserted
ms.assetid: eef24670-059b-4f10-91d4-a67bc1ed12ab
caps.latest.revision: 36
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1950d65a35d6fab52025d069e0338493ee7c639d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="scopeidentity-transact-sql"></a>SCOPE_IDENTITY (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  同じスコープ内の ID 列に挿入された最後の ID 値を返します。 スコープは、ストアド プロシージャ、トリガー、関数、バッチのいずれかのモジュールです。 したがって、2 つのステートメントが同じストアド プロシージャ、関数、またはバッチである場合は、同じスコープ内ではです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
SCOPE_IDENTITY()  
```  
  
## <a name="return-types"></a>戻り値の型  
 **numeric(38,0)**  
  
## <a name="remarks"></a>解説  
 SCOPE_IDENTITY、IDENT_CURRENT、および @@IDENTITY id 列に挿入される値を返すという同様の機能は、します。  
  
 IDENT_CURRENT はスコープとセッションには限定されませんが、特定のテーブルに限定されます。 IDENT_CURRENT では、任意のセッションとスコープ内の特定のテーブルに対して生成された値が返されます。 詳細については、次を参照してください。 [IDENT_CURRENT (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ident-current-transact-sql.md).  
  
 SCOPE_IDENTITY と @@IDENTITYは任意のテーブルで、現在のセッションで生成した最後の id 値を返します。 ただし、SCOPE_IDENTITY は、現在のスコープ内でのみ挿入された値を返します@@IDENTITYは、特定のスコープに限定されません。  
  
 たとえば、T1 と T2 の 2 つのテーブルがあるとし、INSERT トリガーが T1 で定義されているとします。 T1 に行が挿入されると、トリガーが起動し、T2 に行を挿入します。 このシナリオでは、T1 上での挿入と、トリガーの結果として得られる T2 上での挿入という、2 つのスコープがあります。  
  
 想定される T1 と T2 の両方が id 列をある@IDENTITYSCOPE_IDENTITY は、T1 で INSERT ステートメントの最後に異なる値を返すとします。 @@IDENTITY現在のセッションで任意のスコープにおいて挿入された最後の id 列の値を返します。 これは、T2 で挿入された値です。 SCOPE_IDENTITY() では、T1 に挿入された IDENTITY 値を返します。 これは、同じスコープ内で発生した最後の挿入です。 SCOPE_IDENTITY() 関数は、id 列への INSERT ステートメントのスコープ内で発生する前に、関数が呼び出された場合に、null 値を返します。  
  
 失敗したステートメントとトランザクションによって、テーブルに対する現在の ID が変更され、ID 列値に差異が生じる可能性があります。 ID 値がロールバックされることはありません。これは、テーブルに値を挿入するトランザクションがコミットされない場合でも同じです。 たとえば、INSERT ステートメントが IGNORE_DUP_KEY 違反のために失敗しても、テーブルの現在の ID 値は増分されます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-identity-and-scopeidentity-with-triggers"></a>A. を使用して@IDENTITYおよび SCOPE_IDENTITY をトリガーで  
 次の例は、2 つのテーブルを作成`TZ`と`TY`とに INSERT トリガー`TZ`です。 行が挿入されるテーブルに`TZ`、トリガー (`Ztrig`) が起動し、行を挿入`TY`です。  
  
```sql  
USE tempdb;  
GO  
CREATE TABLE TZ (  
   Z_id  int IDENTITY(1,1)PRIMARY KEY,  
   Z_name varchar(20) NOT NULL);  
  
INSERT TZ  
   VALUES ('Lisa'),('Mike'),('Carla');  
  
SELECT * FROM TZ;  
```     
結果セット: これは、どのようなテーブル TZ です。  
  
```  
Z_id   Z_name  
-------------  
1      Lisa  
2      Mike  
3      Carla  
```  
```sql 
CREATE TABLE TY (  
   Y_id  int IDENTITY(100,5)PRIMARY KEY,  
   Y_name varchar(20) NULL);  
  
INSERT TY (Y_name)  
   VALUES ('boathouse'), ('rocks'), ('elevator');  
  
SELECT * FROM TY;  
```   
結果セット: これは、どのような TY:  
```  
Y_id  Y_name  
---------------  
100   boathouse  
105   rocks  
110   elevator  
```  

TZ をテーブルに行が挿入されたときに、TY のテーブルに行を挿入するトリガーを作成します。  
```sql  
CREATE TRIGGER Ztrig  
ON TZ  
FOR INSERT AS   
   BEGIN  
   INSERT TY VALUES ('')  
   END;  
```  
トリガーを起動しを入手する id 値を確認する、@@IDENTITYおよび SCOPE_IDENTITY 関数。   
```sql
INSERT TZ VALUES ('Rosalie');  
  
SELECT SCOPE_IDENTITY() AS [SCOPE_IDENTITY];  
GO  
SELECT @@IDENTITY AS [@@IDENTITY];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```
/*SCOPE_IDENTITY returns the last identity value in the same scope. This was the insert on table TZ.*/`  
SCOPE_IDENTITY  
4  

/*@@IDENTITY returns the last identity value inserted to TY by the trigger. 
  This fired because of an earlier insert on TZ.*/
@@IDENTITY  
115  
```  
  
### <a name="b-using-identity-and-scopeidentity-with-replication"></a>B. を使用して@IDENTITYおよび SCOPE_IDENTITY() をレプリケーションで  
 次の例を使用する方法を示して`@@IDENTITY`と`SCOPE_IDENTITY()`のマージ レプリケーション用にパブリッシュされるデータベースに挿入します。 両方のテーブルの例では、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]サンプル データベース:`Person.ContactType`はパブリッシュされず`Sales.Customer`が公開します。 マージ レプリケーションでは、パブリッシュされたテーブルにトリガーを追加します。 したがって、`@@IDENTITY`ユーザー テーブルへの挿入ではなく、レプリケーション システム テーブルに挿入値を返すことができます。  
  
 `Person.ContactType`テーブルには、最大 id 値の 20 です。 このテーブルに行を挿入する場合、`@@IDENTITY` と `SCOPE_IDENTITY()` は同じ値を返します。  
  
```sql  
USE AdventureWorks2012;  
GO  
INSERT INTO Person.ContactType ([Name]) VALUES ('Assistant to the Manager');  
GO  
SELECT SCOPE_IDENTITY() AS [SCOPE_IDENTITY];  
GO  
SELECT @@IDENTITY AS [@@IDENTITY];  
GO  
```  
  
[!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
```  
SCOPE_IDENTITY  
21  
@@IDENTITY  
21
```  
  
 `Sales.Customer`テーブルに id 値の最大値は 29483 です。 テーブルに行を挿入する場合`@@IDENTITY`と`SCOPE_IDENTITY()`異なる値を返します。 `SCOPE_IDENTITY()` は値をユーザー テーブルに挿入して返すのに対し、`@@IDENTITY` は値をレプリケーション システム テーブルに挿入して返します。 挿入した ID 値にアクセスする必要があるアプリケーションには、`SCOPE_IDENTITY()` を使用してください。  
  
```sql  
INSERT INTO Sales.Customer ([TerritoryID],[PersonID]) VALUES (8,NULL);  
GO  
SELECT SCOPE_IDENTITY() AS [SCOPE_IDENTITY];  
GO  
SELECT @@IDENTITY AS [@@IDENTITY];  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
 ```
 SCOPE_IDENTITY  
 29484  
 @@IDENTITY  
 89
 ```  
  
## <a name="see-also"></a>参照  
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)  
  
  


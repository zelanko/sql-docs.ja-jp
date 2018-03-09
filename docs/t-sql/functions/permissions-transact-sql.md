---
title: "権限 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PERMISSIONS_TSQL
- PERMISSIONS
dev_langs:
- TSQL
helpviewer_keywords:
- permissions [SQL Server], verifying
- current permission status
- users [SQL Server], permissions status
- checking permission status
- security [SQL Server], permissions
- verifying permission status
- testing permissions
- PERMISSIONS function
ms.assetid: 81625a56-b160-4424-91c5-1ce8b259a8e6
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: d1d8b8fff2313559c2a076ed761d0792fafd5001
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="permissions-transact-sql"></a>PERMISSIONS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  現在のユーザーのステートメント権限、オブジェクト権限、または列権限を示すビットマップを含む値を返します。  
  
 **重要な**[!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]使用[fn_my_permissions](../../relational-databases/system-functions/sys-fn-my-permissions-transact-sql.md)と[Has_Perms_By_Name](../../t-sql/functions/has-perms-by-name-transact-sql.md)代わりにします。 PERMISSIONS 関数を継続して使用すると、パフォーマンスが低下する場合があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
PERMISSIONS ( [ objectid [ , 'column' ] ] )  
```  
  
## <a name="arguments"></a>引数  
 *objectid*  
 セキュリティ保護可能なリソースの ID を指定します。 場合*objectid*はビットマップ値には、現在のユーザーのステートメント権限が含まれています。 指定しないと、です。 それ以外の場合、ビットマップが、セキュリティ保護可能な、現在のユーザーのアクセス許可が含まれます。 指定したセキュリティ保護可能なリソースは、現在のデータベースに存在する必要があります。 使用して、 [OBJECT_ID](../../t-sql/functions/object-id-transact-sql.md)を判断する関数、 *objectid*値。  
  
 **'** *列* **'**  
 権限情報を返す列の名前を指定します (省略可能)。 列が有効な列名で指定されたテーブル内にある必要があります*objectid*です。  
  
## <a name="return-types"></a>戻り値の型  
 **int**  
  
## <a name="remarks"></a>解説  
 PERMISSIONS は、現在のユーザーがステートメントを実行するのに必要な権限を所有しているか、または別のユーザーに対して権限を許可 (GRANT) できるかを調べるときに使用できます。  
  
 返される権限情報は 32 ビットのビットマップです。  
  
 下位 16 ビットは、ユーザーに許可されている権限と、現在のユーザーがメンバーである Windows グループまたは固定サーバー ロールに適用されている権限を表します。 たとえば、返された値 66 (16 進値 0x42) のない場合*objectid*が指定されている、ユーザーが、CREATE TABLE (10 進値 2) とデータベースのバックアップ (10 進値の 64) ステートメントを実行する権限を持っていることを示します。  
  
 上位 16 ビットは、ユーザーが他のユーザーに許可 (GRANT) できる権限を表します。 上位 16 ビットの解釈は、次の表の下位 16 ビットを左側に 16 ビット移す (65,536 を乗算する) だけです。 たとえば、0x8 (10 進数 8) には、ビットを INSERT 権限を示すときに、 *objectid*を指定します。 これに対して、0x80000 (10 進値の 524288) は、524288 = 8 × 65536 であり、INSERT 権限を許可 (GRANT) できることを表します。  
  
 ロールのメンバーシップにより、ステートメントの実行権限のないユーザーでも、他のユーザーに権限を許可できる場合があります。  
  
 次の表では、ステートメント権限に対して使用されるビット (*objectid*が指定されていません)。  
  
|ビット (10 進)|ビット (16 進)|ステートメント権限|  
|-----------------|-----------------|--------------------------|  
|1|0x1|CREATE DATABASE (master データベースのみ)|  
|2|0x2|CREATE TABLE|  
|4|0x4|CREATE PROCEDURE|  
|8|0x8|CREATE VIEW|  
|16|0x10|CREATE RULE|  
|32|0x20|CREATE DEFAULT|  
|64|0x40|BACKUP DATABASE|  
|128|0x80|BACKUP LOG|  
|256|0x100|予約済み。|  
  
 次の表に、時にのみ返されるオブジェクトのアクセス許可に使用されるビット*objectid*を指定します。  
  
|ビット (10 進)|ビット (16 進)|ステートメント権限|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT ALL|  
|2|0x2|UPDATE ALL|  
|4|0x4|REFERENCES ALL|  
|8|0x8|INSERT|  
|16|0x10|DELETE|  
|32|0x20|EXECUTE (プロシージャのみ)|  
|4096|0x1000|SELECT ANY (少なくとも 1 列)|  
|8192|0x2000|UPDATE ANY|  
|16384|0x4000|REFERENCES ANY|  
  
 次の表に、ときに返される列レベルのオブジェクトのアクセス許可に使用されるビット両方*objectid*および列を指定します。  
  
|ビット (10 進)|ビット (16 進)|ステートメント権限|  
|-----------------|-----------------|--------------------------|  
|1|0x1|SELECT|  
|2|0x2|UPDATE|  
|4|0x4|REFERENCES|  
  
 指定されたパラメーターが NULL または有効でない場合、NULL が返されます (たとえば、 *objectid*または列が存在しません)。 適用されない権限 (テーブルに対するビット 0x20 の EXECUTE 権限など) のビット値は定義されていません。  
  
 PERMISSIONS 関数で返すビットマップ内の各ビットを指定するには、ビットごとの AND 演算子 (&) を使用します。  
  
 現在のデータベース内のユーザーに与えられている権限の一覧を返すには、sp_helprotect システム ストアド プロシージャを使用することもできます。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-the-permissions-function-with-statement-permissions"></a>A. PERMISSIONS 関数をステートメント権限に対して使用する  
 次の例では、現在のユーザーが実行できるかどうかを判断、`CREATE TABLE`ステートメントです。  
  
```  
IF PERMISSIONS()&2=2  
   CREATE TABLE test_table (col1 INT)  
ELSE  
   PRINT 'ERROR: The current user cannot create a table.';  
```  
  
### <a name="b-using-the-permissions-function-with-object-permissions"></a>B. PERMISSIONS 関数をオブジェクト権限に対して用する  
 次の例では、現在のユーザーが `Address` データベース内の `AdventureWorks2012` テーブルにデータ行を挿入できるかどうかを判定します。  
  
```  
IF PERMISSIONS(OBJECT_ID('AdventureWorks2012.Person.Address','U'))&8=8   
   PRINT 'The current user can insert data into Person.Address.'  
ELSE  
   PRINT 'ERROR: The current user cannot insert data into Person.Address.';  
```  
  
### <a name="c-using-the-permissions-function-with-grantable-permissions"></a>C. PERMISSIONS 関数を、付与できる権限に対して使用する  
 次の例では、現在のユーザーが別のユーザーに `Address` データベース内の `AdventureWorks2012` テーブルに対する INSERT 権限を許可できるかどうかを判定します。  
  
```  
IF PERMISSIONS(OBJECT_ID('AdventureWorks2012.Person.Address','U'))&0x80000=0x80000  
   PRINT 'INSERT on Person.Address is grantable.'  
ELSE  
   PRINT 'You may not GRANT INSERT permissions on Person.Address.';  
```  
  
## <a name="see-also"></a>参照  
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [OBJECT_ID と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/object-id-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [sp_helprotec &#40;TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-helprotect-transact-sql.md)   
 [システム関数 &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  

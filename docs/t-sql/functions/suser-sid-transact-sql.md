---
title: "SUSER_SID (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/29/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SUSER_SID
- SUSER_SID_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- logins [SQL Server], users
- SIDs [SQL Server]
- security identifiers [SQL Server]
- users [SQL Server], logins
- 15401 (Database Engine error)
- IDs [SQL Server], logins
- identification numbers [SQL Server], logins
- SUSER_SID function
ms.assetid: 57b42a74-94e1-4326-85f1-701b9de53c7d
caps.latest.revision: 31
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: ab02d47027f970e05820bc377d72f60938b52b62
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="susersid-transact-sql"></a>SUSER_SID (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  指定されたログイン名のセキュリティ ID 番号 (SID) を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
SUSER_SID ( [ 'login' ] [ , Param2 ] )   
```  
  
## <a name="arguments"></a>引数  
 **'** *ログイン* **'**  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ユーザーのログイン名を指定します。 *ログイン*は**sysname**です。 *ログイン*、省略可能であるを指定できます、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ログインまたは[!INCLUDE[msCoName](../../includes/msconame-md.md)]Windows ユーザーまたはグループ。 場合*ログイン*が指定されていない、現在のセキュリティ コンテキストに関する情報が返されます。 パラメーターに "NULL" という語が含まれていると、NULL が返されます。  
  
 *Param2 を含みます*  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
 ログイン名を検証するかどうかを指定します。 *Param2*の種類は**int**は省略可能です。 ときに*Param2*が 0 の場合、ログイン名は検証されません。 ときに*Param2*が指定されていない 0 として、Windows ログイン名はログイン名と同じであるに保存されていることを確認[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
## <a name="return-types"></a>戻り値の型  
 **varbinary (85)**  
  
## <a name="remarks"></a>解説  
 SUSER_SID は、ALTER TABLE または CREATE TABLE の中で、DEFAULT 制約として使用できます。 SUSER_SID は、選択リストの中、WHERE 句の中、また、式を使える所ならどこにでも使用できます。 SUSER_SID の後には、パラメーターを指定しない場合も含め、常にかっこが必要です。  
  
 SUSER_SID を引数なしで呼び出すと、現在のセキュリティ コンテキストの SID が返されます。 EXECUTE AS を使用してコンテキストを切り替えたバッチ内で SUSER_SID を引数なしで呼び出すと、権限を借用したコンテキストの SID が返されます。 権限を借用したコンテキストから SUSER_SID(ORIGINAL_LOGIN()) を呼び出すと、元のコンテキストの SID が返されます。  
  
 ときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]照合順序と Windows 照合順序が異なる、ときに SUSER_SID は失敗する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Windows ログインを格納する別の形式とします。 たとえば、Windows コンピューター TestComputer のログインが User で、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] にはそのログインが TESTCOMPUTER\User として格納されている場合、ログイン TestComputer\User を参照したときにログイン名を正しく解決できないことがあります。 ログイン名には、この検証をスキップするには、使用*Param2*です。 異なる照合順序の原因は、多くの場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]エラー 15401 が発生します。  
  
 `Windows NT user or group '%s' not found. Check the name again.`  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-susersid"></a>A. SUSER_SID を使用する  
 次の例では、現在のセキュリティ コンテキストのセキュリティ ID 番号 (SID) を返します。  
  
```  
SELECT SUSER_SID('sa');  
```  
  
### <a name="b-using-susersid-with-a-specific-login"></a>B. SUSER_SID を特定のログインと共に使用する  
 次の例は、のセキュリティ識別番号を返します、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] `sa`ログインします。  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SID('sa');  
GO  
```  
  
### <a name="c-using-susersid-with-a-windows-user-name"></a>C. SUSER_SID を Windows ユーザー名と共に使用する  
 次の例では、Windows ユーザーである `London\Workstation1` のセキュリティ ID 番号を返します。  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SID('London\Workstation1');  
GO  
```  
  
### <a name="d-using-susersid-as-a-default-constraint"></a>D. SUSER_SID を DEFAULT 制約として使用する  
 次の例では、`SUSER_SID` ステートメントで `DEFAULT` を `CREATE TABLE` 制約として使用しています。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE sid_example  
(  
login_sid   varbinary(85) DEFAULT SUSER_SID(),  
login_name  varchar(30) DEFAULT SYSTEM_USER,  
login_dept  varchar(10) DEFAULT 'SALES',  
login_date  datetime DEFAULT GETDATE()  
);   
GO  
INSERT sid_example DEFAULT VALUES;  
GO  
```  
  
### <a name="e-comparing-the-windows-login-name-to-the-login-name-stored-in-sql-server"></a>E. Windows ログイン名と SQL Server に格納されたログイン名を比較する  
 次の例は、使用する方法を示しています。 *Param2* Windows から SID を取得するへの入力としてその SID を使用して、`SUSER_SNAME`関数。 Windows に格納された形式 (`TestComputer\User`) でログインを指定し、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] に格納された形式 (`TESTCOMPUTER\User`) のログインを取得しています。  
  
**適用されます**:[!INCLUDE[ssSQL11](../../includes/sssql11-md.md)]経由[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]
  
```  
SELECT SUSER_SNAME(SUSER_SID('TestComputer\User', 0));  
```  
  
## <a name="see-also"></a>参照  
 [ORIGINAL_LOGIN & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/original-login-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [binary と varbinary & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/binary-and-varbinary-transact-sql.md)   
 [システム関数 & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-functions/system-functions-for-transact-sql.md)  
  
  


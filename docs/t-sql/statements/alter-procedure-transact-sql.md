---
title: "ALTER PROCEDURE (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/01/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER_PROCEDURE_TSQL
- ALTER_PROC_TSQL
- ALTER PROC
- ALTER PROCEDURE
dev_langs:
- TSQL
helpviewer_keywords:
- ALTER PROCEDURE statement
- stored procedure modifications [SQL Server]
- modifying stored procedures
- stored procedures [SQL Server], modifying
ms.assetid: ed9b2f76-11ec-498d-a95e-75b490a75733
caps.latest.revision: 69
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3dc195d3f6ca908253ff5726c3f336435e7f2bd1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-procedure-transact-sql"></a>ALTER PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all_md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  内の CREATE PROCEDURE ステートメントを実行することによって作成された以前に作成したプロシージャ変更[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [TRANSACT-SQL 構文表記規則 (TRANSACT-SQL)](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database
  
ALTER { PROC | PROCEDURE } [schema_name.] procedure_name [ ; number ]   
    [ { @parameter [ type_schema_name. ] data_type }   
        [ VARYING ] [ = default ] [ OUT | OUTPUT ] [READONLY]  
    ] [ ,...n ]   
[ WITH <procedure_option> [ ,...n ] ]  
[ FOR REPLICATION ]   
AS { [ BEGIN ] sql_statement [;] [ ...n ] [ END ] }  
[;]  
  
<procedure_option> ::=   
    [ ENCRYPTION ]  
    [ RECOMPILE ]  
    [ EXECUTE AS Clause ]  
```  
  
```  
-- Syntax for SQL Server CLR Stored Procedure  
  
ALTER { PROC | PROCEDURE } [schema_name.] procedure_name [ ; number ]   
    [ { @parameter [ type_schema_name. ] data_type }   
        [ = default ] [ OUT | OUTPUT ] [READONLY]  
    ] [ ,...n ]   
[ WITH EXECUTE AS Clause ]  
AS { EXTERNAL NAME assembly_name.class_name.method_name }  
[;]  
```  
  
```tsql  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
ALTER { PROC | PROCEDURE } [schema_name.] procedure_name  
    [ { @parameterdata_type } [= ] ] [ ,...n ]  
AS { [ BEGIN ] sql_statement [ ; ] [ ,...n ] [ END ] }  
[;]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 プロシージャが属するスキーマの名前を指定します。  
  
 *procedure_name*  
 変更するプロシージャの名前を指定します。 プロシージャ名は、 [識別子](../../relational-databases/databases/database-identifiers.md)のルールに従っている必要があります。  
  
 **;** *数*  
 既存の省略可能な整数で使用される同じ名前のプロシージャをグループ化できるように、DROP PROCEDURE ステートメントを使用して、まとめて削除できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 **@***パラメーター*  
 プロシージャ内のパラメーターです。 パラメーターは 2,100 個まで指定できます。  
  
 [ *type_schema_name***です。** *data_type*  
 パラメーターのデータ型とそれが属するスキーマを指定します。  
  
 データ型の制限については、次を参照してください。 [CREATE PROCEDURE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-procedure-transact-sql.md).  
  
 VARYING  
 出力パラメーターとしてサポートされている結果セットを指定します。 このパラメーターは、ストアド プロシージャによって動的に構築され、その内容を変更ことができます。 カーソル パラメーターにのみ適用されます。 このオプションは、CLR プロシージャでは無効です。  
  
 *既定値*  
 パラメーターの既定値です。  
  
 OUT | OUTPUT  
 パラメーターが、戻りパラメーターであることを示します。  
  
 READONLY  
 パラメーターを更新またはプロシージャの本体内で変更できないことを示します。 パラメーターの型がテーブル値型の場合は、READONLY を指定する必要があります。  
  
 RECOMPILE  
 示します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]実行時にこの手順と、プロシージャのプランが再コンパイルをキャッシュせずします。  
  
 ENCRYPTION  
 **適用されます**: SQL Server ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]) と[!INCLUDE[ssSDSFull](../../includes/sssdsfull-md.md)]です。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]で、ALTER PROCEDURE ステートメントの元のテキストを、暗号化した形式に変換することを示します。 難読化の出力内のカタログ ビューのいずれかで直接表示がない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 システム テーブルまたはデータベース ファイルへのアクセスがないユーザーは、難読化テキストを取得できません。 ただし、テキストができるように特権を持つ経由でシステム テーブルにアクセスできるか、 [DAC ポート](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)または直接データベース ファイルにアクセスします。 また、サーバー プロセスにデバッガーをアタッチできるユーザーは、実行時にメモリから元のプロシージャを取得できます。 システム メタデータへのアクセスの詳細については、次を参照してください。 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)です。  
  
 このオプションで作成されたプロシージャは、の一部としてパブリッシュできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション。  
  
 このオプションは、共通言語ランタイム (CLR) のストアド プロシージャには指定できません。  
  
> [!NOTE]  
>  アップグレードの際、[!INCLUDE[ssDE](../../includes/ssde-md.md)]に格納されている暗号化コメントを使用して**sys.sql_modules**プロシージャが再作成します。  
  
 EXECUTE AS  
 アクセス後にストアド プロシージャを実行するセキュリティ コンテキストを指定します。  
  
 詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)」を参照してください。  
  
 FOR REPLICATION  

  
 レプリケーション用に作成したストアド プロシージャは、サブスクライバーでは実行できないことを示します。 FOR REPLICATION オプションを指定して作成したストアド プロシージャは、ストアド プロシージャ フィルターとして使用され、レプリケーション時にのみ実行されます。 FOR REPLICATION を指定した場合、パラメーターは宣言できません。 このオプションは、CLR プロシージャでは無効です。 RECOMPILE オプションは、FOR REPLICATION を使って作成されたプロシージャでは無視されます。  
  
> [!NOTE]  
>  このオプションは、包含データベースでは使用できません。  
  
 {[BEGIN] *sql_statement* [;][ ... *n*  ] [終了]}  
 プロシージャの本体を構成する 1 つ以上の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定します。 省略可能な BEGIN キーワードと END キーワードを使用して、ステートメントを囲むことができます。 詳細については、セクションを参照して、ベスト プラクティス、全般的な解説と制限事項と制約で[CREATE PROCEDURE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-procedure-transact-sql.md).  
  
 外部名*assembly_name***.***class_name***.***メソッド名が*  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 メソッドを指定します、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR アセンブリのストアド プロシージャで参照します。 *class_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子、アセンブリ内のクラスとして存在する必要があります。 名前空間で修飾された名前が、期間を使用して、クラスにある場合 (**.**) 名前空間の部分を分割する、クラス名を角かっこで区切る必要があります (**:operator[]**) または引用符 (**""**). 指定するメソッドは、クラスの静的メソッドであることが必要です。  
  
 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は CLR コードを実行できません。 作成、変更、および共通言語ランタイム モジュール; を参照するデータベース オブジェクトを削除することができます。ただし、これらの参照を実行することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効にするまで、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)です。 オプションを有効にするには、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
> [!NOTE]  
>  CLR プロシージャは、包含データベースではサポートされていません。  
  
## <a name="general-remarks"></a>全般的な解説  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ストアド プロシージャを CLR ストアド プロシージャに変更したり、その逆に変更することはできません。  
  
 ALTER PROCEDURE では権限は変更されず、従属ストアド プロシージャまたはトリガーに影響することはありませんが、 QUOTED_IDENTIFIER と ANSI_NULLS の現在のセッション設定は、変更時にストアド プロシージャに取り込まれます。 ストアド プロシージャの最初の作成時に有効であった設定と変更後の設定が異なる場合、ストアド プロシージャの動作が変わる可能性があります。  
  
 以前のプロシージャ定義が WITH ENCRYPTION または WITH RECOMPILE を使用して作成されている場合、これらのオプションは、ALTER PROCEDURE に指定されるときだけ有効になります。  
  
 ストアド プロシージャの詳細については、次を参照してください。 [CREATE PROCEDURE & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-procedure-transact-sql.md).  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**ALTER**プロシージャに対する権限のメンバーシップが必要か、 **db_ddladmin**固定データベース ロール。  
  
## <a name="examples"></a>使用例  
 次の例では、`uspVendorAllInfo` ストアド プロシージャを作成します。 この手順が供給するすべてのベンダーの名前を返します[!INCLUDE[ssSampleDBCoFull](../../includes/sssampledbcofull-md.md)]が供給する製品、信用評価、および可用性。 このプロシージャを作成した後、別の結果セットを返すようプロシージャを変更します。  
  
```  
  
IF OBJECT_ID ( 'Purchasing.uspVendorAllInfo', 'P' ) IS NOT NULL   
    DROP PROCEDURE Purchasing.uspVendorAllInfo;  
GO  
CREATE PROCEDURE Purchasing.uspVendorAllInfo  
WITH EXECUTE AS CALLER  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS Vendor, p.Name AS 'Product name',   
      v.CreditRating AS 'Rating',   
      v.ActiveFlag AS Availability  
    FROM Purchasing.Vendor v   
    INNER JOIN Purchasing.ProductVendor pv  
      ON v.BusinessEntityID = pv.BusinessEntityID   
    INNER JOIN Production.Product p  
      ON pv.ProductID = p.ProductID   
    ORDER BY v.Name ASC;  
GO  
  
```  
  
 次の例では、`uspVendorAllInfo` ストアド プロシージャを変更します。 EXECUTE AS CALLER 句を削除し、指定した製品を供給するベンダーだけを返すようにプロシージャの本体を変更します。 ここでは、 `LEFT` 関数および `CASE` 関数を使用して、結果セットの表示をカスタマイズします。  
  
```  
USE AdventureWorks2012;  
GO  
ALTER PROCEDURE Purchasing.uspVendorAllInfo  
    @Product varchar(25)   
AS  
    SET NOCOUNT ON;  
    SELECT LEFT(v.Name, 25) AS Vendor, LEFT(p.Name, 25) AS 'Product name',   
    'Rating' = CASE v.CreditRating   
        WHEN 1 THEN 'Superior'  
        WHEN 2 THEN 'Excellent'  
        WHEN 3 THEN 'Above average'  
        WHEN 4 THEN 'Average'  
        WHEN 5 THEN 'Below average'  
        ELSE 'No rating'  
        END  
    , Availability = CASE v.ActiveFlag  
        WHEN 1 THEN 'Yes'  
        ELSE 'No'  
        END  
    FROM Purchasing.Vendor AS v   
    INNER JOIN Purchasing.ProductVendor AS pv  
      ON v.BusinessEntityID = pv.BusinessEntityID   
    INNER JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID   
    WHERE p.Name LIKE @Product  
    ORDER BY v.Name ASC;  
GO  
  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```   
 Vendor               Product name  Rating    Availability  
-------------------- ------------- -------   ------------  
Proseware, Inc.      LL Crankarm   Average   No  
Vision Cycles, Inc.  LL Crankarm   Superior  Yes  
(2 row(s) affected)`  
```  

## <a name="see-also"></a>参照  
 [CREATE PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/create-procedure-transact-sql.md)   
 [DROP PROCEDURE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [実行 AS (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [ストアド プロシージャ &#40;データベース エンジン&#41;](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [sys.procedures & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)  
  
  


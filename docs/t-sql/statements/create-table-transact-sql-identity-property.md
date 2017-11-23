---
title: "IDENTITY (プロパティ) (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- IDENTITY_TSQL
- IDENTITY
dev_langs: TSQL
helpviewer_keywords:
- IDENTITY property
- columns [SQL Server], creating
- identity columns [SQL Server], IDENTITY property
- autonumbers, identity numbers
ms.assetid: 8429134f-c821-4033-a07c-f782a48d501c
caps.latest.revision: "27"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.openlocfilehash: c8ed5f2b2dd8daaf244f9e12ea17a69ff489ae3b
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="create-table-transact-sql-identity-property"></a>テーブル (TRANSACT-SQL) IDENTITY (プロパティ) を作成します。
[!INCLUDE[tsql-appliesto-ss2008-asdb-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-asdw-xxx-md.md)]

  テーブルに ID 列を作成します。 このプロパティは、CREATE TABLE および ALTER TABLE で使用[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。  
  
> [!NOTE]  
>  IDENTITY プロパティは、SQL-DMO を異なる**Identity**列の行 id プロパティを公開するプロパティです。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
IDENTITY [ (seed , increment) ]  
```  
  
## <a name="arguments"></a>引数  
 *シード*  
 テーブルに読み込まれる最初の行に使用される値です。  
  
 *増分値*  
 既に読み込まれている前の行の ID 値に加算される増分の値です。  
  
 seed と increment の両方を指定するか、またはどちらも指定しないでください。 どちらも指定しないときの既定値は (1,1) です。  
  
## <a name="remarks"></a>解説  
 ID 列はキー値の生成に使用できます。 列の ID プロパティでは、次の点が保証されます。  
  
-   新しい値はそれぞれ、現在のシードと増分値に基づいて生成されます。  
  
-   特定のトランザクションの新しい各値は、テーブルの他の同時実行トランザクションとは異なります。  
  
 列の ID プロパティでは、次の点は保証されません。  
  
-   **値の一意性**– を使用して、一意性を強制する必要があります、**主キー**または**UNIQUE**制約または**UNIQUE**インデックス。  
  
-   **トランザクション内での連続した値**– 複数の行を挿入するトランザクションが、テーブルに対するその他の同時実行の挿入が発生する可能性があるために、行の連続する値を取得する保証はありません。 値が連続している必要があるかどうか、トランザクションが、テーブルで排他ロックを使用してまたはを使用して、 **SERIALIZABLE**分離レベル。  
  
-   **サーバーの再起動またはその他の失敗後の連続した値**–[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]パフォーマンス上の理由から id 値をキャッシュする場合があり、割り当てられた値の一部が失われるデータベースの障害やサーバーの再起動中にします。 その結果、挿入時に非連続的な ID 値が生成される場合があります。 非連続的な値が許可されない場合、アプリケーションは独自のメカニズムを使用してキー値を生成する必要があります。 シーケンス ジェネレーターを使用して、 **NOCACHE**オプションは、トランザクションがコミットされないにギャップを制限できます。  
  
-   **値の再利用**– 特定のシードと増分値は、エンジンによって再利用されません id を持つ特定の id プロパティ。 特定の挿入ステートメントが失敗した場合または挿入ステートメントがロールバックされた場合、使用した ID 値は失われ、再度生成されることはありません。 その結果、それ以降の ID 値が生成されると、連続しない場合があります。  
  
 これらの制限事項が仕様に含まれているのは、パフォーマンスを向上するため、および多くの一般的な状況で許容されるためです。 これらの制限事項が原因で ID 値を使用できない場合は、アプリケーションを使用して、現在の値を保持する別のテーブルを作成し、テーブルと番号の割り当てへのアクセスを管理します。  
  
 ID 列を持つテーブルがレプリケーション用にパブリッシュされている場合、使用されているレプリケーションの種類に適した方法で、ID 列を管理する必要があります。 詳細については、「[Replicate Identity Columns](../../relational-databases/replication/publish/replicate-identity-columns.md)」 (ID 列のレプリケート) を参照してください。  
  
 ID 列は 1 つのテーブルにつき 1 つだけ作成できます。  
  
 メモリ最適化テーブルで、シードと増分値を 1, 1 に設定する必要があります。 シード値または増分を次のエラー結果が 1 以外の値に設定します。、シードと増分の値を使用するその他のよりも、1 は、メモリ最適化テーブルでサポートされていません。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-the-identity-property-with-create-table"></a>A. CREATE TABLE で IDENTITY プロパティを使用する  
 次の例では、ID 番号を自動的に増分するテーブルを、`IDENTITY` プロパティを使用して新規作成します。  
  
```  
USE AdventureWorks2012;  
  
IF OBJECT_ID ('dbo.new_employees', 'U') IS NOT NULL  
   DROP TABLE new_employees;  
GO  
CREATE TABLE new_employees  
(  
 id_num int IDENTITY(1,1),  
 fname varchar (20),  
 minit char(1),  
 lname varchar(30)  
);  
  
INSERT new_employees  
   (fname, minit, lname)  
VALUES  
   ('Karin', 'F', 'Josephs');  
  
INSERT new_employees  
   (fname, minit, lname)  
VALUES  
   ('Pirkko', 'O', 'Koskitalo');  
```  
  
### <a name="b-using-generic-syntax-for-finding-gaps-in-identity-values"></a>B. ID 値のギャップを検索する汎用構文を使用する  
 次の例では、データが削除された場合に ID 値のギャップを検索する汎用構文を示します。  
  
> [!NOTE]  
>  次の最初の部分[!INCLUDE[tsql](../../includes/tsql-md.md)]スクリプトは、例示のみを目的に設計されています。 実行できるのは、"`-- Create the img table`" というコメントで始まる [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトです。  
  
```  
-- Here is the generic syntax for finding identity value gaps in data.  
-- The illustrative example starts here.  
SET IDENTITY_INSERT tablename ON;  
DECLARE @minidentval column_type;  
DECLARE @maxidentval column_type;  
DECLARE @nextidentval column_type;  
SELECT @minidentval = MIN($IDENTITY), @maxidentval = MAX($IDENTITY)  
    FROM tablename  
IF @minidentval = IDENT_SEED('tablename')  
   SELECT @nextidentval = MIN($IDENTITY) + IDENT_INCR('tablename')  
   FROM tablename t1  
   WHERE $IDENTITY BETWEEN IDENT_SEED('tablename') AND   
      @maxidentval AND  
      NOT EXISTS (SELECT * FROM tablename t2  
         WHERE t2.$IDENTITY = t1.$IDENTITY +   
            IDENT_INCR('tablename'))  
ELSE  
   SELECT @nextidentval = IDENT_SEED('tablename');  
SET IDENTITY_INSERT tablename OFF;  
-- Here is an example to find gaps in the actual data.  
-- The table is called img and has two columns: the first column   
-- called id_num, which is an increasing identification number, and the   
-- second column called company_name.  
-- This is the end of the illustration example.  
  
-- Create the img table.  
-- If the img table already exists, drop it.  
-- Create the img table.  
IF OBJECT_ID ('dbo.img', 'U') IS NOT NULL  
   DROP TABLE img;  
GO  
CREATE TABLE img (id_num int IDENTITY(1,1), company_name sysname);  
INSERT img(company_name) VALUES ('New Moon Books');  
INSERT img(company_name) VALUES ('Lucerne Publishing');  
-- SET IDENTITY_INSERT ON and use in img table.  
SET IDENTITY_INSERT img ON;  
  
DECLARE @minidentval smallint;  
DECLARE @nextidentval smallint;  
SELECT @minidentval = MIN($IDENTITY) FROM img  
 IF @minidentval = IDENT_SEED('img')  
    SELECT @nextidentval = MIN($IDENTITY) + IDENT_INCR('img')  
    FROM img t1  
    WHERE $IDENTITY BETWEEN IDENT_SEED('img') AND 32766 AND  
      NOT    EXISTS (SELECT * FROM img t2  
          WHERE t2.$IDENTITY = t1.$IDENTITY + IDENT_INCR('img'))  
 ELSE  
    SELECT @nextidentval = IDENT_SEED('img');  
SET IDENTITY_INSERT img OFF;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DBCC CHECKIDENT &#40;Transact-SQL&#41;](../../t-sql/database-console-commands/dbcc-checkident-transact-sql.md)   
 [IDENT_INCR &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ident-incr-transact-sql.md)   
 [@@IDENTITY &#40;Transact-SQL&#41;](../../t-sql/functions/identity-transact-sql.md)   
 [ID および #40 です。関数と #41 です。&#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/identity-function-transact-sql.md)   
 [IDENT_SEED &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/ident-seed-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET IDENTITY_INSERT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-identity-insert-transact-sql.md)   
 [ID 列のレプリケート](../../relational-databases/replication/publish/replicate-identity-columns.md)  
  
  

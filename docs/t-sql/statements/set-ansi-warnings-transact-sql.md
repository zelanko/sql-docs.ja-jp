---
title: "[SET ANSI_WARNINGS] (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/02/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- SET ANSI_WARNINGS
- ANSI_WARNINGS_TSQL
- ANSI_WARNINGS
- SET_ANSI_WARNINGS_TSQL
dev_langs: TSQL
helpviewer_keywords:
- errors [SQL Server], ISO standard behavior
- warnings [SQL Server]
- SET ANSI_WARNINGS statement
- ANSI_WARNINGS option
ms.assetid: f82aaab0-334f-427b-89b0-de4af596b4fa
caps.latest.revision: "33"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: b0c584a6573e9b5ddc5b306a31fe7dada2100f72
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-ansiwarnings-transact-sql"></a>SET ANSI_WARNINGS (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  複数のエラー条件に対して ISO 標準の動作をすることを指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server and Azure SQL Database  
  
SET ANSI_WARNINGS { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_WARNINGS ON;  
```  
  
## <a name="remarks"></a>解説  
 SET ANSI_WARNINGS は、次の条件に影響します。  
  
-   ON に設定した場合、SUM、AVG、MAX、MIN、STDEV、STDEVP、VAR、VARP、COUNT などの集計関数に NULL 値が含まれていると、警告メッセージが生成されます。 OFF の場合、警告メッセージは生成されません。  
  
-   ON に設定した場合、0 除算や演算オーバーフロー エラーが発生すると、ステートメントはロールバックされエラー メッセージが生成されます。 OFF に設定した場合、0 除算や演算オーバーフロー エラーが発生すると、NULL 値が返されます。 0 除算や演算オーバーフロー エラーが原因となって null 値が返されますが、INSERT または UPDATE が試行されて、**文字**、Unicode、または**バイナリ**の列の長さ新しい値が列の最大サイズを超えています。 SET ANSI_WARNINGS が ON の場合、INSERT または UPDATE は ISO 標準の指定に従って取り消されます。 文字型の列の末尾の空白文字とバイナリ列の末尾の NULL 値は無視されます。 OFF の場合、データは列のサイズに切り捨てられ、ステートメントは成功します。  
  
    > [!NOTE]  
    >  切り捨てが発生すると、変換にまたはからに**バイナリ**または**varbinary**オプションの設定に関係なく、データ、警告やエラーを発行します。  
  
    > [!NOTE]  
    >  ストアド プロシージャでパラメーターを引き渡す場合や、バッチ ステートメントで変数を宣言または設定する場合、またはユーザー定義関数においては、ANSI_WARNINGS は無視されます。 たとえば、として変数が定義されている**char (3)**とし、次の 3 つの文字を超える値に設定、データは切り捨てに定義されているサイズと、INSERT または UPDATE ステートメントは成功します。  
  
 sp_configure の user options オプションを使用すると、ANSI_WARNINGS の既定の設定をサーバーに対するすべての接続に適用できます。 詳細については、このトピックの「 [sp_configure &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)のバックアップと復元で使用する基本的なバックアップ メディア用語を紹介します。  
  
 計算列やインデックス付きビューのインデックスを作成または操作するときには、SET ANSI_WARNINGS を ON に設定する必要があります。 SET ANSI_WARNINGS が OFF の場合、計算列にインデックスが設定されているテーブルやインデックス付きビューに対して CREATE、UPDATE、INSERT、または DELETE ステートメントを実行すると失敗します。 計算列でインデックス付きビューとインデックスを持つ必要な SET オプション設定に関する詳細についてを参照してください「の考慮事項とする SET ステートメントの使用」 [SET ステートメント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statements-transact-sql.md).  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、ANSI_WARNINGS データベース オプションが用意されています。 これは、SET ANSI_WARNINGS と同じです。 SET ANSI_WARNINGS が ON の場合、0 除算やデータベースの列のサイズを超える文字列、または同様のエラーが発生すると、エラーまたは警告が発生します。 SET ANSI_WARNINGS が OFF の場合、これらのエラーや警告は発生しません。 model データベースでは、SET ANSI_WARNINGS の既定の設定は OFF です。 指定しない場合は、ANSI_WARNINGS の設定が適用されます。 SET ANSI_WARNINGS を OFF 場合、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] is_ansi_warnings_on 列の値を使用して、 [sys.databases](../../relational-databases/system-catalog-views/sys-databases-transact-sql.md)カタログ ビューです。  
  
 分散クエリを実行する場合は、ANSI_WARNINGS を ON に設定してください。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]接続するときに自動的に ON に ANSI_WARNINGS を設定します。 この構成は、ODBC データ ソースまたは ODBC 接続属性で定義され、接続前にアプリケーションで設定できます。 DB-Library アプリケーションからの接続に対しては、既定では SET ANSI_WARNINGS は OFF に設定されています。  
  
 SET ANSI_DEFAULTS が ON の場合は、SET ANSI_WARNINGS は有効になります。  
  
 SET ANSI_WARNINGS は、解析時ではなく実行時に設定されます。  
  
 SET ARITHABORT または SET ARITHIGNORE のいずれか OFF、SET ANSI_WARNINGS が ON、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 0 除算やオーバーフロー エラーが発生した場合もエラー メッセージが返されます。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @ANSI_WARN VARCHAR(3) = 'OFF';  
IF ( (8 & @@OPTIONS) = 8 ) SET @ANSI_WARN = 'ON';  
SELECT @ANSI_WARN AS ANSI_WARNINGS;  
```  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、SET ANSI_WARNINGS が ON の場合と OFF の場合に分けて、上の 3 つの状況を示しています。  
  
```  
USE AdventureWorks2012;  
GO  
  
CREATE TABLE T1   
(  
   a int,   
   b int NULL,   
   c varchar(20)  
);  
GO  
  
SET NOCOUNT ON;  
  
INSERT INTO T1   
VALUES (1, NULL, '')   
      ,(1, 0, '')  
      ,(2, 1, '')  
      ,(2, 2, '');  
  
SET NOCOUNT OFF;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS ON';  
GO  
  
SET ANSI_WARNINGS ON;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (3, 3, 'Text string longer than 20 characters');  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
PRINT '**** Setting ANSI_WARNINGS OFF';  
GO  
SET ANSI_WARNINGS OFF;  
GO  
  
PRINT 'Testing NULL in aggregate';  
GO  
SELECT a, SUM(b)   
FROM T1   
GROUP BY a;  
GO  
  
PRINT 'Testing String Overflow in INSERT';  
GO  
INSERT INTO T1   
VALUES (4, 4, 'Text string longer than 20 characters');  
GO  
SELECT a, b, c   
FROM T1  
WHERE a = 4;  
GO  
  
PRINT 'Testing Divide by zero';  
GO  
SELECT a / b AS ab   
FROM T1;  
GO  
  
DROP TABLE T1  
```  
  
## <a name="see-also"></a>参照  
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [SELECT &#40;Transact-SQL&#41;](../../t-sql/queries/select-transact-sql.md)   
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [[SET ansi_defaults] &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md)   
 [SESSIONPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/sessionproperty-transact-sql.md)  
  
  

---
title: "SET ANSI_PADDING (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: sql-data-warehouse, pdw, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ANSI_PADDING_TSQL
- ANSI_PADDING
- SET_ANSI_PADDING_TSQL
- SET ANSI_PADDING
dev_langs: TSQL
helpviewer_keywords:
- data types [SQL Server], short values
- ANSI_PADDING option
- short values [SQL Server]
- SET ANSI_PADDING statement
- trailing blanks
ms.assetid: 92bd29a3-9beb-410e-b7e0-7bc1dc1ae6d0
caps.latest.revision: "47"
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: d73104a4e49c81fd153bd70b4b223aba5d86c407
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="set-ansipadding-transact-sql"></a>SET ANSI_PADDING (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-pdw-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-pdw-md.md)]

  列に定義されているサイズよりも短い値を列に格納する方法と、値の後に **char**、 **varchar**、 **binary**、 **varbinary** データ型で空白が続いている値を列に格納する方法を指定します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server  
  
SET ANSI_PADDING { ON | OFF }  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  
  
SET ANSI_PADDING ON;  
```  
  
## <a name="remarks"></a>解説  
 定義された列**char**、 **varchar**、**バイナリ**、および**varbinary**データ型が、定義されたサイズに設定します。  
  
 この設定は新しい列の定義にだけ影響します。 列が作成された後は、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では列の作成時の設定に基づいて値が格納されます。 この設定を後で変更しても、既存の列には影響がありません。  
  
> [!NOTE]  
>  常に ANSI_PADDING を ON に設定することをお勧めします。  
  
 値が列に挿入されると、次の表は、SET ANSI_PADDING の設定の効果を示します**char**、 **varchar**、**バイナリ**、および**varbinary**データ型。  
  
|設定|char (*n*) NOT NULL または binary (*n*) NOT NULL|char (*n*) NULL または binary (*n*) NULL|varchar (*n*) または varbinary (*n*)|  
|-------------|----------------------------------------------------|--------------------------------------------|----------------------------------------|  
|ON|元の値を埋め込む (空白で**char**列と末尾の 0 の**バイナリ**列)、列の長さにします。|場合と同じ規則に従います**char (***n***)**または**バイナリ (**  *n* **)** SET ANSI_PADDING が ON の場合は NOT NULL します。|挿入された文字値の後続の空白**varchar**列は切り捨てられません。 挿入されたバイナリ値の後続の 0 **varbinary**列は切り捨てられません。 列の長さに合わせるためにパディングされることはありません。|  
|OFF|元の値を埋め込む (空白で**char**列と末尾の 0 の**バイナリ**列)、列の長さにします。|場合と同じ規則に従います**varchar**または**varbinary** SET ANSI_PADDING が OFF の場合。|挿入された文字値の後続の空白、 **varchar**列は切り捨てられます。 挿入されたバイナリ値の後続の 0、 **varbinary**列は切り捨てられます。|  
  
> [!NOTE]  
>  埋められる場合は、 **char**列は空白で埋められますと**バイナリ**列が 0 で埋められます。 切り捨てられる場合、 **char**列がある末尾の空白をトリミング、および**バイナリ**列がある末尾の 0 が切り捨てられます。  
  
 計算列やインデックス付きビューのインデックスを作成または変更するときには、SET ANSI_PADDING を ON に設定する必要があります。 計算列でインデックス付きビューとインデックスを持つ必要な SET オプション設定に関する詳細についてを参照してください「の考慮事項とする SET ステートメントの使用」 [SET ステートメント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-statements-transact-sql.md).  
  
 既定では、SET ANSI_PADDING は ON に設定されています。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Native Client ODBC ドライバーと[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Native Client OLE DB Provider for[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を ON に接続するときに ANSI_PADDING を自動的に設定します。 この構成は、ODBC データ ソースまたは ODBC 接続属性で定義でき、接続前にアプリケーションで設定される OLE DB 接続プロパティでも定義できます。 DB-Library アプリケーションからの接続に対しては、既定では SET ANSI_PADDING は OFF に設定されています。  
  
 SET ANSI_PADDING の設定には影響しません、 **nchar**、 **nvarchar**、 **ntext**、**テキスト**、**イメージ**、 **varbinary (max)**、 **varchar (max)**、および**nvarchar (max)**データ型。 これらの値では、常に SET ANSI_PADDING ON の動作が示されます。 つまり、末尾の空白と 0 は切り捨てられません。  
  
 SET ANSI_DEFAULTS が ON の場合は、SET ANSI_PADDING が有効になります。  
  
 SET ANSI_PADDING は、解析時ではなく実行時に設定されます。  
  
 この設定の現在の設定を表示するには、次のクエリを実行します。  
  
```  
DECLARE @ANSI_PADDING VARCHAR(3) = 'OFF';  
IF ( (16 & @@OPTIONS) = 16 ) SET @ANSI_PADDING = 'ON';  
SELECT @ANSI_PADDING AS ANSI_PADDING;  
  
```  
  
## <a name="permissions"></a>Permissions  
 public ロールのメンバーシップが必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、この設定が各データ型にどのように影響するかを示しています。  
  
```  
PRINT 'Testing with ANSI_PADDING ON'  
SET ANSI_PADDING ON;  
GO  
  
CREATE TABLE t1 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t1 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t1 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '\<',  
   varbinarycol  
FROM t1;  
GO  
  
PRINT 'Testing with ANSI_PADDING OFF';  
SET ANSI_PADDING OFF;  
GO  
  
CREATE TABLE t2 (  
   charcol CHAR(16) NULL,   
   varcharcol VARCHAR(16) NULL,   
   varbinarycol VARBINARY(8)  
);  
GO  
INSERT INTO t2 VALUES ('No blanks', 'No blanks', 0x00ee);  
INSERT INTO t2 VALUES ('Trailing blank ', 'Trailing blank ', 0x00ee00);  
  
SELECT 'CHAR' = '>' + charcol + '\<', 'VARCHAR'='>' + varcharcol + '<',  
   varbinarycol  
FROM t2;  
GO  
  
DROP TABLE t1;  
DROP TABLE t2;  
```  
  
## <a name="see-also"></a>参照  
 [SET ステートメント &#40;Transact-SQL&#41;](../../t-sql/statements/set-statements-transact-sql.md)   
 [SESSIONPROPERTY &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/sessionproperty-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [INSERT &#40;Transact-SQL&#41;](../../t-sql/statements/insert-transact-sql.md)   
 [[SET ansi_defaults] &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-ansi-defaults-transact-sql.md)  
  
  

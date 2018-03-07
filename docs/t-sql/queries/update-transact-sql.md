---
title: "更新 (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|queries
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- UPDATE_TSQL
- UPDATE
dev_langs:
- TSQL
helpviewer_keywords:
- DML [SQL Server], UPDATE statement
- data updates [SQL Server], UPDATE statement
- updating data [SQL Server]
- TOP clause, UPDATE
- OUTPUT clause
- large value data types
- data manipulation language [SQL Server], UPDATE statement
- user-defined types [SQL Server], modifying
- INSTEAD OF triggers
- modifying data [SQL Server], UPDATE statement
- data modifications [SQL Server], UPDATE statement
- large data, modifying
- .WRITE clause
- table modifications [SQL Server], UPDATE statement
- UDTs [SQL Server], modifying
- UPDATE statement [SQL Server], about UPDATE statement
- LOB data [SQL Server], modifying
- modifying LOB data
- UPDATE statement [SQL Server]
- FROM clause, UPDATE statement
- WHERE clause, UPDATE statement
ms.assetid: 40e63302-0c68-4593-af3e-6d190181fee7
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Active
ms.openlocfilehash: 227cafdd68eddac2ff6a515853f0fcded0c07f63
ms.sourcegitcommit: 9e6a029456f4a8daddb396bc45d7874a43a47b45
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/25/2018
---
# <a name="update-transact-sql"></a>UPDATE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  既存のデータ テーブルまたはビューを変更[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。 例については、次を参照してください。[例](#UpdateExamples)です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
-- Syntax for SQL Server and Azure SQL Database  

[ WITH <common_table_expression> [...n] ]  
UPDATE   
    [ TOP ( expression ) [ PERCENT ] ]   
    { { table_alias | <object> | rowset_function_limited   
         [ WITH ( <Table_Hint_Limited> [ ...n ] ) ]  
      }  
      | @table_variable      
    }  
    SET  
        { column_name = { expression | DEFAULT | NULL }  
          | { udt_column_name.{ { property_name = expression  
                                | field_name = expression }  
                                | method_name ( argument [ ,...n ] )  
                              }  
          }  
          | column_name { .WRITE ( expression , @Offset , @Length ) }  
          | @variable = expression  
          | @variable = column = expression  
          | column_name { += | -= | *= | /= | %= | &= | ^= | |= } expression  
          | @variable { += | -= | *= | /= | %= | &= | ^= | |= } expression  
          | @variable = column { += | -= | *= | /= | %= | &= | ^= | |= } expression  
        } [ ,...n ]   
  
    [ <OUTPUT Clause> ]  
    [ FROM{ <table_source> } [ ,...n ] ]   
    [ WHERE { <search_condition>   
            | { [ CURRENT OF   
                  { { [ GLOBAL ] cursor_name }   
                      | cursor_variable_name   
                  }   
                ]  
              }  
            }   
    ]   
    [ OPTION ( <query_hint> [ ,...n ] ) ]  
[ ; ]  
  
<object> ::=  
{   
    [ server_name . database_name . schema_name .   
    | database_name .[ schema_name ] .   
    | schema_name .  
    ]  
    table_or_view_name}  
```  
  
```  
-- Syntax for Azure SQL Data Warehouse and Parallel Data Warehouse  

UPDATE [ database_name . [ schema_name ] . | schema_name . ] table_name   
SET { column_name = { expression | NULL } } [ ,...n ]  
[ FROM from_clause ]  
[ WHERE <search_condition> ]   
[ OPTION ( LABEL = label_name ) ]  
[;]  
```  
  
## <a name="arguments"></a>引数  
 WITH \<common_table_expression>  
 UPDATE ステートメントのスコープ内で定義された、一時的な名前付き結果セットまたはビュー (共通テーブル式 (CTE) とも呼ばれる) を指定します。 CTE 結果セットは単純なクエリから派生し、UPDATE ステートメントで参照されます。  
  
 共通テーブル式は、SELECT、INSERT、DELETE、CREATE VIEW の各ステートメントでも使用できます。 詳細については、次を参照してください。[で common_table_expression と #40 です。TRANSACT-SQL と #41 です](../../t-sql/queries/with-common-table-expression-transact-sql.md)。  
  
 上部**(** *式 * * *)** [PERCENT]  
 数または更新する行の割合を指定します。 *expression* は行数または行の比率 (%) にすることができます。  
  
 INSERT、UPDATE、または DELETE を使用する TOP 式で参照される行は、順序付けされません。  
  
 区切るかっこ*式*INSERT、UPDATE、および DELETE ステートメントで TOP が必要です。 詳細については、次を参照してください。 [TOP &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/top-transact-sql.md).  
  
 *table_alias*  
 FROM 句で指定される別名です。行を更新するテーブルまたはビューを表します。  
  
 *server_name*  
 サーバーの名前を指定します (リンク サーバー名を使用して、または[OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)サーバー名として機能)、テーブルまたはビューが配置されています。 場合*server_name*が指定されている*database_name*と*schema_name*が必要です。  
  
 *database_name*  
 データベースの名前です。  
  
 *schema_name*  
 テーブルまたはビューが属するスキーマの名前を指定します。  
  
 *table_or view_name*  
 行を更新するテーブルまたはビューの名前です。 によって参照されるビュー *table_or_view_name*可能にし、ビューの FROM 句内のただ 1 つのベース テーブルを参照する必要があります。 更新可能なビューの詳細については、次を参照してください。 [CREATE VIEW &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-view-transact-sql.md).  
  
 *rowset_function_limited*  
 いずれかが、 [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)または[OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)関数、プロバイダーの機能です。  
  
 WITH **(** \<Table_Hint_Limited> **)**  
 対象のテーブルに設定可能なテーブル ヒントを 1 つ以上指定します。 キーワード WITH とかっこが必要です。 NOLOCK および READUNCOMMITTED は指定できません。 テーブル ヒントの詳細については、次を参照してください。[テーブル ヒント &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/hints-transact-sql-table.md).  
  
 @*table_variable*  
 指定します、[テーブル](../../t-sql/data-types/table-transact-sql.md)変数テーブル ソースとして。  
  
 SET  
 更新する列名または変数名の一覧を指定します。  
  
 *column_name*  
 変更するデータを含む列です。 *column_name*に存在する必要があります*table_or view_name*です。 ID 列は更新できません。  
  
 *式 (expression)*  
 変数、リテラル値、式、または 1 つの値を返すかっこで囲んだサブセレクト ステートメントです。 によって返される値*式*既存の値を置き換えます*column_name*または *@variable*です。  
  
> [!NOTE]  
>  Unicode 文字データ型を参照するときに**nchar**、 **nvarchar**、および**ntext**、'expression' は、大文字の英字を付ける必要があります 'N' です。 場合 'n' が指定されていない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データベースまたは列の既定の照合順序に対応するコード ページに文字列に変換します。 文字列がこのコード ページにない場合は、失われます。  
  
 DEFAULT  
 列に格納された値を列に定義された既定値で置き換えることを指定します。 列に既定値が定義されておらず、NULL 値が許されている場合は、この句を使用して列を NULL に変更できます。  
  
 { **+=** | **-=** | **\*=** | **/=** | **%=** | **&=** | **^=** | **|=** }  
 複合代入演算子です:  
 += 加算して、割り当てる  
 -= 減算して代入  
 *= 乗算して代入  
 /= 除算して代入  
 % = 剰余して代入  
 &=                        ビットごとの AND 演算を行って代入  
 ^ = ビットごとの XOR と割り当て  
 | = ビットごとの OR と割り当て  
  
 *udt_column_name*  
 ユーザー定義型の列です。  
  
 *property_name* | *field_name*  
 ユーザー定義型のパブリック プロパティまたはパブリック データ メンバーです。  
  
 *method_name* **(** *argument* [ **,**... *n*] **)**  
 静的でないパブリック ミューテーター メソッドは、 *udt_column_name*を 1 つまたは複数の引数を受け取る。  
  
 **.**WRITE **(***expression***,***@Offset***,***@Length***)**  
 指定の値のセクション*column_name*を変更できます。 *式*置換 *@Length* 単位から *@Offset* の*column_name*です。 列だけ**varchar (max)**、 **nvarchar (max)**、または**varbinary (max)**この句で指定することができます。 *column_name* NULL にすることはできませんし、テーブル名やテーブル別名で修飾することはできません。  
  
 *式*にコピーされる値は、 *column_name*です。 *式*に評価されるかに暗黙的にキャストすることができる必要があります、 *column_name*型です。 場合*式*を NULL に設定されている *@Length* は無視され、値と*column_name*は切り捨てられます内の指定した *@Offset*.  
  
 *@Offset*値の開始点は、 *column_name*を*式*が書き込まれます。 *@Offset*0 から始まる序数位置は**bigint**、負の数値にすることはできません。 場合 *@Offset* が NULL の場合、更新操作が追加*式*、既存の最後に*column_name*値および *@Length*は無視されます。 場合@Offsetがの長さより大きい、 *column_name*値、[!INCLUDE[ssDE](../../includes/ssde-md.md)]はエラーを返します。 場合 *@Offset*  plus  *@Length* 文字までが削除最後の値の列の基になる値の末尾を超える場合、します。 場合 *@Offset*  LEN plus (*式*) が、基になるより大きいサイズを宣言するには、エラーが発生します。  
  
 *@Length*始めて、列内のセクションの長さは、  *@Offset*は置き換え*式*です。 *@Length***bigint**は負の数値にすることはできません。 場合 *@Length* が NULL の場合、更新操作からのすべてのデータを削除する *@Offset* の末尾に、 *column_name*値。  
  
 詳細については、「解説」を参照してください。  
  
 **@** *variable*  
 によって返される値に設定されている宣言された変数*式*です。  
  
 SET **@***variable* = *column* = *expression* sets the variable to the same value as the column. これは、セットと異なる **@ * * * 変数* = *列*、*列* = *式*、設定する、列の更新前の値を変数です。  
  
 \<OUTPUT_Clause>  
 更新されたデータまたはそれに基づく式を、UPDATE 操作の一部として返します。 OUTPUT 句は、リモート テーブルまたはリモート ビューを対象とした DML ステートメントではサポートされません。 詳細については、次を参照してください。 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md).  
  
 FROM \<table_source>  
 別のテーブル、ビュー、または派生テーブルのソースを使用して更新操作の基になる値を提供することを指定します。 詳細については、「[FROM &#40;Transact-SQL&#41;](../../t-sql/queries/from-transact-sql.md)」を参照してください。  
  
 更新対象のオブジェクトが FROM 句で指定されたオブジェクトと同じで、FROM 句にそのオブジェクトへの参照が 1 つしかない場合、オブジェクトの別名は指定しても指定しなくてもかまいません。 更新対象のオブジェクトが FROM 句に 2 つ以上含まれている場合、そのオブジェクトへの単独の参照でテーブルの別名を指定してはなりません。 FROM 句にあるオブジェクトへの他のすべての参照に、オブジェクトの別名を含める必要があります。  
  
 INSTEAD OF UPDATE トリガーを伴うビューは、FROM 句を伴う UPDATE の対象にはなりません。  
  
> [!NOTE]  
>  FROM 句での OPENDATASOURCE、OPENQUERY、または OPENROWSET の呼び出しは、更新の対象として使用されるこれらの関数の呼び出しとは別に評価されます。これは、両方の呼び出しに同じ引数が指定されている場合にも当てはまります。 特に、いずれか一方の呼び出しの結果に適用されるフィルター条件または結合条件は、もう一方の結果に影響しません。  
  
 WHERE  
 更新する行を制限する条件を指定します。 WHERE 句で使用される形式に基づいて、更新には 2 種類の形式があります。  
  
-   検索更新では、削除する行を識別する検索条件を指定します。  
  
-   位置指定更新では、CURRENT OF 句を使用してカーソルを指定します。 更新操作は、カーソルの現在位置で行われます。  
  
\<search_condition>  
 更新の対象となる行の条件を指定します。 検索条件を結合の基準条件にすることもできます。 検索条件に含まれる述語の数に制限はありません。 述語および検索条件の詳細については、次を参照してください。[検索条件 &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/queries/search-condition-transact-sql.md).  
  
CURRENT OF  
 指定したカーソルの現在位置で更新を行うことを指定します。  
  
 WHERE CURRENT OF 句を使用する位置指定更新では、カーソルの現在位置にある 1 行を更新します。 これは、WHERE を使用する検索更新よりも正確、 \<search_condition > 句を更新する行を限定します。 検索更新は、検索条件が特定の行を識別しない場合に複数の行を変更します。  
  
GLOBAL  
 指定する*cursor_name*はグローバル カーソルを参照します。  
  
*cursor_name*  
 フェッチが行われる、開いているカーソルの名前です。 グローバルとローカル カーソルの名前を持つ場合*cursor_name*存在、GLOBAL が指定されたそれ以外の場合、この引数はグローバル カーソルを参照、ローカル カーソルを参照します。 カーソルは、更新可能である必要があります。  
  
*cursor_variable_name*  
 カーソル変数の名前を指定します。 *cursor_variable_name*更新できるカーソルを参照する必要があります。  
  
OPTION **(** \<query_hint> [ **,**... *n* ] **)**  
 オプティマイザー ヒントを使用して、[!INCLUDE[ssDE](../../includes/ssde-md.md)]がステートメントを処理する方法をカスタマイズすることを指定します。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
## <a name="best-practices"></a>ベスト プラクティス  
 使用して、@@ROWCOUNT関数の数を返しますが、クライアント アプリケーションに行を挿入します。 詳細については、次を参照してください。 [@@ROWCOUNT &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/rowcount-transact-sql.md).  
  
 影響を受ける古い値と新しい値を示すために、UPDATE ステートメントの中で変数名を使用することは可能です。ただし、これは UPDATE ステートメントによって影響を受けるのが単一のレコードである場合のみに限定されています。 UPDATE ステートメントが各レコードの新旧の値を返す、複数のレコードに影響する場合を使用して、 [OUTPUT 句](../../t-sql/queries/output-clause-transact-sql.md)です。  
  
 FROM 句を指定して更新操作の条件を設定するときは注意が必要です。 ステートメントには、1 つだけを重視する方法は対象の各列が更新されるとするかどうか、UPDATE ステートメントでは決定的であるに使用できるように指定されていない FROM 句が含まれている場合、UPDATE ステートメントの結果は未定義です。 たとえば、次のスクリプトの UPDATE ステートメントでは、`Table1` のどちらの行も UPDATE ステートメントの FROM 句の条件を満たしています。ただし、`Table1` のどちらの行を使用して `Table2.` の行を更新するかは未定義です。  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('dbo.Table1', 'U') IS NOT NULL  
    DROP TABLE dbo.Table1;  
GO  
IF OBJECT_ID ('dbo.Table2', 'U') IS NOT NULL  
    DROP TABLE dbo.Table2;  
GO  
CREATE TABLE dbo.Table1   
    (ColA int NOT NULL, ColB decimal(10,3) NOT NULL);  
GO  
CREATE TABLE dbo.Table2   
    (ColA int PRIMARY KEY NOT NULL, ColB decimal(10,3) NOT NULL);  
GO  
INSERT INTO dbo.Table1 VALUES(1, 10.0), (1, 20.0);  
INSERT INTO dbo.Table2 VALUES(1, 0.0);  
GO  
UPDATE dbo.Table2   
SET dbo.Table2.ColB = dbo.Table2.ColB + dbo.Table1.ColB  
FROM dbo.Table2   
    INNER JOIN dbo.Table1   
    ON (dbo.Table2.ColA = dbo.Table1.ColA);  
GO  
SELECT ColA, ColB   
FROM dbo.Table2;  
```  
  
 FROM 句と WHERE CURRENT OF 句を組み合わせた場合にも同じ問題が発生します。 次の例では、`Table2` のどちらの行も `FROM` ステートメントの `UPDATE` 句の条件を満たします。 `Table2` のどちらの列を使用してテーブル `Table1` の行を更新するかは未定義です。  
  
```sql  
USE AdventureWorks2012;  
GO  
IF OBJECT_ID ('dbo.Table1', 'U') IS NOT NULL  
    DROP TABLE dbo.Table1;  
GO  
IF OBJECT_ID ('dbo.Table2', 'U') IS NOT NULL  
    DROP TABLE dbo.Table2;  
GO  
CREATE TABLE dbo.Table1  
    (c1 int PRIMARY KEY NOT NULL, c2 int NOT NULL);  
GO  
CREATE TABLE dbo.Table2  
    (d1 int PRIMARY KEY NOT NULL, d2 int NOT NULL);  
GO  
INSERT INTO dbo.Table1 VALUES (1, 10);  
INSERT INTO dbo.Table2 VALUES (1, 20), (2, 30);  
GO  
DECLARE abc CURSOR LOCAL FOR  
    SELECT c1, c2   
    FROM dbo.Table1;  
OPEN abc;  
FETCH abc;  
UPDATE dbo.Table1   
SET c2 = c2 + d2   
FROM dbo.Table2   
WHERE CURRENT OF abc;  
GO  
SELECT c1, c2 FROM dbo.Table1;  
GO  
```  
  
## <a name="compatibility-support"></a>互換性サポート  
 使用して、READUNCOMMITTED ヒントおよび NOLOCK ヒントの from 句で UPDATE または DELETE ステートメントの対象のテーブルに適用されるは、将来のバージョンで削除される予定のサポートを[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業ではこのコンテキストでのヒントの使用を避け、現在このヒントを使用しているアプリケーションは変更を検討してください。  
  
## <a name="data-types"></a>データ型  
 すべて**char**と**nchar**列が定義された長さに右側が埋め込まれます。  
  
 挿入されたデータからすべての末尾のスペースが削除された ANSI_PADDING が OFF に設定されている場合**varchar**と**nvarchar**列ではスペースのみを含む文字列。 スペースだけで構成される文字列は空の文字列に切り捨てられます。 ANSI_PADDING を ON に設定すると、後続にスペースが挿入されます。 Microsoft SQL Server ODBC ドライバーおよび OLE DB Provider for SQL Server は、接続するたびに自動的に SET ANSI_PADDING を ON にします。 これは、ODBC データ ソースで構成するか、または接続属性やプロパティで設定することができます。 詳細については、「[SET ANSI_PADDING &#40;Transact-SQL&#41;](../../t-sql/statements/set-ansi-padding-transact-sql.md)」を参照してください。  
  
### <a name="updating-text-ntext-and-image-columns"></a>text 型、ntext 型、および image 型の列を更新する  
 変更、**テキスト**、 **ntext**、または**イメージ**列を初期化します、有効なテキスト ポインターを割り当てますおよびしない限り、少なくとも 1 つのデータ ページを割り当てる列を更新しますNULL 列を更新しています。  
  
 置換または変更量が多い**テキスト**、 **ntext**、または**イメージ**データを使用して[WRITETEXT](../../t-sql/queries/writetext-transact-sql.md)または[UPDATETEXT](../../t-sql/queries/updatetext-transact-sql.md) UPDATE ステートメントの代わりにします。  
  
 UPDATE ステートメントは両方のクラスター化キーと 1 つまたは複数の更新中に複数の行を変更する可能性がある場合**テキスト**、 **ntext**、または**イメージ**列、に対する部分更新これらの列は、値の完全な置き換えとして実行されます。  
  
> [!IMPORTANT]  
>  **Ntext**、**テキスト**、および**イメージ**データ型は、将来のバージョンで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では、これらのデータ型の使用は避け、現在これらのデータ型を使用しているアプリケーションは修正するようにしてください。 代わりに、 [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)、 [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)、 [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) を使用してください。  
  
### <a name="updating-large-value-data-types"></a>大きな値のデータ型を更新する  
 使用して、 **.**書き込み (*式 * * *、** *@Offset***、***@Length*) 句の一部または全体の更新を実行する**varchar (max)**、 **nvarchar (max)**、および**varbinary (max)**データ型。 たとえば、部分的に更新、 **varchar (max)**列が削除または完全な更新は削除または列内のすべてのデータを変更する一方、列の最初の 200 文字だけを変更します。 **.**に一括ログまたは単純に、データベースの復旧モデルが設定されている場合、挿入、または新しいデータを追加する更新プログラムは最小ログ記録を作成します。 既存の値を更新するときには、最小限のログ記録は使用されません。 詳細については、「[トランザクションログ &#40;SQL Server&#41;](../../relational-databases/logs/the-transaction-log-sql-server.md)」を参照してください.  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] UPDATE ステートメントにより、これらのアクションのいずれかの完全な更新に部分的な更新に変換します。  
-   パーティション ビューまたはパーティション テーブルのキー列が変更される場合  
-   複数の行が変更され、定数以外の値に対する一意でないクラスター化インデックスのキーも更新される場合  
  
使用することはできません、 **.**NULL 列を更新するかの値を設定する書き込み句*column_name*を NULL にします。  
  
*@Offset*および *@Length* のバイト数で指定された**varbinary**と**varchar**データ型の文字、 **nvarchar**データ型。 2 バイト文字セット (DBCS) の照合順序では、適切なオフセットが計算されます。  
  
最高のパフォーマンスが得られるよう、8,040 バイトの倍数の単位でデータを挿入または更新することをお勧めします。  
  
によって、列が変更された場合、 **.**書き込み句がいずれかの列の完全な値が OUTPUT 句で参照されて前のイメージに、**を削除します * * * column_name*または後のイメージで **挿入します。 * * * column_name*、が返されます。指定された列に、テーブル変数にします。 次の R の例を参照してください。  
  
同じ機能を実現するために**.**他の文字またはバイナリ データ型と書き込みを使用して、 [STUFF &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/functions/stuff-transact-sql.md).  
  
### <a name="updating-user-defined-type-columns"></a>ユーザー定義型の列を更新する  
 ユーザー定義型の列の値を更新するには、次のいずれかの方法を使用します。  
  
-   値を指定して、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型、ユーザー定義型は、その型から暗黙的または明示的な変換をサポートしている限り、します。 次の例は、文字列からの明示的な変換によって、ユーザー定義型 `Point` の列の値を更新する方法を示します。  
  
    ```sql  
    UPDATE Cities  
    SET Location = CONVERT(Point, '12.3:46.2')  
    WHERE Name = 'Anchorage';  
    ```  
  
-   ユーザー定義型のミューテーターとしてマークされたメソッドを呼び出して更新を行います。 次の例では、`Point` 型の `SetXY` というミューテーター メソッドを呼び出します。 これにより、その型のインスタンスの状態が更新されます。  
  
    ```sql  
    UPDATE Cities  
    SET Location.SetXY(23.5, 23.5)  
    WHERE Name = 'Anchorage';  
    ```  
  
    > [!NOTE]  
    >  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ミューテーター メソッドで呼び出される場合はエラーを返します、 [!INCLUDE[tsql](../../includes/tsql-md.md)] null 値、またはによって生成された新しい値の場合はミューテーター メソッドは null です。  
  
-   ユーザー定義型の登録済みプロパティまたはパブリック データ メンバーの値を変更します。 値を指定する式は、プロパティの型に暗黙的に変換できる必要があります。 次の例では、ユーザー定義型 `X` のプロパティ `Point` の値を変更します。  
  
    ```sql  
    UPDATE Cities  
    SET Location.X = 23.5  
    WHERE Name = 'Anchorage';  
    ```  
  
     同一のユーザー定義型の列のプロパティを複数変更するには、複数の UPDATE ステートメントを実行するか、その型のミューテーター メソッドを呼び出します。  
  
### <a name="updating-filestream-data"></a>FILESTREAM データを更新する  
 UPDATE ステートメントを使用すると、FILESTREAM フィールドを NULL 値、空の値、または比較的少量のインライン データに更新できます。 ただし、大量のデータは、Win32 インターフェイスを使用して、ファイルにストリーミング効率的です。 FILESTREAM フィールドを更新すると、その基となるファイル システムの BLOB データが変更されます。 FILESTREAM フィールドを NULL に設定すると、フィールドに関連付けられている BLOB データが削除されます。 次のように使用できません。WRITE() は、FILESTREAM データへの部分更新を実行します。 詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)」をご覧ください。  
  
## <a name="error-handling"></a>エラー処理  
 行の更新が制約やルールに違反する場合、列の NULL 値の設定に違反する場合、または新しい値が互換性のないデータ型の場合には、ステートメントは取り消され、エラーが返されます。レコードは更新されません。  
  
 式の評価時に UPDATE ステートメントが算術エラー (オーバーフロー、0 による除算、ドメイン エラー) を検出した場合、更新は行われません。 バッチの残りの部分は実行されず、エラー メッセージが返されます。  
  
 クラスター化インデックスに関係する列を更新した結果、クラスター化インデックスと行のサイズが 8,060 バイトを超える場合、更新は失敗し、エラー メッセージが返されます。  
  
## <a name="interoperability"></a>相互運用性  
 UPDATE ステートメントをユーザー定義関数の本文で使用できるのは、変更対象のテーブルがテーブル変数の場合だけです。  
  
 INSTEAD OF トリガーが、テーブルに対する UPDATE 操作で定義されている場合は、UPDATE ステートメントの代わりにそのトリガーが実行されます。 以前のバージョンの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、UPDATE およびその他のデータ変更ステートメントでサポートされているのは AFTER トリガーのみです。 FROM 句は、INSTEAD OF トリガーが定義されているビューを直接または間接的に参照する UPDATE ステートメントでは指定できません。 INSTEAD of トリガーの詳細については、次を参照してください。 [CREATE TRIGGER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-trigger-transact-sql.md).  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 、直接的または間接的に定義された INSTEAD OF トリガーが設定されているビューを参照する UPDATE ステートメントの FROM 句を指定することはできません。 INSTEAD of トリガーの詳細については、次を参照してください。 [CREATE TRIGGER &#40;です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-trigger-transact-sql.md).  
  
 共通テーブル式 (CTE) が UPDATE ステートメントの対象である場合、ステートメント内の CTE に対するすべての参照を一致させる必要があります。 たとえば、FROM 句で CTE に別名を割り当てた場合、CTE に対するすべての参照で別名を使用する必要があります。 CTE はオブジェクト ID を持たないため、CTE の参照は明確にする必要があります。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、オブジェクト ID を使用して、オブジェクトと別名の暗黙的なリレーションシップを識別します。 このリレーションシップがない場合、クエリ プランで予期しない結合動作やクエリ結果が生成される可能性があります。 次の例では、更新操作の対象オブジェクトとして CTE を指定するときの、適切な方法と不適切な方法を示します。  
  
```sql  
USE tempdb;  
GO  
-- UPDATE statement with CTE references that are correctly matched.  
DECLARE @x TABLE (ID int, Value int);  
DECLARE @y TABLE (ID int, Value int);  
INSERT @x VALUES (1, 10), (2, 20);  
INSERT @y VALUES (1, 100),(2, 200);  
  
WITH cte AS (SELECT * FROM @x)  
UPDATE x -- cte is referenced by the alias.  
SET Value = y.Value  
FROM cte AS x  -- cte is assigned an alias.  
INNER JOIN @y AS y ON y.ID = x.ID;  
SELECT * FROM @x;  
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 ID     Value  
 ------ -----  
 1      100  
 2      200  
 (2 row(s) affected)  
```  

CTE 参照を使用できませんが適合しているステートメントを更新します。  
```sql  
USE tempdb;  
GO  
DECLARE @x TABLE (ID int, Value int);  
DECLARE @y TABLE (ID int, Value int);  
INSERT @x VALUES (1, 10), (2, 20);  
INSERT @y VALUES (1, 100),(2, 200);  
  
WITH cte AS (SELECT * FROM @x)  
UPDATE cte   -- cte is not referenced by the alias.  
SET Value = y.Value  
FROM cte AS x  -- cte is assigned an alias.  
INNER JOIN @y AS y ON y.ID = x.ID;   
SELECT * FROM @x;   
GO  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
```  
ID     Value  
------ -----  
1      100  
2      100  
(2 row(s) affected)  
```  

## <a name="locking-behavior"></a>ロック動作  
 UPDATE ステートメントでは、常に、そのステートメントで変更するテーブルについて排他 (X) ロックを獲得し、トランザクションが完了するまでそのロックを保持します。 排他ロックをかけたトランザクション以外はデータを変更できません。 別のロック手法を指定することにより、UPDATE ステートメントの存続期間におけるこの既定の動作を無効にするためのテーブル ヒントを指定できます。ただし、このヒントは、経験豊富な開発者およびデータベース管理者が最後の手段としてのみ使用することを推奨します。 詳細については、「[テーブル ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-table.md)」を参照してください。  
  
## <a name="logging-behavior"></a>ログ記録の動作  
 UPDATE ステートメントがログに記録します。ただし、部分型を更新する大きな値データを使用して、 **.**句は最小ログ記録を作成します。 詳細については、前のセクション「データ型」の「大きな値のデータ型を更新する」を参照してください。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 対象のテーブルに対する UPDATE 権限が必要です。 SELECT 権限を UPDATE ステートメントに WHERE 句が含まれている場合、または場合に更新されるテーブルに必要なも*式*セット内句は、テーブルの列を使用します。  
  
 メンバーに権限は、既定の更新、 **sysadmin**固定サーバー ロール、 **db_owner**と**db_datawriter**固定データベース ロール、およびテーブル所有者です。 メンバー、 **sysadmin**、 **db_owner**、および**db_securityadmin**ロール、およびテーブル所有者は、他のユーザーに権限を譲渡できます。  
  
##  <a name="UpdateExamples"></a> 使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[基本構文](#BasicSyntax)|UPDATE|  
|[更新される行数を制限します。](#LimitingValues)|WHERE • TOP • WITH 共通テーブル式 • WHERE CURRENT OF|  
|[列値の設定](#ColumnValues)|計算値 • 複合演算子 • 既定値 • サブクエリ|  
|[標準的なテーブル以外の対象オブジェクトを指定します。](#TargetObjects)|ビュー • テーブル変数 • テーブルの別名|  
|[他のテーブルからデータに基づくデータの更新](#OtherTables)|FROM|  
|[リモート テーブル内の行を更新します。](#RemoteTables)|リンク サーバー • OPENQUERY • OPENDATASOURCE|  
|[ラージ オブジェクト データ型を更新します。](#LOBValues)|.• OPENROWSET を記述します。|  
|[ユーザー定義型を更新します。](#UDTs)|ユーザー定義型|  
|[ヒントを使用して、クエリ オプティマイザーの既定の動作を上書きする.](#TableHints)|テーブル ヒント • クエリ ヒント|  
|[UPDATE ステートメントの結果をキャプチャ](#CaptureResults)|OUTPUT 句|  
|[その他のステートメントで UPDATE を使用](#Other)|ストアド プロシージャ • TRY...CATCH|  
  
###  <a name="BasicSyntax"></a>基本構文  
 このセクションの例では、最低限必要な構文を使用して UPDATE ステートメントの基本機能を示します。  
  
#### <a name="a-using-a-simple-update-statement"></a>A. 単純な UPDATE ステートメントを使用する  
 次の例では、`Person.Address` テーブル内のすべての行を対象に単一の列を更新します。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Person.Address  
SET ModifiedDate = GETDATE();  
```  
  
#### <a name="b-updating-multiple-columns"></a>B. 複数の列を更新する  
 次の例では、`Bonus` テーブルのすべての行の `CommissionPct` 列、`SalesQuota` 列、および `SalesPerson` 列の値を更新します。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET Bonus = 6000, CommissionPct = .10, SalesQuota = NULL;  
GO  
```  
  
###  <a name="LimitingValues"></a>更新される行数を制限します。  
 このセクションの例では、UPDATE ステートメントによって影響を受ける行の数を制限する方法を示します。  
  
#### <a name="c-using-the-where-clause"></a>C. WHERE 句を使用する  
 次の例では、WHERE 句を使用して更新する行を指定します。 ステートメントの値を更新、`Color`の列、 `Production.Product` 'Red' の既存の値を持つすべての行のテーブル、`Color`列内で値を持つ、 `Name` 'road-250' で始まる列です。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.Product  
SET Color = N'Metallic Red'  
WHERE Name LIKE N'Road-250%' AND Color = N'Red';  
GO  
```  
  
#### <a name="d-using-the-top-clause"></a>D. TOP 句を使用する  
 次の例では、UPDATE ステートメントで変更される行の数を TOP 句で制限します。 ときに、TOP (*n*) UPDATE 句を使用のランダムな選択で、更新操作が実行される '*n*' 行の数。 次の例では、`VacationHours` テーブル内のランダムな 10 個の行について、`Employee` 列を 25% 増しに更新します。  
  
```sql  
USE AdventureWorks2012;
GO
UPDATE TOP (10) HumanResources.Employee
SET VacationHours = VacationHours * 1.25 ;
GO  
```  
  
 TOP を使用して、意味のある日時順に更新を適用する必要がある場合は、サブセレクト ステートメントに ORDER BY を含めて TOP を使用する必要があります。 次の例では、採用日の古い従業員上位 10 人の休暇時間を更新します。  
  
```sql  
UPDATE HumanResources.Employee  
SET VacationHours = VacationHours + 8  
FROM (SELECT TOP 10 BusinessEntityID FROM HumanResources.Employee  
     ORDER BY HireDate ASC) AS th  
WHERE HumanResources.Employee.BusinessEntityID = th.BusinessEntityID;  
GO  
```  
  
#### <a name="e-using-the-with-commontableexpression-clause"></a>E. WITH common_table_expression 句を使用する  
 次の例では、`PerAssemnblyQty` の製造に直接または間接的に使用されるすべての部品およびコンポーネントの `ProductAssemblyID 800` の値を更新します。 共通テーブル式を構築するには、直接使用される部品の階層リストを返します`ProductAssemblyID 800`と、これらのコンポーネントをビルドするために使用される部品です。 共通テーブル式が返した行のみが変更されます。  
  
```sql  
USE AdventureWorks2012;  
GO  
WITH Parts(AssemblyID, ComponentID, PerAssemblyQty, EndDate, ComponentLevel) AS  
(  
    SELECT b.ProductAssemblyID, b.ComponentID, b.PerAssemblyQty,  
        b.EndDate, 0 AS ComponentLevel  
    FROM Production.BillOfMaterials AS b  
    WHERE b.ProductAssemblyID = 800  
          AND b.EndDate IS NULL  
    UNION ALL  
    SELECT bom.ProductAssemblyID, bom.ComponentID, p.PerAssemblyQty,  
        bom.EndDate, ComponentLevel + 1  
    FROM Production.BillOfMaterials AS bom   
        INNER JOIN Parts AS p  
        ON bom.ProductAssemblyID = p.ComponentID  
        AND bom.EndDate IS NULL  
)  
UPDATE Production.BillOfMaterials  
SET PerAssemblyQty = c.PerAssemblyQty * 2  
FROM Production.BillOfMaterials AS c  
JOIN Parts AS d ON c.ProductAssemblyID = d.AssemblyID  
WHERE d.ComponentLevel = 0;  
```  
  
#### <a name="f-using-the-where-current-of-clause"></a>F. WHERE CURRENT OF 句を使用する  
 次の例では、WHERE CURRENT OF 句を使用して、カーソルが置かれている行だけを更新します。 カーソルが、結合のみに基づいてときに、`table_name`更新プログラムで指定されたステートメントを変更します。 この場合、カーソルに関連する他のテーブルには影響ありません。  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE complex_cursor CURSOR FOR  
    SELECT a.BusinessEntityID  
    FROM HumanResources.EmployeePayHistory AS a  
    WHERE RateChangeDate <>   
         (SELECT MAX(RateChangeDate)  
          FROM HumanResources.EmployeePayHistory AS b  
          WHERE a.BusinessEntityID = b.BusinessEntityID) ;  
OPEN complex_cursor;  
FETCH FROM complex_cursor;  
UPDATE HumanResources.EmployeePayHistory  
SET PayFrequency = 2   
WHERE CURRENT OF complex_cursor;  
CLOSE complex_cursor;  
DEALLOCATE complex_cursor;  
GO  
```  
  
###  <a name="ColumnValues"></a>列値の設定  
 このセクションの例では、計算値、サブクエリ、および DEFAULT 値を使用した列の更新を示します。  
  
#### <a name="g-specifying-a-computed-value"></a>G. 計算値を指定する  
 次の例では、UPDATE ステートメントに計算値を使用しています。 `ListPrice` テーブルのすべての行の `Product` 列の値を倍にします。  
  
```sql  
USE AdventureWorks2012 ;  
GO  
UPDATE Production.Product  
SET ListPrice = ListPrice * 2;  
GO  
```  
  
#### <a name="h-specifying-a-compound-operator"></a>H. 複合演算子を指定する  
 次の例は、変数を使用して`@NewPrice`を現在の価格を取得して 10 を追加することですべての赤い自転車の価格をインクリメントします。  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @NewPrice int = 10;  
UPDATE Production.Product  
SET ListPrice += @NewPrice  
WHERE Color = N'Red';  
GO  
```  
  
 次の例では、複合演算子 += を使用して、`' - tool malfunction'` が 10 ～ 12 である行を対象に、`Name` 列の既存の値にデータ `ScrapReasonID` を追加します。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.ScrapReason   
SET Name += ' - tool malfunction'  
WHERE ScrapReasonID BETWEEN 10 and 12;  
```  
  
#### <a name="i-specifying-a-subquery-in-the-set-clause"></a>I. SET 句でサブクエリを指定する  
 次の例では、SET 句にサブクエリを使用して、列の更新に使用する値を決定します。 サブクエリからは、スカラー値 (つまり、1 行につき単一の値) のみが返されます。 この例では、`SalesYTD` テーブルの最新の売上高を反映するように `SalesPerson` テーブルの `SalesOrderHeader` 列を変更します。 サブクエリにより、`UPDATE` ステートメントで各販売員の売上高が集計されます。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET SalesYTD = SalesYTD +   
    (SELECT SUM(so.SubTotal)   
     FROM Sales.SalesOrderHeader AS so  
     WHERE so.OrderDate = (SELECT MAX(OrderDate)  
                           FROM Sales.SalesOrderHeader AS so2  
                           WHERE so2.SalesPersonID = so.SalesPersonID)  
     AND Sales.SalesPerson.BusinessEntityID = so.SalesPersonID  
     GROUP BY so.SalesPersonID);  
GO  
```  
  
#### <a name="j-updating-rows-using-default-values"></a>J. DEFAULT 値を使用して行を更新する  
 次の例では、`CostRate` の値が `CostRate` より大きいすべての行を対象に、`20.00` 列をその既定値 (0.00) に設定します。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.Location  
SET CostRate = DEFAULT  
WHERE CostRate > 20.00;  
```  
  
###  <a name="TargetObjects"></a>標準的なテーブル以外の対象オブジェクトを指定します。  
 このセクションの例では、ビュー、テーブルの別名、またはテーブル変数を指定して行を更新する方法を示します。  
  
#### <a name="k-specifying-a-view-as-the-target-object"></a>K. ビューを対象オブジェクトとして指定する  
 次の例では、対象オブジェクトとしてビューを指定し、テーブルの行を更新します。 ビュー定義では複数のテーブルが参照されますが、UPDATE ステートメントで参照されるのは、基になるいずれかのテーブルの列だけであるため、ステートメントは正常に実行されます。 仮に両方のテーブルの列が指定された場合、UPDATE ステートメントは失敗します。 詳細については、次を参照してください。[変更データ ビューを経由した](../../relational-databases/views/modify-data-through-a-view.md)です。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Person.vStateProvinceCountryRegion  
SET CountryRegionName = 'United States of America'  
WHERE CountryRegionName = 'United States';  
```  
  
#### <a name="l-specifying-a-table-alias-as-the-target-object"></a>L. テーブルの別名を対象オブジェクトとして指定する  
 次の例では、テーブル `Production.ScrapReason` の行を更新します。 割り当てられているテーブルの別名`ScrapReason`from 句を UPDATE 句の対象オブジェクトとして指定します。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE sr  
SET sr.Name += ' - tool malfunction'  
FROM Production.ScrapReason AS sr  
JOIN Production.WorkOrder AS wo   
     ON sr.ScrapReasonID = wo.ScrapReasonID  
     AND wo.ScrappedQty > 300;  
```  
  
#### <a name="m-specifying-a-table-variable-as-the-target-object"></a>M. テーブル変数を対象オブジェクトとして指定する  
 次の例では、テーブル変数内の行を更新します。  
  
```sql  
USE AdventureWorks2012;  
GO  
-- Create the table variable.  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    NewVacationHours int,  
    ModifiedDate datetime);  
  
-- Populate the table variable with employee ID values from HumanResources.Employee.  
INSERT INTO @MyTableVar (EmpID)  
    SELECT BusinessEntityID FROM HumanResources.Employee;  
  
-- Update columns in the table variable.  
UPDATE @MyTableVar  
SET NewVacationHours = e.VacationHours + 20,  
    ModifiedDate = GETDATE()  
FROM HumanResources.Employee AS e   
WHERE e.BusinessEntityID = EmpID;  
  
-- Display the results of the UPDATE statement.  
SELECT EmpID, NewVacationHours, ModifiedDate FROM @MyTableVar  
ORDER BY EmpID;  
GO  
```  
  
###  <a name="OtherTables"></a>他のテーブルからデータに基づくデータの更新  
 このセクションの例では、テーブルの行を別のテーブルの情報に基づいて更新する方法を示します。  
  
#### <a name="n-using-the-update-statement-with-information-from-another-table"></a>N. 別のテーブルの情報を使用して UPDATE ステートメントを実行する  
 次の例を変更、`SalesYTD`内の列、`SalesPerson`テーブルに記録された最新の売り上げ高を反映するように、`SalesOrderHeader`テーブル。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET SalesYTD = SalesYTD + SubTotal  
FROM Sales.SalesPerson AS sp  
JOIN Sales.SalesOrderHeader AS so  
    ON sp.BusinessEntityID = so.SalesPersonID  
    AND so.OrderDate = (SELECT MAX(OrderDate)  
                        FROM Sales.SalesOrderHeader  
                        WHERE SalesPersonID = sp.BusinessEntityID);  
GO  
```  
  
 前の例では、特定の日付の指定された営業部員の売上は 1 つのみ記録され、更新が最新であるということを前提にしています。 指定された営業部員に対し、同じ日に 2 つ以上の売上が記録される場合は、前の例は正しく動作しません。 例では実行エラーではなく各`SalesYTD`値がその日に実際に起こっていた売上件数に関係なく、1 つだけの販売で更新します。 これは、1 つの UPDATE ステートメントで同じ行を 2 回更新しないためです。  
  
 1 つ以上の販売が同じ日に発生することが指定された営業部員の各販売員のすべての売上集計する必要がまとめて内での状況で、`UPDATE`ステートメントでは、次の例で示すようにします。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Sales.SalesPerson  
SET SalesYTD = SalesYTD +   
    (SELECT SUM(so.SubTotal)   
     FROM Sales.SalesOrderHeader AS so  
     WHERE so.OrderDate = (SELECT MAX(OrderDate)  
                           FROM Sales.SalesOrderHeader AS so2  
                           WHERE so2.SalesPersonID = so.SalesPersonID)  
     AND Sales.SalesPerson.BusinessEntityID = so.SalesPersonID  
     GROUP BY so.SalesPersonID);  
GO  
```  
  
###  <a name="RemoteTables"></a>リモート テーブル内の行を更新します。  
 このセクションの例を使用してリモートの対象テーブルの行を更新する方法をデモンストレーション、[リンク サーバー](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)または[行セット関数](../../t-sql/functions/rowset-functions-transact-sql.md)リモート テーブルを参照します。  
  
#### <a name="o-updating-data-in-a-remote-table-by-using-a-linked-server"></a>O.  リンク サーバーを使用してリモート テーブルのデータを更新する  
 次の例では、リモート サーバー上のテーブルを更新します。 使用してリモート データ ソースへのリンクを作成した後、 [sp_addlinkedserver](../../relational-databases/system-stored-procedures/sp-addlinkedserver-transact-sql.md)です。 server.catalog.schema.object という形式の 4 部構成のオブジェクト名の一部として、リンク サーバー名 `MyLinkServer` を指定します。 `@datasrc` には有効なサーバー名を指定する必要があります。  
  
```sql  
USE master;  
GO  
-- Create a link to the remote data source.   
-- Specify a valid server name for @datasrc as 'server_name' or 'server_nameinstance_name'.  
  
EXEC sp_addlinkedserver @server = N'MyLinkServer',  
    @srvproduct = N' ',  
    @provider = N'SQLNCLI10',   
    @datasrc = N'<server name>',  
    @catalog = N'AdventureWorks2012';  
GO  
USE AdventureWorks2012;  
GO  
-- Specify the remote data source using a four-part name   
-- in the form linked_server.catalog.schema.object.  
  
UPDATE MyLinkServer.AdventureWorks2012.HumanResources.Department  
SET GroupName = N'Public Relations'  
WHERE DepartmentID = 4;  
```  
  
#### <a name="p-updating-data-in-a-remote-table-by-using-the-openquery-function"></a>P. OPENQUERY 関数を使用してリモート テーブルのデータを更新する  
 次の例では、リモート テーブルの行を更新を指定して、 [OPENQUERY](../../t-sql/functions/openquery-transact-sql.md)行セット関数。 この例では、前の例で作成したリンク サーバー名を使用します。  
  
```sql  
UPDATE OPENQUERY (MyLinkServer, 'SELECT GroupName FROM HumanResources.Department WHERE DepartmentID = 4')   
SET GroupName = 'Sales and Marketing';  
```  
  
#### <a name="q-updating-data-in-a-remote-table-by-using-the-opendatasource-function"></a>Q.  OPENDATASOURCE 関数を使用してリモート テーブルのデータを更新する  
 次の例では、リモート テーブルに行を挿入を指定して、 [OPENDATASOURCE](../../t-sql/functions/opendatasource-transact-sql.md)行セット関数。 形式を使用して、データ ソースの有効なサーバー名を指定*server_name*または*server_name \instance_name*です。 インスタンスを構成する必要があります[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]Ad Hoc Distributed Queries 用です。 詳細については、次を参照してください。 [ad hoc distributed queries サーバー構成オプション](../../database-engine/configure-windows/ad-hoc-distributed-queries-server-configuration-option.md)です。  
  
```sql  
UPDATE OPENQUERY (MyLinkServer, 'SELECT GroupName FROM HumanResources.Department WHERE DepartmentID = 4')   
SET GroupName = 'Sales and Marketing';  
```  
  
###  <a name="LOBValues"></a>ラージ オブジェクト データ型を更新します。  
 このセクションの例では、ラージ オブジェクト (LOB) データ型で定義された列の値を更新する方法を示します。  
  
#### <a name="r-using-update-with-write-to-modify-data-in-an-nvarcharmax-column"></a>R.  UPDATE を .WRITE と共に使用し、nvarchar(max) 列のデータを変更する  
 次の例を使用します。部分的な値を更新する書き込み句`DocumentSummary`、 **nvarchar (max)**内の列、`Production.Document`テーブル。 置換する語、既存データ内で置換される語の開始位置 (オフセット)、置換する文字数 (長さ) を指定することにより、`components` という語が、`features` という語で置換されます。 例では、また句を使用して出力を返す前に、のイメージと後、`DocumentSummary`列を`@MyTableVar`テーブル変数。  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table (  
    SummaryBefore nvarchar(max),  
    SummaryAfter nvarchar(max));  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N'features',28,10)  
OUTPUT deleted.DocumentSummary,   
       inserted.DocumentSummary   
    INTO @MyTableVar  
WHERE Title = N'Front Reflector Bracket Installation';  
SELECT SummaryBefore, SummaryAfter   
FROM @MyTableVar;  
GO  
```  
  
#### <a name="s-using-update-with-write-to-add-and-remove-data-in-an-nvarcharmax-column"></a>S.  UPDATE を .WRITE と共に使用し、nvarchar(max) 列のデータを追加および削除する  
 次の例では、追加し、データの削除、 **nvarchar (max)**を NULL に設定して現在の値を持つ列。 します。NULL 列を変更する句を使用することはできません、まず、列は一時的なデータを設定を記述します。 次に .WRITE 句を使用して、このデータを正しいデータで置換します。 その後の例では、列の値の最後にデータを追加し、列からデータを削除 (切り捨て) し、最後に列から部分的なデータを削除します。 SELECT ステートメントは、各 UPDATE ステートメントで生成されたデータ変更を表示します。  
  
```sql  
USE AdventureWorks2012;  
GO  
-- Replacing NULL value with temporary data.  
UPDATE Production.Document  
SET DocumentSummary = N'Replacing NULL value'  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Replacing temporary data with the correct data. Setting @Length to NULL   
-- truncates all existing data from the @Offset position.  
UPDATE Production.Document  
SET DocumentSummary .WRITE(N'Carefully inspect and maintain the tires and crank arms.',0,NULL)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Appending additional data to the end of the column by setting   
-- @Offset to NULL.  
UPDATE Production.Document  
SET DocumentSummary .WRITE (N' Appending data to the end of the column.', NULL, 0)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Removing all data from @Offset to the end of the existing value by   
-- setting expression to NULL.   
UPDATE Production.Document  
SET DocumentSummary .WRITE (NULL, 56, 0)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
-- Removing partial data beginning at position 9 and ending at   
-- position 21.  
UPDATE Production.Document  
SET DocumentSummary .WRITE ('',9, 12)  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
SELECT DocumentSummary   
FROM Production.Document  
WHERE Title = N'Crank Arm and Tire Maintenance';  
GO  
```  
  
#### <a name="t-using-update-with-openrowset-to-modify-a-varbinarymax-column"></a>T.  UPDATE を OPENROWSET と共に使用し、varbinary(max) 列を変更する  
 次の例に格納されている既存のイメージが置き換えられます、 **varbinary (max)**新しいイメージを含む列。 [OPENROWSET](../../t-sql/functions/openrowset-transact-sql.md)関数は、この列にイメージの読み込みに BULK オプションと共に使用します。 この例では、`Tires.jpg` という名前のファイルが指定されたファイル パスに存在することを前提としています。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.ProductPhoto  
SET ThumbNailPhoto = (  
    SELECT *  
    FROM OPENROWSET(BULK 'c:Tires.jpg', SINGLE_BLOB) AS x )  
WHERE ProductPhotoID = 1;  
GO  
```  
  
#### <a name="u-using-update-to-modify-filestream-data"></a>U.  UPDATE を使用して FILESTREAM データを変更する  
 次の例では、UPDATE ステートメントを使用して、ファイル システムのファイルのデータを変更します。 大量のデータをファイルにストリーミングする場合、この方法はお勧めできません。 適切な Win32 インターフェイスを使用してください。 ファイル レコード内の任意のテキストを、 `Xray 1`というテキストに置換する例を次に示します。 詳細については、「[FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)」をご覧ください。  
  
```sql  
UPDATE Archive.dbo.Records  
SET [Chart] = CAST('Xray 1' as varbinary(max))  
WHERE [SerialNumber] = 2;  
```  
  
###  <a name="UDTs"></a>ユーザー定義型を更新します。  
 次の例では、CLR ユーザー定義型 (UDT) の列の値を変更します。 3 つの方法が示されています。 ユーザー定義の列の詳細については、次を参照してください。 [clr ユーザー定義型](../../relational-databases/clr-integration-database-objects-user-defined-types/clr-user-defined-types.md)です。  
  
#### <a name="v-using-a-system-data-type"></a>V.  システム データ型を使用する  
 ユーザー定義型で [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] システム データ型からの暗黙的または明示的な変換がサポートされている場合は、そのシステム データ型の値を指定することによって、UDT を更新できます。 次の例は、文字列からの明示的な変換によって、ユーザー定義型 `Point` の列の値を更新する方法を示します。  
  
```sql  
UPDATE dbo.Cities  
SET Location = CONVERT(Point, '12.3:46.2')  
WHERE Name = 'Anchorage';  
```  
  
#### <a name="w-invoking-a-method"></a>W. メソッドを呼び出す  
 ミューテーターとしてマークされたユーザー定義型のメソッドを呼び出し、更新を実行することによって、UDT を更新できます。 次の例では、`Point` 型の `SetXY` というミューテーター メソッドを呼び出します。 これにより、その型のインスタンスの状態が更新されます。  
  
```sql  
UPDATE dbo.Cities  
SET Location.SetXY(23.5, 23.5)  
WHERE Name = 'Anchorage';  
```  
  
#### <a name="x-modifying-the-value-of-a-property-or-data-member"></a>X. プロパティまたはデータ メンバーの値を変更する  
 ユーザー定義型の登録済みプロパティまたはパブリック データ メンバーの値を変更することによって、UDT を更新できます。 値を指定する式は、プロパティの型に暗黙的に変換できる必要があります。 次の例では、ユーザー定義型 `X` のプロパティ `Point` の値を変更します。  
  
```sql  
UPDATE dbo.Cities  
SET Location.X = 23.5  
WHERE Name = 'Anchorage';  
```  
  
###  <a name="TableHints"></a>ヒントを使用して、クエリ オプティマイザーの既定の動作を上書きする.  
 このセクションの例では、テーブル ヒントとクエリ ヒントを使用して、UPDATE ステートメントを処理する際のクエリ オプティマイザーの既定の動作を一時的に上書きする方法を示します。  
  
> [!CAUTION]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]通常、クエリ オプティマイザーがクエリの最適な実行プランを選択、ヒントは、経験を積んだ開発者やデータベース管理者が、最後の手段としてのみ使用することをお勧めします。  
  
#### <a name="y-specifying-a-table-hint"></a>Y. テーブル ヒントを指定する  
 次の例を指定します、[テーブル ヒント](../../t-sql/queries/hints-transact-sql-table.md)TABLOCK です。 このヒントは、テーブルに対して共有ロックが行われることを示す`Production.Product`UPDATE ステートメントが終了するまで保持されているとします。  
  
```sql  
USE AdventureWorks2012;  
GO  
UPDATE Production.Product  
WITH (TABLOCK)  
SET ListPrice = ListPrice * 1.10  
WHERE ProductNumber LIKE 'BK-%';  
GO  
```  
  
#### <a name="z-specifying-a-query-hint"></a>Z. クエリ ヒントを指定する  
 次の例を指定します、[クエリ ヒント](../../t-sql/queries/hints-transact-sql-query.md)`OPTIMIZE FOR (@variable)` UPDATE ステートメントでします。 このヒントは、クエリをコンパイルおよび最適化するときにローカル変数に対して特定の値を使用するように、クエリ オプティマイザーに指示します。 この値はクエリを最適化する過程でのみ使用され、クエリの実行時には使用されません。  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE PROCEDURE Production.uspProductUpdate  
@Product nvarchar(25)  
AS  
SET NOCOUNT ON;  
UPDATE Production.Product  
SET ListPrice = ListPrice * 1.10  
WHERE ProductNumber LIKE @Product  
OPTION (OPTIMIZE FOR (@Product = 'BK-%') );  
GO  
-- Execute the stored procedure   
EXEC Production.uspProductUpdate 'BK-%';  
```  
  
###  <a name="CaptureResults"></a>UPDATE ステートメントの結果をキャプチャ  
 このセクションの例を使用する方法をデモンストレーション、 [OUTPUT 句](../../t-sql/queries/output-clause-transact-sql.md)情報や、それらに基づく式を返す、影響を受ける各行 UPDATE ステートメントでします。 これらの結果は処理アプリケーションに返され、確認メッセージの表示、アーカイブ化、その他のアプリケーション要件で使用することができます。  
  
#### <a name="aa-using-update-with-the-output-clause"></a>AA. UPDATE ステートメントを OUTPUT 句と共に使用する  
 次の例では、最初の 10 行について `VacationHours` テーブルの列 `Employee` を 1.25 倍に更新し、列 `ModifiedDate` の値を現在の日付に設定します。 `OUTPUT` 句は、`VacationHours` を適用する前の `UPDATE` 列の `deleted.VacationHours` の値と、`inserted.VacationHours` 列の更新後の値を `@MyTableVar` テーブル変数に返します。  
  
 この後に、`SELECT` 内の値、および `@MyTableVar` テーブルの更新操作の結果を返す 2 つの `Employee` ステートメントが続きます。 例については、OUTPUT 句を使用して、次を参照してください。 [OUTPUT 句と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/output-clause-transact-sql.md).  
  
```sql  
USE AdventureWorks2012;  
GO  
DECLARE @MyTableVar table(  
    EmpID int NOT NULL,  
    OldVacationHours int,  
    NewVacationHours int,  
    ModifiedDate datetime);  
UPDATE TOP (10) HumanResources.Employee  
SET VacationHours = VacationHours * 1.25,  
    ModifiedDate = GETDATE()   
OUTPUT inserted.BusinessEntityID,  
       deleted.VacationHours,  
       inserted.VacationHours,  
       inserted.ModifiedDate  
INTO @MyTableVar;  
--Display the result set of the table variable.  
SELECT EmpID, OldVacationHours, NewVacationHours, ModifiedDate  
FROM @MyTableVar;  
GO  
--Display the result set of the table.  
SELECT TOP (10) BusinessEntityID, VacationHours, ModifiedDate  
FROM HumanResources.Employee;  
GO  
```  
  
###  <a name="Other"></a>その他のステートメントで UPDATE を使用  
 このセクションの例では、他のステートメントでの UPDATE の使用方法を示します。  
  
#### <a name="ab-using-update-in-a-stored-procedure"></a>AB. UPDATE をストアド プロシージャで使用する  
 次の例では、UPDATE ステートメントをストアド プロシージャで使用しています。 このプロシージャは、1 つの入力パラメーター`@NewHours`と 1 つの出力パラメーター`@RowCount`です。 `@NewHours`パラメーターの値が列を更新する UPDATE ステートメントで使用される`VacationHours`表内の`HumanResources.Employee`します。 `@RowCount`をローカル変数に影響を受ける行の数を返す出力パラメーターを使用します。 条件付きで設定されている値を決定する SET 句で CASE 式が使用される`VacationHours`です。 ときに、従業員給与が時給ベース (`SalariedFlag` = 0)、`VacationHours`で指定された値の合計時間の現在の数に設定されている`@NewHours`、それ以外の`VacationHours`で指定された値に設定されている`@NewHours`です。  
  
```sql  
USE AdventureWorks2012;  
GO  
CREATE PROCEDURE HumanResources.Update_VacationHours  
@NewHours smallint  
AS   
SET NOCOUNT ON;  
UPDATE HumanResources.Employee  
SET VacationHours =   
    ( CASE  
         WHEN SalariedFlag = 0 THEN VacationHours + @NewHours  
         ELSE @NewHours  
       END  
    )  
WHERE CurrentFlag = 1;  
GO  
  
EXEC HumanResources.Update_VacationHours 40;  
```  
  
#### <a name="ac-using-update-in-a-trycatch-block"></a>AC. TRY...CATCH ブロックで UPDATE を使用する  
 次の例では、TRY で UPDATE ステートメントを使用しています.CATCH ブロックを更新操作中に発生する可能性がありますで実行エラーを処理します。  
  
```sql  
USE AdventureWorks2012;  
GO  
BEGIN TRANSACTION;  
  
BEGIN TRY  
    -- Intentionally generate a constraint violation error.  
    UPDATE HumanResources.Department  
    SET Name = N'MyNewName'  
    WHERE DepartmentID BETWEEN 1 AND 2;  
END TRY  
BEGIN CATCH  
    SELECT   
         ERROR_NUMBER() AS ErrorNumber  
        ,ERROR_SEVERITY() AS ErrorSeverity  
        ,ERROR_STATE() AS ErrorState  
        ,ERROR_PROCEDURE() AS ErrorProcedure  
        ,ERROR_LINE() AS ErrorLine  
        ,ERROR_MESSAGE() AS ErrorMessage;  
  
    IF @@TRANCOUNT > 0  
        ROLLBACK TRANSACTION;  
END CATCH;  
  
IF @@TRANCOUNT > 0  
    COMMIT TRANSACTION;  
GO  
```  
  
## <a name="examples-includesssdwincludessssdw-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDW](../../includes/sssdw-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="ad-using-a-simple-update-statement"></a>AD. 単純な UPDATE ステートメントを使用する  
 次の例に示すがどのようにすべての行を受けることができる場合、WHERE 句は使用されませんを更新する行 (または行) を指定します。  
  
 この例の値を更新、`EndDate`と`CurrentFlag`のすべての行の列、`DimEmployee`テーブル。  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimEmployee  
SET EndDate = '2010-12-31', CurrentFlag='False';  
```  
  
 UPDATE ステートメントでは計算値を使用することもできます。 次の例は、`ListPrice` テーブルのすべての行の `Product` 列の値を倍にします。  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimEmployee  
SET BaseRate = BaseRate * 2;  
```  
  
### <a name="ae-using-the-update-statement-with-a-where-clause"></a>AE. WHERE 句で UPDATE ステートメントを使用します。  
 次の例では、WHERE 句を使用して更新する行を指定します。  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimEmployee  
SET FirstName = 'Gail'  
WHERE EmployeeKey = 500;  
```  
  
### <a name="af-using-the-update-statement-with-label"></a>AF. UPDATE ステートメント ラベルと共に使用します。  
 次の例では、UPDATE ステートメントのラベルの使用を示します。  
  
```sql  
-- Uses AdventureWorks  
  
UPDATE DimProduct  
SET ProductSubcategoryKey = 2   
WHERE ProductKey = 313  
OPTION (LABEL = N'label1');  
```  
  
### <a name="ag-using-the-update-statement-with-information-from-another-table"></a>可用性グループです。 別のテーブルの情報を使用して UPDATE ステートメントを実行する  
 この例では、年ごとの売上合計を格納するテーブルを作成します。 2004 年の FactInternetSales テーブルに対して SELECT ステートメントを実行して、総売り上げ高を更新します。  
  
```sql  
-- Uses AdventureWorks  
  
CREATE TABLE YearlyTotalSales (  
    YearlySalesAmount money NOT NULL,  
    Year smallint NOT NULL )  
WITH ( DISTRIBUTION = REPLICATE );  
  
INSERT INTO YearlyTotalSales VALUES (0, 2004);  
INSERT INTO YearlyTotalSales VALUES (0, 2005);  
INSERT INTO YearlyTotalSales VALUES (0, 2006);  
  
UPDATE YearlyTotalSales  
SET YearlySalesAmount=  
(SELECT SUM(SalesAmount) FROM FactInternetSales WHERE OrderDateKey >=20040000 AND OrderDateKey < 20050000)  
WHERE Year=2004;  
  
SELECT * FROM YearlyTotalSales;   
```  

### <a name="ah-ansi-join-replacement-for-update-statements"></a>AH. Update ステートメントの代わりに ANSI 結合
一緒に ANSI 結合構文を使用して更新または削除を実行する 2 つ以上のテーブルを結合する複雑な更新があることがあります。  

このテーブルを更新する必要がありました想像してください。  

```sql
CREATE TABLE [dbo].[AnnualCategorySales]
(   [EnglishProductCategoryName]    NVARCHAR(50)    NOT NULL
,   [CalendarYear]                  SMALLINT        NOT NULL
,   [TotalSalesAmount]              MONEY           NOT NULL
)
WITH
(
    DISTRIBUTION = ROUND_ROBIN
)
;  
```

次のように、元のクエリが説明しました。  

```
UPDATE  acs
SET     [TotalSalesAmount] = [fis].[TotalSalesAmount]
FROM    [dbo].[AnnualCategorySales]     AS acs
JOIN    (
        SELECT  [EnglishProductCategoryName]
        ,       [CalendarYear]
        ,       SUM([SalesAmount])              AS [TotalSalesAmount]
        FROM    [dbo].[FactInternetSales]       AS s
        JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
        JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
        JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
        JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
        WHERE   [CalendarYear] = 2004
        GROUP BY
                [EnglishProductCategoryName]
        ,       [CalendarYear]
        ) AS fis
ON  [acs].[EnglishProductCategoryName]  = [fis].[EnglishProductCategoryName]
AND [acs].[CalendarYear]                = [fis].[CalendarYear]
;  
```

[!INCLUDE[ssSDW_md](../../includes/sssdw-md.md)] ANSI を UPDATE ステートメントの FROM 句で結合をサポートしません、少し変更することがなく経由でこのコードをコピーすることはできません。  

CTAS と暗黙の結合の組み合わせを使用すると、このコードに置き換えます。  

```sql
-- Create an interim table
CREATE TABLE CTAS_acs
WITH (DISTRIBUTION = ROUND_ROBIN)
AS
SELECT  ISNULL(CAST([EnglishProductCategoryName] AS NVARCHAR(50)),0)    AS [EnglishProductCategoryName]
,       ISNULL(CAST([CalendarYear] AS SMALLINT),0)                      AS [CalendarYear]
,       ISNULL(CAST(SUM([SalesAmount]) AS MONEY),0)                     AS [TotalSalesAmount]
FROM    [dbo].[FactInternetSales]       AS s
JOIN    [dbo].[DimDate]                 AS d    ON s.[OrderDateKey]             = d.[DateKey]
JOIN    [dbo].[DimProduct]              AS p    ON s.[ProductKey]               = p.[ProductKey]
JOIN    [dbo].[DimProductSubCategory]   AS u    ON p.[ProductSubcategoryKey]    = u.[ProductSubcategoryKey]
JOIN    [dbo].[DimProductCategory]      AS c    ON u.[ProductCategoryKey]       = c.[ProductCategoryKey]
WHERE   [CalendarYear] = 2004
GROUP BY
        [EnglishProductCategoryName]
,       [CalendarYear]
;

-- Use an implicit join to perform the update
UPDATE  AnnualCategorySales
SET     AnnualCategorySales.TotalSalesAmount = CTAS_ACS.TotalSalesAmount
FROM    CTAS_acs
WHERE   CTAS_acs.[EnglishProductCategoryName] = AnnualCategorySales.[EnglishProductCategoryName]
AND     CTAS_acs.[CalendarYear]               = AnnualCategorySales.[CalendarYear]
;

--Drop the interim table
DROP TABLE CTAS_acs
;
```
  
## <a name="see-also"></a>参照  
 [CREATE TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/create-table-transact-sql.md)   
 [CREATE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/create-trigger-transact-sql.md)   
 [カーソル &#40;Transact-SQL&#41;](../../t-sql/language-elements/cursors-transact-sql.md)   
 [DELETE &#40;Transact-SQL&#41;](../../t-sql/statements/delete-transact-sql.md)   
 [挿入 &#40; です。Transact SQL と &#41; です。](../../t-sql/statements/insert-transact-sql.md)   
 [テキストとイメージ関数 &#40;です。TRANSACT-SQL と #41 です。](http://msdn.microsoft.com/library/b9c70488-1bf5-4068-a003-e548ccbc5199)   
 [で common_table_expression と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/queries/with-common-table-expression-transact-sql.md)   
 [FILESTREAM &#40;SQL Server&#41;](../../relational-databases/blob/filestream-sql-server.md)  
  
  

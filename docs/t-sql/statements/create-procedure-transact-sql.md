---
title: "プロシージャ (TRANSACT-SQL) を作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- PROC
- PROCEDURE
- CREATE PROCEDURE
- CREATE_PROC_TSQL
- PROCEDURE_TSQL
- CREATE PROC
- PROC_TSQL
- CREATE_PROCEDURE_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- parameters [SQL Server], stored procedures
- table-valued parameters
- SET statement, stored procedures
- stored procedures [SQL Server], creating
- wildcard parameters [SQL Server]
- maximum size of stored procedures
- WITH RECOMPILE clause
- common language runtime [SQL Server], stored procedures
- CREATE PROCEDURE statement
- local temporary procedures [SQL Server]
- WITH ENCRYPTION clause
- output parameters [SQL Server]
- nesting stored procedures
- user-defined stored procedures [SQL Server]
- system stored procedures [SQL Server], creating
- deferred name resolution, stored procedures
- referenced tables [SQL Server]
- global temporary procedures [SQL Server]
- cursor data type
- temporary stored procedures [SQL Server]
- size [SQL Server], stored procedures
- automatic stored procedure execution
- creating stored procedures
ms.assetid: afe3d86d-c9ab-44e4-b74d-4e3dbd9cc58c
caps.latest.revision: 180
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: c2a0a43aefe59bc11f16445b5ee0c781179a33fa
ms.openlocfilehash: 23460288040b37ec6a09293bc02a46e4f9af94fa
ms.contentlocale: ja-jp
ms.lasthandoff: 09/07/2017

---
# <a name="create-procedure-transact-sql"></a>CREATE PROCEDURE (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  作成、[!INCLUDE[tsql](../../includes/tsql-md.md)]共通言語ランタイム (CLR) ストアド プロシージャまたは[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、Azure SQL Data Warehouse と並列データ ウェアハウスです。 ストアド プロシージャは、次のことを実行できる点で、他のプログラミング言語のプロシージャに似ています。  
  
-   入力パラメーターを受け取り、呼び出し元のプロシージャまたはバッチに出力パラメーターの形式で複数の値を返す。  
  
-   他のプロシージャの呼び出しなど、データベース内での操作を実行するプログラミング ステートメントを含む。  
  
-   呼び出し元のプロシージャまたはバッチの成功または失敗、および失敗の理由) を示すためにステータス値を返します。  
  
 このステートメントを使用して、現在のデータベースまたは一時プロシージャ内で永続的なプロシージャを作成する、 **tempdb**データベース。  
  
> [!NOTE]  
>  SQL Server への .NET Framework CLR の統合はこのトピックで説明します。 CLR 統合は、Azure には適用されません[!INCLUDE[ssSDS](../../includes/sssds-md.md)]です。

ジャンプ[簡単な例を](#Simple)ストアド プロシージャの構文の詳細をスキップして、基本的なは簡単な例を取得します。
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Transact-SQL Syntax for Stored Procedures in SQL Server and Azure SQL Database  
  
CREATE [ OR ALTER ] { PROC | PROCEDURE } 
    [schema_name.] procedure_name [ ; number ]   
    [ { @parameter [ type_schema_name. ] data_type }  
        [ VARYING ] [ = default ] [ OUT | OUTPUT | [READONLY]  
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
-- Transact-SQL Syntax for CLR Stored Procedures  
  
CREATE [ OR ALTER ] { PROC | PROCEDURE } 
    [schema_name.] procedure_name [ ; number ]   
    [ { @parameter [ type_schema_name. ] data_type }   
        [ = default ] [ OUT | OUTPUT ] [READONLY]  
    ] [ ,...n ]   
[ WITH EXECUTE AS Clause ]  
AS { EXTERNAL NAME assembly_name.class_name.method_name }  
[;]  
```  
  
```  
-- Transact-SQL Syntax for Natively Compiled Stored Procedures  
  
CREATE [ OR ALTER ] { PROC | PROCEDURE } [schema_name.] procedure_name  
    [ { @parameter data_type } [ NULL | NOT NULL ] [ = default ] 
        [ OUT | OUTPUT ] [READONLY] 
    ] [ ,... n ]  
  WITH NATIVE_COMPILATION, SCHEMABINDING [ , EXECUTE AS clause ]  
AS  
{  
  BEGIN ATOMIC WITH (set_option [ ,... n ] )  
sql_statement [;] [ ... n ]  
 [ END ]  
}  
 [;]  
  
<set_option> ::=  
    LANGUAGE =  [ N ] 'language'  
  | TRANSACTION ISOLATION LEVEL =  { SNAPSHOT | REPEATABLE READ | SERIALIZABLE }  
  | [ DATEFIRST = number ]  
  | [ DATEFORMAT = format ]  
  | [ DELAYED_DURABILITY = { OFF | ON } ]  
```  
  
```  
-- Transact-SQL Syntax for Stored Procedures in Azure SQL Data Warehouse
-- and Parallel Data Warehouse  
  
-- Create a stored procedure   
CREATE { PROC | PROCEDURE } [ schema_name.] procedure_name  
    [ { @parameterdata_type } [ OUT | OUTPUT ] ] [ ,...n ]  
AS { [ BEGIN ] sql_statement [;][ ,...n ] [ END ] }  
[;]  
```  
  
## <a name="arguments"></a>引数
または変更  
 **適用されます**: Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1)。  
  
 既に存在する場合は、プロシージャを変更します。
 
 *schema_name*  
 プロシージャが属するスキーマの名前を指定します。 プロシージャはスキーマ バインドされています。 プロシージャの作成時にスキーマ名を指定しない場合は、プロシージャを作成しているユーザーの既定のスキーマが自動的に割り当てられます。  
  
 *procedure_name*  
 プロシージャの名前を指定します。 プロシージャ名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)スキーマ内で一意である必要があります。  
  
 使用を避けるため、 **sp _**プロシージャの名前を付けるときにプレフィックスします。 このプレフィックスは、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でシステム プロシージャを指定するために使用されるものです。 このプレフィックスを使用すると、同じ名前のシステム プロシージャがある場合にアプリケーション コードが機能しなくなる可能性があります。  
  
 ローカルまたはグローバル一時プロシージャは、前に 1 つのシャープ記号 (#) を使用して作成する*procedure_name* (*#procedure_name*)、ローカル一時プロシージャとグローバル一時の 2 つのシャープ記号のプロシージャ (*##0.00;($# procedure_name*)。 ローカル一時プロシージャは、そのプロシージャが作成された接続のみで表示でき、その接続が閉じられると削除されます。 グローバル一時プロシージャは、すべての接続で使用でき、そのプロシージャを使用する最後のセッションが終了すると削除されます。 CLR プロシージャには一時名は指定できません。  
  
 プロシージャまたはグローバル一時プロシージャの名前は、## を含め最大で半角 128 文字です。 ローカル一時プロシージャの名前は、# を含め最大で半角 116 文字です。  
  
 **;** *数*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 同じ名前のプロシージャのグループ化に使用される整数を指定します (省略可能)。 グループ化したプロシージャは、DROP PROCEDURE ステートメントの 1 回の実行でまとめて削除できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssNoteDepFutureAvoid](../../includes/ssnotedepfutureavoid-md.md)]  
  
 番号付きプロシージャは使用できません、 **xml**または CLR ユーザー定義型し、プラン ガイドでは使用できません。  
  
 **@***パラメーター*  
 プロシージャ内で宣言されているパラメーターを指定します。 使用して、パラメーター名を指定、アット マーク (**@**) 最初の文字として。 パラメーター名は、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)です。 パラメーターはプロシージャに対してローカルです。同じパラメーター名を他のプロシージャで使用できます。  
  
 1 つ以上のパラメーター (最大 2,100 個) を宣言できます。 宣言される各パラメーターの値は、パラメーターに既定値が定義されていない場合、または別のパラメーターと同じ値を使用するよう設定されていない場合は、プロシージャの呼び出し時にユーザーが指定する必要があります。 プロシージャが含まれている場合[テーブル値パラメーター](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)パラメーターが呼び出しで不足していると、空のテーブルが渡されました。 パラメーターは定数式の代わりにのみ使用することができます。テーブル名、列名、またはその他のデータベース オブジェクト名の代わりにパラメーターを使用することはできません。 詳細については、「 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)」を参照してください。  
  
 FOR REPLICATION を指定した場合、パラメーターは宣言できません。  
  
 [ *type_schema_name***です。** *data_type*  
 パラメーターのデータ型とそのデータ型が属するスキーマを指定します。  
  
**に関するガイドライン[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャ**:  
  
-   すべて[!INCLUDE[tsql](../../includes/tsql-md.md)]データ型をパラメーターとして使用することができます。  
  
-   ユーザー定義テーブル型を使用して、テーブル値パラメーターを作成できます。 テーブル値パラメーターは、入力パラメーターとしてのみ指定でき、READONLY キーワードと共に使用する必要があります。 詳細については、次を参照してください[テーブル値パラメーター (&) #40";"データベース エンジン"&"#41;。](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)  
  
-   **カーソル**データ型の出力パラメーターであることができますのみと VARYING キーワードと共に使用する必要があります。  
  
**CLR プロシージャに関するガイドライン**:  
  
-   マネージ コード内に同等の型を持つネイティブの [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] データ型であれば、どの型でもパラメーターとして使用できます。 CLR 型間の通信の詳細については、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型を参照してください[CLR パラメーター データのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)です。 詳細については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]システム データ型とその構文を参照してください。[データ型 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/data-types/data-types-transact-sql.md).  
  
-   テーブル値または**カーソル**データ型をパラメーターとして使用することはできません。  
  
-   パラメーターのデータ型が CLR ユーザー定義型の場合は、その型に対する EXECUTE 権限が必要です。  
  
VARYING  
 出力パラメーターとしてサポートされている結果セットを指定します。 このパラメーターはプロシージャによって動的に作成され、その内容は変化します。 のみ適用されます**カーソル**パラメーター。 このオプションは、CLR プロシージャでは無効です。  
  
*既定値*  
 パラメーターの既定値。 既定値がパラメーターに定義されている場合は、そのパラメーターの値を指定せず、プロシージャを実行できます。 既定値は定数である必要があります、NULL にすることができます。 定数値はワイルドカードの形式で指定できるため、パラメーターをプロシージャに渡すときに LIKE キーワードを使用することができます。   
  
 既定値に記録される、 **sys.parameters.default** CLR プロシージャに対してのみの列です。 その列は NULL です[!INCLUDE[tsql](../../includes/tsql-md.md)]プロシージャのパラメーターです。  
  
OUT | OUTPUT  
 パラメーターが出力パラメーターであることを示します。 プロシージャの呼び出し元に値を返すには、OUTPUT パラメーターを使用します。 **テキスト**、 **ntext**、および**イメージ**パラメーターは、プロシージャが CLR プロシージャでない限り、出力パラメーターとして使用できません。 出力パラメーターは、プロシージャが CLR プロシージャでない場合は、カーソルのプレースホルダーにできます。 テーブル値データ型をプロシージャの OUTPUT パラメーターとして指定することはできません。  
  
READONLY  
 パラメーターを更新またはプロシージャの本体内で変更できないことを示します。 パラメーターの型がテーブル値型の場合は、READONLY を指定する必要があります。  
  
RECOMPILE  
 示します、[!INCLUDE[ssDE](../../includes/ssde-md.md)]強制的コンパイルが実行されるたびに、この手順のクエリ プランをキャッシュしません。 強制的に再コンパイルの理由の詳細については、次を参照してください。[ストアド プロシージャを再コンパイル](../../relational-databases/stored-procedures/recompile-a-stored-procedure.md)です。 このオプションは、FOR REPLICATION を指定した場合または CLR プロシージャには使用できません。  
  
 指示するため、[!INCLUDE[ssDE](../../includes/ssde-md.md)]プロシージャ内の個々 のクエリのクエリ プランを破棄するには、クエリの定義で RECOMPILE クエリ ヒントを使用します。 詳細については、「[クエリ ヒント &#40;Transact-SQL&#41;](../../t-sql/queries/hints-transact-sql-query.md)」を参照してください。  
  
ENCRYPTION  
 **適用されます**: SQL Server ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 示します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]CREATE PROCEDURE ステートメントの元のテキストを難読化された形式に変換します。 難読化の出力内のカタログ ビューのいずれかで直接表示がない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 システム テーブルまたはデータベース ファイルへのアクセス権を持たないユーザーは、暗号化した形式のテキストを取得できません。 ただし、テキストは経由でシステム テーブルにアクセスできるか、ユーザー特権を持つユーザーが使用できる、 [DAC ポート](../../database-engine/configure-windows/diagnostic-connection-for-database-administrators.md)または直接データベース ファイルにアクセスします。 また、サーバー プロセスにデバッガーをアタッチできるユーザーは、実行時に、暗号化を解除したプロシージャをメモリから取得できます。 システム メタデータへのアクセスの詳細については、次を参照してください。 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)です。  
  
 このオプションは、CLR プロシージャでは無効です。  
  
 このオプションで作成されたプロシージャは、の一部としてパブリッシュできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション。  
  
EXECUTE AS*句*  
 プロシージャを実行するセキュリティ コンテキストを指定します。  
  
 以降のネイティブ コンパイル ストアド プロシージャの[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]し、 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]、EXECUTE AS に制限はありません句。 [!INCLUDE[ssSQL14](../../includes/sssql14-md.md)] SELF、OWNER、および*'user_name'*句は、ネイティブ コンパイル ストアド プロシージャでサポートされます。  
  
 詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)」を参照してください。  
  
FOR REPLICATION  
 **適用されます**: SQL Server ([!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)])、[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 プロシージャがレプリケーション用に作成されていることを指定します。 そのため、サブスクライバーでプロシージャを実行することはできません。 FOR REPLICATION オプションを指定して作成したプロシージャは、プロシージャ フィルターとして使用され、レプリケーション時にのみ実行されます。 FOR REPLICATION を指定した場合、パラメーターは宣言できません。 CLR プロシージャには FOR REPLICATION は指定できません。 RECOMPILE オプションは、FOR REPLICATION を使って作成されたプロシージャでは無視されます。  
  
 A`FOR REPLICATION`手順では、オブジェクトの種類**RF**で**sys.objects**と**sys.procedures**です。  
  
 {[BEGIN] *sql_statement* [;][ ... *n*  ] [終了]}  
 プロシージャの本体を構成する 1 つ以上の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントを指定します。 省略可能な BEGIN キーワードと END キーワードを使用して、ステートメントを囲むことができます。 詳細については、後で説明する「ベスト プラクティス」、「全般的な解説」、および「制限事項と制約事項」をご覧ください。  
  
外部名*assembly_name***.***class_name***.***メソッド名が*  
 **適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、[!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)]です。  
  
 メソッドを指定します、 [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] CLR プロシージャを参照するアセンブリ。 *class_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子、アセンブリ内のクラスとして存在する必要があります。 クラスにピリオドを使用する名前空間で修飾された名前 (**.**) 名前空間の部分を分割する、クラス名を角かっこで区切る必要があります (**:operator[]**) または引用符 (**""**). 指定するメソッドは、クラスの静的メソッドであることが必要です。  
  
 既定では、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は CLR コードを実行できません。 作成、変更、および共通言語ランタイム モジュール; を参照するデータベース オブジェクトを削除することができます。ただし、これらの参照を実行することはできません[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]有効にするまで、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)です。 オプションを有効にするには、 [sp_configure](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
> [!NOTE]  
>  CLR プロシージャは、包含データベースではサポートされていません。  
  
ATOMIC WITH  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 アトミック ストアド プロシージャの実行を示します。 変更はコミットされるか、例外のスローによってすべての変更がロールバックされます。 ネイティブ コンパイル ストアド プロシージャには、ATOMIC WITH ブロックが必要です。  
  
 明示的に RETURN ステートメントによって、または暗黙的に実行の完了によってプロシージャの制御が戻ると (RETURN)、プロシージャによって実行された作業がコミットされます。 プロシージャによってスロー (THROW) が行われると、プロシージャによって実行された作業がロールバックされます。  
  
 XACT_ABORT はアトミック ブロック内で既定で ON であり、変更できません。 XACT_ABORT は、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ステートメントによって実行時エラーが発生した場合に、[!INCLUDE[tsql](../../includes/tsql-md.md)] が自動的に現在のトランザクションをロールバックするかどうかを指定します。  
  
 以下の SET オプションは、ATOMIC ブロック内で常に ON であり、変更できません。  
-   CONCAT_NULL_YIELDS_NULL  
-   QUOTED_IDENTIFIER、ARITHABORT  
-   NOCOUNT  
-   ANSI_NULLS  
-   ANSI_WARNINGS  
  
SET オプションは、ATOMIC ブロック内部では変更できません。 ユーザー セッション内の SET オプションは、ネイティブ コンパイル ストアド プロシージャのスコープでは使用されません。 これらのオプションは、コンパイル時に固定されます。  
  
BEGIN、ROLLBACK、および COMMIT 操作は、アトミック ブロック内では使用できません。  
  
 ネイティブ コンパイル ストアド プロシージャごとに、プロシージャのスコープの外部に 1 つの ATOMIC ブロックがあります。 ブロックを入れ子にすることはできません。 Atomic ブロックに関する詳細については、次を参照してください。 [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)です。  
  
**NULL** |NOT NULL します。  
 パラメーターで NULL 値を許すかどうかを示します。 NULL が既定値です。  
  
NATIVE_COMPILATION  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 プロシージャがネイティブにコンパイルされることを示します。 NATIVE_COMPILATION、SCHEMABINDING、および EXECUTE AS は、任意の順序で指定できます。 詳細については、次を参照してください。 [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)です。  
  
SCHEMABINDING  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 プロシージャによって参照されるテーブルを削除または変更できないようにします。 ネイティブ コンパイル ストアド プロシージャでは、SCHEMABINDING が必要です。 (詳細については、次を参照してください[Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)。)。SCHEMABINDING の制限は、ユーザー定義関数に対する場合と同じです。 詳細については、SCHEMABINDING のセクションを参照してください。 [CREATE FUNCTION & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-function-transact-sql.md).  
  
LANGUAGE = [N] 'language'  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 等価[言語 &#40; を設定TRANSACT-SQL と #41 です。](../../t-sql/statements/set-language-transact-sql.md)セッション オプション。 LANGUAGE = [N] 'language' は必須です。  
  
TRANSACTION ISOLATION LEVEL  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 ネイティブ コンパイル ストアド プロシージャでは必要です。 ストアド プロシージャのトランザクション分離レベルを指定します。 次のオプションがあります。  
  
 これらのオプションの詳細については、次を参照してください。 [SET TRANSACTION ISOLATION LEVEL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-transaction-isolation-level-transact-sql.md).  
  
REPEATABLE READ  
 他のトランザクションによって変更されていてもまだコミットされていないデータは、ステートメントで読み取ることができないことを指定します。 別のトランザクションが、現在のトランザクションが読み取ったデータを変更する場合、現在のトランザクションは失敗します。  
  
SERIALIZABLE  
 次のことを指定します。  
-   他のトランザクションで変更されたが、まだコミットされていないデータは、ステートメントで読み取れない。  
-   別のトランザクションが、現在のトランザクションが読み取ったデータを変更する場合、現在のトランザクションは失敗します。  
-   別のトランザクションでは、現在のトランザクション内のステートメントで読み取ったキー範囲に該当するキーの値を持つ新しい行が挿入、現在のトランザクションは失敗します。  
  
SNAPSHOT  
 トランザクションで任意のステートメントによって読み取られるデータのトランザクションの開始時に存在していたデータの一貫性のバージョンであることを指定します。  
  
DATEFIRST =*数*  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 週の最初の曜日を 1 ～ 7 の数値で指定します。 DATEFIRST は省略可能です。 指定しない場合、設定は指定された言語から推定されます。  
  
 詳細については、次を参照してください。 [SET DATEFIRST & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-datefirst-transact-sql.md).  
  
DATEFORMAT =*形式*  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 date、smalldatetime、datetime、datetime2、datetimeoffset の各文字列を解釈する際の日付要素 (月、日、年) の順序を指定します。 DATEFORMAT は省略可能です。 指定しない場合、設定は指定された言語から推定されます。  
  
 詳細については、次を参照してください。 [SET DATEFORMAT と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-dateformat-transact-sql.md).  
  
DELAYED_DURABILITY = { OFF | ON }  
 **適用されます**:[!INCLUDE[ssSQL14](../../includes/sssql14-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]と[!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)]です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] によるトランザクションのコミットには、完全持続性、既定値、または遅延持続性が適用されます。  
  
 詳細については、次を参照してください。[トランザクションの持続性の制御](../../relational-databases/logs/control-transaction-durability.md)です。  

## <a name="Simple"></a>簡単な例

作業を開始するために、2 つの簡単な例を次に示します。  
`SELECT DB_NAME() AS ThisDB;`現在のデータベースの名前を返します。  
など、ストアド プロシージャで、そのステートメントをラップすることができます。  
```sql  
CREATE PROC What_DB_is_this     
AS   
SELECT DB_NAME() AS ThisDB; 
```   
ステートメントを使用してストアド プロシージャを呼び出します。`EXEC What_DB_is_this;`   

やや複雑は、プロシージャの柔軟性を高めるへの入力パラメーターを提供することです。 例:  
```sql   
CREATE PROC What_DB_is_that @ID int   
AS    
SELECT DB_NAME(@ID) AS ThatDB;   
```   
プロシージャを呼び出すときは、データベースの id 番号を提供します。 たとえば、`EXEC What_DB_is_that 2;`返します`tempdb`です。   

参照してください[例](#Examples)より多くの例は、このトピックの最後の方です。     
    
## <a name="best-practices"></a>ベスト プラクティス  
 ここではベスト プラクティスをすべて網羅しているわけではありませんが、次の推奨事項に従うと、プロシージャのパフォーマンスが向上する場合があります。  
  
-   プロシージャの本体の最初のステートメントとして SET NOCOUNT ON ステートメントを使用する。 つまり、SET NOCOUNT ON ステートメントを AS キーワードの直後に配置します。 この有効にするメッセージ[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]SELECT、INSERT、UPDATE、MERGE、後に、クライアントに返送され、DELETE ステートメントが実行されます。 この不要なネットワーク オーバーヘッドを軽減することにより、データベースとアプリケーションの全体的なパフォーマンスが向上します。 詳細については、次を参照してください。 [SET NOCOUNT & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/set-nocount-transact-sql.md).  
  
-   プロシージャ内のデータベース オブジェクトを作成または参照するときにスキーマ名を使用する。 処理時間がかかりません、[!INCLUDE[ssDE](../../includes/ssde-md.md)]複数のスキーマを検索するがあるない場合は、オブジェクト名を解決するのには。 また、権限とアクセスの問題が原因で、スキーマを指定せずに作成されたオブジェクトに割り当てられているユーザーの既定のスキーマも回避されます。  
  
-   WHERE 句と JOIN 句で指定された列を関数でラップしないようにする。 ラップすると、列が非決定的になるため、クエリ プロセッサでインデックスを使用できなくなります。  
  
-   多くのデータ行を返す SELECT ステートメントではスカラー関数を使用しない。 スカラー関数はすべての行に適用する必要があるため、結果として、行ベースの処理のような動作になり、パフォーマンスが低下します。  
  
-   使用を避ける`SELECT *`です。 代わりに、必要な列名を指定します。 これにより、プロシージャの実行を停止する[!INCLUDE[ssDE](../../includes/ssde-md.md)]のエラーのいくつかを回避できます。 たとえば、`SELECT *`数まで、12 列のテーブルからデータを返すし、そのデータを 12 列の一時テーブルに挿入するステートメントが成功するか、いずれかのテーブルの列の順序を変更します。  
  
-   非常に多くのデータを処理したり返したりしない。 プロシージャ コードによってできるだけ早く結果を絞り込むことで、プロシージャが実行する後続の操作で使用されるデータ セットをできる限り小さくします。 基本的なデータのみをクライアント アプリケーションに送信します。 その方が、ネットワーク経由で余分なデータを送信して、クライアント アプリケーションで不必要に大きな結果セットを処理させるよりも効率的です。  
  
-   開始/コミット トランザクションを使用して、明示的なトランザクションを使用して、トランザクションはできるだけ短くします。 トランザクションが長いほど、レコードのロックが長くなり、デッドロックが発生する可能性が高くなります。  
  
-   プロシージャ内のエラー処理に [!INCLUDE[tsql](../../includes/tsql-md.md)] TRY...CATCH 機能を使用する。 TRY...CATCH は [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントのブロック全体をカプセル化できます。 これにより、パフォーマンスのオーバーヘッドが低減されるだけでなく、記述するプログラムの数が大幅に削減され、エラー レポートの精度も向上します。  
  
-   プロシージャの本体の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメント CREATE TABLE または ALTER TABLE によって参照されているすべてのテーブル列で DEFAULT キーワードを使用する。 これは、null 値を許容しない列に NULL を渡すようにします。  
  
-   一時テーブルの各列に NULL または NOT NULL を使用する。 ANSI_DFLT_ON および ANSI_DFLT_OFF オプションを制御する方法、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] CREATE TABLE または ALTER TABLE ステートメントでは、これらの属性は指定されていないときに、列に NULL または NOT NULL 属性を割り当てます。 ある接続でこれらのオプションを使用してプロシージャを実行する場合、オプションの設定がプロシージャを作成した接続時と異なっていると、新しい接続で作成されるテーブルの列に対して、異なる NULL 許容属性や異なる動作を指定することができます。 各列に NULL または NOT NULL を明示的に宣言すると、プロシージャを実行するすべての接続に対して同じ NULL 許容属性を使用することにより、複数の一時テーブルが作成されます。  
  
-   NULL を変換する変更ステートメントを使用し、クエリから NULL 値を含む行を除外するロジックを含める。 注意してくださいで[!INCLUDE[tsql](../../includes/tsql-md.md)]"nothing"の値や NULL は、空ではありません。 NULL は不明な値を表すプレースホルダーのため、特に結果セットに対してクエリを実行している場合や集計関数を使用している場合は、予期しない動作が発生することがあります。  
  
-   個別の値に対する特定のニーズがない限り、UNION 演算子または OR 演算子の代わりに UNION ALL 演算子を使用する。 フィルターによって重複が結果セットから除外されないため、UNION ALL 演算子の処理オーバーヘッドが少なくなります。  
  
## <a name="general-remarks"></a>全般的な解説  
 プロシージャの最大サイズは、事前には定義されていません。  
  
 ユーザー定義の手順で指定された変数を指定できますまたはシステム環境変数のように @@SPIDです。  
  
 プロシージャは最初の実行時にコンパイルされ、データを取得するための最適なアクセス プランが決定されます。 プロシージャが[!INCLUDE[ssDE](../../includes/ssde-md.md)]のプラン キャッシュに残っている場合、次にそのストアド プロシージャを実行するときには生成済みのプランを再使用できます。  
  
 1 つ以上のプロシージャが自動的に実行できる場合に[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]を開始します。 システム管理者によって、プロシージャを作成する必要があります、**マスター**データベースし、で実行される、 **sysadmin**バック グラウンド プロセスとして固定サーバー ロール。 プロシージャに入力または出力パラメーターを指定することはできません。 詳細については、次を参照してください。[ストアド プロシージャを実行する](../../relational-databases/stored-procedures/execute-a-stored-procedure.md)です。  
  
 プロシージャは、別のプロシージャを呼び出す場合、または CLR ルーチン、型、集計を参照してマネージ コードを実行する場合に入れ子になります。 プロシージャとマネージ コード参照は、32 レベルまで入れ子にすることができます。 入れ子のレベルは、呼び出されたプロシージャまたはマネージ コード参照の実行が開始されると 1 つ増加し、呼び出されたプロシージャまたはマネージ コード参照の実行が終了されると 1 つ減少します。 マネージ コード内から呼び出されたメソッドは、この入れ子レベルの制限としてはカウントされません。 ただし、CLR ストアド プロシージャで、SQL Server マネージ プロバイダーを利用してデータ アクセス操作が実行される場合、マネージ コードから SQL への移行時に入れ子のレベルが 1 つ追加されます。  
  
 入れ子の最高レベルを越える呼び出しを行うと、一連の呼び出しが失敗します。 使用することができます、@@NESTLEVELを現在のストアド プロシージャの実行の入れ子レベルを返す関数。  
  
## <a name="interoperability"></a>相互運用性  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)] プロシージャを作成または変更すると、[!INCLUDE[tsql](../../includes/tsql-md.md)]では SET QUOTED_IDENTIFIER と SET ANSI_NULLS の両方の設定が保存されます。 これらの元の設定は、プロシージャの実行時に使用されます。 したがって、プロシージャの実行中は、SET QUOTED_IDENTIFIER と SET ANSI_NULLS のクライアント セッションの設定は無視されます。  
  
 SET ARITHABORT、SET ANSI_WARNINGS、SET ANSI_PADDINGS など他の SET オプションは、プロシージャの作成時または変更時に保存されません。 プロシージャのロジックが特定の設定に依存する場合は、プロシージャの先頭に SET ステートメントを挿入し、適切な設定を確保します。 プロシージャから SET ステートメントを実行すると、その設定は、プロシージャが実行を終了するまでの間だけ有効になります。 プロシージャが終了すると、その設定は、プロシージャが呼び出されたときの値に復元されます。 この機能を使用すると、個々のクライアントでプロシージャのロジックに影響を与えずに必要なオプションを設定できます。  
  
 SET ステートメントは、SET SHOWPLAN_TEXT および SET SHOWPLAN_ALL を除き、プロシージャ内部で指定できます。 バッチで同時に他のステートメントを実行することはできません。 選択した SET オプションは、プロシージャの実行中は有効で、実行後に元の設定に戻されます。  
  
> [!NOTE]  
>  プロシージャまたはユーザー定義関数でパラメーターを渡す場合や、バッチ ステートメントで変数を宣言または設定する場合には、SET ANSI_WARNINGS は無視されます。 たとえば、として変数が定義されている**char**(3) とし、次の 3 つの文字を超える値に設定、データは切り捨てに定義されているサイズと、INSERT または UPDATE ステートメントは成功します。  
  
## <a name="limitations-and-restrictions"></a>制限事項と制約事項  
 CREATE PROCEDURE ステートメントは、その他と組み合わせることはできません[!INCLUDE[tsql](../../includes/tsql-md.md)]1 つのバッチ内のステートメント。  
  
 次のステートメントは、ストアド プロシージャの本体では使用できません。  
  
||||  
|-|-|-|  
|CREATE AGGREGATE|CREATE SCHEMA|[SET SHOWPLAN_TEXT]|  
|CREATE DEFAULT|CREATE TRIGGER または ALTER TRIGGER|SET SHOWPLAN_XML|  
|CREATE FUNCTION または ALTER FUNCTION|CREATE VIEW または ALTER VIEW|使用して*database_name*|  
|CREATE PROCEDURE または ALTER PROCEDURE|[SET PARSEONLY]||  
|CREATE RULE|SET SHOWPLAN_ALL||  
  
 プロシージャはまだ存在していないテーブルを参照できます。 作成時には、構文チェックのみが行われます。 プロシージャは、最初の実行時までコンパイルされません。 プロシージャ内で参照されているすべてのオブジェクトが解決されるのは、コンパイル時のみです。 存在しないテーブルを参照する構文的に正しいプロシージャを正常に作成するそのため、ただし、参照先のテーブルが存在しない場合、プロシージャは実行時に失敗します。  
  
 関数名を、パラメーターの既定値として指定したり、プロシージャの実行時にパラメーターに渡される値として指定したりできません。 ただし、次の例に示すように、関数を変数として渡すことができます。  
  
```  
-- Passing the function value as a variable.  
DECLARE @CheckDate datetime = GETDATE();  
EXEC dbo.uspGetWhereUsedProductID 819, @CheckDate;   
GO  
```  
  
 プロシージャがのリモート インスタンス上の変更を行うかどうか[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]変更をロールバックすることはできません。 リモート プロシージャはトランザクションにはかかわりません。  
  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]が .NET Framework でオーバーロードされるときに正しいメソッドを参照するようにするには、EXTERNAL NAME 句で指定されるメソッドに以下の特性が必要です。  
  
-   静的メソッドとして宣言される。  
  
-   プロシージャのパラメーター数と同じ数のパラメーターを受け取る。  
  
-   [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] プロシージャの対応するパラメーターのデータ型と互換性のあるパラメーター型を使用する。 一致については[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]データ型を[!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]データ型を参照してください[CLR パラメーター データのマッピング](../../relational-databases/clr-integration-database-objects-types-net-framework/mapping-clr-parameter-data.md)です。  
  
## <a name="metadata"></a>メタデータ  
 次の表に、ストアド プロシージャに関する情報を返すために使用できるカタログ ビューおよび動的管理ビューを示します。  
  
|表示|Description|  
|----------|-----------------|  
|[sys.sql_modules](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)|[!INCLUDE[tsql](../../includes/tsql-md.md)] プロシージャの定義を返します。 使用して暗号化オプションで作成されたプロシージャのテキストを表示することはできません、 **sys.sql_modules**カタログ ビューです。|  
|[sys.assembly_modules](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)|CLR プロシージャに関する情報を返します。|  
|[sys.parameters](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)|プロシージャで定義されているパラメーターに関する情報を返します。|  
|[sys.sql_expression_dependencies](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md) [sys.dm_sql_referenced_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md) [sys.dm_sql_referencing_entities](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)|プロシージャによって参照されるオブジェクトを返します。|  
  
 コンパイル後のプロシージャのサイズを予測するには、次のパフォーマンス モニター カウンターを使用します。  
  
|パフォーマンス モニター オブジェクト名|パフォーマンス モニター カウンター名|  
|-------------------------------------|--------------------------------------|  
|SQLServer: Plan Cache オブジェクト|Cache Hit Ratio|  
||Cache Pages|  
||Cache Object Counts*|  
  
 * アドホック [!INCLUDE[tsql](../../includes/tsql-md.md)]、準備された [!INCLUDE[tsql](../../includes/tsql-md.md)]、プロシージャ、トリガーなど、キャッシュ オブジェクトの種類別にオブジェクトの数を調べることができます。 詳細については、次を参照してください。 [SQL Server、プランのキャッシュ オブジェクト](../../relational-databases/performance-monitor/sql-server-plan-cache-object.md)です。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 必要があります**CREATE PROCEDURE** 、データベースの権限と**ALTER**プロシージャでは、作成中またはメンバーシップが必要です、スキーマに対する権限、 **db_ddladmin**固定データベース ロール。  
  
 CLR ストアド プロシージャの場合は、EXTERNAL NAME 句で参照されるアセンブリの所有権が必要ですか**参照**そのアセンブリに対する権限。  
  
##  <a name="mot"></a>CREATE PROCEDURE とメモリ最適化テーブル  
 メモリ最適化テーブルは、ネイティブ コンパイル、従来のストアド プロシージャからアクセスできます。 ネイティブ プロシージャより効率的な方法で、ほとんどの場合です。
詳細については、次を参照してください。 [Natively Compiled Stored Procedures](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)です。  
  
 次の例は、メモリ最適化テーブルにアクセスするネイティブ コンパイル ストアド プロシージャを作成する方法を示しています`dbo.Departments`:。  
  
```sql  
CREATE PROCEDURE dbo.usp_add_kitchen @dept_id int, @kitchen_count int NOT NULL  
WITH EXECUTE AS OWNER, SCHEMABINDING, NATIVE_COMPILATION  
AS  
BEGIN ATOMIC WITH (TRANSACTION ISOLATION LEVEL = SNAPSHOT, LANGUAGE = N'us_english')  
  
  UPDATE dbo.Departments  
  SET kitchen_count = ISNULL(kitchen_count, 0) + @kitchen_count  
  WHERE id = @dept_id  
END;  
GO  
```  
  
 NATIVE_COMPILATION なしで作成されたプロシージャをネイティブ コンパイル ストアド プロシージャに変更することはできません。 
  
 ネイティブ コンパイル ストアド プロシージャでのプログラミング機能の詳細については、クエリのセキュリティをサポートし、演算子を参照してください[ネイティブ コンパイル T-SQL モジュールでサポートされる機能](../../relational-databases/in-memory-oltp/supported-features-for-natively-compiled-t-sql-modules.md)します。  
  
## <a name="Examples"></a> 使用例  
  
|カテゴリ|主な構文要素|  
|--------------|------------------------------|  
|[基本構文](#BasicSyntax)|CREATE PROCEDURE|  
|[パラメーターの引き渡し](#Parameters)|@parameter <br> &nbsp;&nbsp;• 既定値 = <br> &nbsp;&nbsp;• 出力 <br> &nbsp;&nbsp;• テーブル値パラメーターの型 <br> &nbsp;&nbsp;• CURSOR VARYING|  
|[ストアド プロシージャを使用したデータの変更](#Modify)|UPDATE|  
|[エラー処理](#Error)|TRY しています.CATCH|  
|[プロシージャの定義の難読化](#Encrypt)|WITH ENCRYPTION|  
|[再コンパイルするプロシージャの強制](#Recompile)|WITH RECOMPILE|  
|[セキュリティ コンテキストの設定](#Security)|EXECUTE AS|  
  
###  <a name="BasicSyntax"></a>基本構文  
 このセクションの例では、最低限必要な構文を使用して  CREATE PROCEDURE ステートメントの基本機能を示します。  
  
#### <a name="a-creating-a-simple-transact-sql-procedure"></a>A. 単純な Transact-SQL プロシージャを作成する  
 次の例は、全従業員 (フルネーム) とその役職および部署名を、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)] データベースのビューから返すストアド プロシージャを作成します。 このプロシージャではパラメーターを使用しません。 その後、3 つのメソッドを使用してプロシージャを実行します。  
  
```sql  
CREATE PROCEDURE HumanResources.uspGetAllEmployees  
AS  
    SET NOCOUNT ON;  
    SELECT LastName, FirstName, JobTitle, Department  
    FROM HumanResources.vEmployeeDepartment;  
GO  
  
SELECT * FROM HumanResources.vEmployeeDepartment;  
```  
  
 `uspGetEmployees`プロシージャは、次の方法で実行できます。  
  
```sql  
EXECUTE HumanResources.uspGetAllEmployees;  
GO  
-- Or  
EXEC HumanResources.uspGetAllEmployees;  
GO  
-- Or, if this procedure is the first statement within a batch:  
HumanResources.uspGetAllEmployees;  
```  
  
#### <a name="b-returning-more-than-one-result-set"></a>B. 複数の結果セットを返す  
 次のプロシージャでは、2 つの結果セットが返されます。  
  
```sql  
CREATE PROCEDURE dbo.uspMultipleResults   
AS  
SELECT TOP(10) BusinessEntityID, Lastname, FirstName FROM Person.Person;  
SELECT TOP(10) CustomerID, AccountNumber FROM Sales.Customer;  
GO  
```  
  
#### <a name="c-creating-a-clr-stored-procedure"></a>C. CLR ストアド プロシージャを作成する  
 次の例を作成、`GetPhotoFromDB`を参照するプロシージャ、`GetPhotoFromDB`のメソッド、`LargeObjectBinary`クラス内で、`HandlingLOBUsingCLR`アセンブリ。 プロシージャが作成される前に、`HandlingLOBUsingCLR`ローカル データベースにアセンブリを登録します。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、 [!INCLUDE[sqldbesa](../../includes/sqldbesa-md.md)] (から作成されたアセンブリを使用して場合*assembly_bits です。*  
  
```sql  
CREATE ASSEMBLY HandlingLOBUsingCLR  
FROM '\\MachineName\HandlingLOBUsingCLR\bin\Debug\HandlingLOBUsingCLR.dll';  
GO  
CREATE PROCEDURE dbo.GetPhotoFromDB  
(  
    @ProductPhotoID int,  
    @CurrentDirectory nvarchar(1024),  
    @FileName nvarchar(1024)  
)  
AS EXTERNAL NAME HandlingLOBUsingCLR.LargeObjectBinary.GetPhotoFromDB;  
GO  
```  
  
###  <a name="Parameters"></a>パラメーターの引き渡し  
 このセクションの例では、入力パラメーターと出力パラメーターを使用してストアド プロシージャ間で値を受け渡す方法を示します。  
  
#### <a name="d-creating-a-procedure-with-input-parameters"></a>D. 入力パラメーターを使用したプロシージャを作成する  
 次の例では、特定の 1 人の従業員の姓と名の値を渡すことで、その従業員に関する情報を返すストアド プロシージャを作成します。 このプロシージャは、渡されたパラメーターと完全に一致するものだけを受け入れます。  
  
```sql  
IF OBJECT_ID ( 'HumanResources.uspGetEmployees', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetEmployees;  
GO  
CREATE PROCEDURE HumanResources.uspGetEmployees   
    @LastName nvarchar(50),   
    @FirstName nvarchar(50)   
AS   
  
    SET NOCOUNT ON;  
    SELECT FirstName, LastName, JobTitle, Department  
    FROM HumanResources.vEmployeeDepartment  
    WHERE FirstName = @FirstName AND LastName = @LastName;  
GO  
  
```  
  
 `uspGetEmployees`プロシージャは、次の方法で実行できます。  
  
```  
EXECUTE HumanResources.uspGetEmployees N'Ackerman', N'Pilar';  
-- Or  
EXEC HumanResources.uspGetEmployees @LastName = N'Ackerman', @FirstName = N'Pilar';  
GO  
-- Or  
EXECUTE HumanResources.uspGetEmployees @FirstName = N'Pilar', @LastName = N'Ackerman';  
GO  
-- Or, if this procedure is the first statement within a batch:  
HumanResources.uspGetEmployees N'Ackerman', N'Pilar';  
  
```  
  
#### <a name="e-using-a-procedure-with-wildcard-parameters"></a>E. ワイルドカード パラメーターを含むプロシージャを使用する  
 次の例では、従業員の姓と名を表す値のすべてまたは一部を渡して従業員に関する情報を返すストアド プロシージャを作成します。 この手順のパターンは、渡されたパラメーターを一致するか、指定されていない場合は、既定のプリセットを使用して (最後の文字で始まる名前`D`)。  
  
```sql  
IF OBJECT_ID ( 'HumanResources.uspGetEmployees2', 'P' ) IS NOT NULL   
    DROP PROCEDURE HumanResources.uspGetEmployees2;  
GO  
CREATE PROCEDURE HumanResources.uspGetEmployees2   
    @LastName nvarchar(50) = N'D%',   
    @FirstName nvarchar(50) = N'%'  
AS   
    SET NOCOUNT ON;  
    SELECT FirstName, LastName, JobTitle, Department  
    FROM HumanResources.vEmployeeDepartment  
    WHERE FirstName LIKE @FirstName AND LastName LIKE @LastName;  
```  
  
 `uspGetEmployees2`プロシージャは、多くの組み合わせで実行できます。 ここでは、一部の組み合わせのみを示します。  
  
```sql  
EXECUTE HumanResources.uspGetEmployees2;  
-- Or  
EXECUTE HumanResources.uspGetEmployees2 N'Wi%';  
-- Or  
EXECUTE HumanResources.uspGetEmployees2 @FirstName = N'%';  
-- Or  
EXECUTE HumanResources.uspGetEmployees2 N'[CK]ars[OE]n';  
-- Or  
EXECUTE HumanResources.uspGetEmployees2 N'Hesse', N'Stefen';  
-- Or  
EXECUTE HumanResources.uspGetEmployees2 N'H%', N'S%';  
```  
  
#### <a name="f-using-output-parameters"></a>F. 出力パラメーターを使用します。  
 次の例を作成、`uspGetList`プロシージャです。 このプロシージャは、指定の価格以下の製品の一覧を返します。 この例を使用して複数`SELECT`ステートメントと複数`OUTPUT`パラメーター。 OUTPUT パラメーターを使用すると、プロシージャの実行中に、外部プロシージャ、バッチ、または複数の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントから、値セットにアクセスできます。  
  
```sql  
IF OBJECT_ID ( 'Production.uspGetList', 'P' ) IS NOT NULL   
    DROP PROCEDURE Production.uspGetList;  
GO  
CREATE PROCEDURE Production.uspGetList @Product varchar(40)   
    , @MaxPrice money   
    , @ComparePrice money OUTPUT  
    , @ListPrice money OUT  
AS  
    SET NOCOUNT ON;  
    SELECT p.[Name] AS Product, p.ListPrice AS 'List Price'  
    FROM Production.Product AS p  
    JOIN Production.ProductSubcategory AS s   
      ON p.ProductSubcategoryID = s.ProductSubcategoryID  
    WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice;  
-- Populate the output variable @ListPprice.  
SET @ListPrice = (SELECT MAX(p.ListPrice)  
        FROM Production.Product AS p  
        JOIN  Production.ProductSubcategory AS s   
          ON p.ProductSubcategoryID = s.ProductSubcategoryID  
        WHERE s.[Name] LIKE @Product AND p.ListPrice < @MaxPrice);  
-- Populate the output variable @compareprice.  
SET @ComparePrice = @MaxPrice;  
GO  
```  
  
 `uspGetList` を実行し、`$700` より安い [!INCLUDE[ssSampleDBCoShort](../../includes/sssampledbcoshort-md.md)] 製品 (バイク) の一覧を返します。 `OUTPUT`パラメーター`@Cost`と`@ComparePrices`内のメッセージを返すにはフロー制御言語と共に使用、**メッセージ**ウィンドウです。  
  
> [!NOTE]  
>  OUTPUT 変数は、プロシージャの作成時と変数の使用時に定義する必要があります。 パラメーター名と変数名は一致はありません。ただし、データ型とパラメーターの位置する必要があります一致しない限り、 `@ListPrice`  = *変数*を使用します。  
  
```sql  
DECLARE @ComparePrice money, @Cost money ;  
EXECUTE Production.uspGetList '%Bikes%', 700,   
    @ComparePrice OUT,   
    @Cost OUTPUT  
IF @Cost <= @ComparePrice   
BEGIN  
    PRINT 'These products can be purchased for less than   
    $'+RTRIM(CAST(@ComparePrice AS varchar(20)))+'.'  
END  
ELSE  
    PRINT 'The prices for all products in this category exceed   
    $'+ RTRIM(CAST(@ComparePrice AS varchar(20)))+'.';  
```  
  
 次に結果セットの一部を示します。  
  
 ```   
 Product                     List Price  
 --------------------------  ----------  
 Road-750 Black, 58          539.99  
 Mountain-500 Silver, 40     564.99  
 Mountain-500 Silver, 42     564.99  
 ...  
 Road-750 Black, 48          539.99  
 Road-750 Black, 52          539.99  
   
 (14 row(s) affected)   
  
 These items can be purchased for less than $700.00.
 ```  
  
#### <a name="g-using-a-table-valued-parameter"></a>G. テーブル値パラメーターを使用する  
 次の例では、テーブル値パラメーターの型を使用して、テーブルに複数の行を挿入します。 さらに、パラメーターの型を作成して、その型を参照するテーブル変数を宣言し、パラメーター一覧を入力して値をストアド プロシージャに渡します。 このストアド プロシージャでは、値を使用してテーブルに複数の行を挿入します。  
  
```sql  
/* Create a table type. */  
CREATE TYPE LocationTableType AS TABLE   
( LocationName VARCHAR(50)  
, CostRate INT );  
GO  
  
/* Create a procedure to receive data for the table-valued parameter. */  
CREATE PROCEDURE usp_InsertProductionLocation  
    @TVP LocationTableType READONLY  
    AS   
    SET NOCOUNT ON  
    INSERT INTO [AdventureWorks2012].[Production].[Location]  
           ([Name]  
           ,[CostRate]  
           ,[Availability]  
           ,[ModifiedDate])  
        SELECT *, 0, GETDATE()  
        FROM  @TVP;  
GO  
  
/* Declare a variable that references the type. */  
DECLARE @LocationTVP   
AS LocationTableType;  
  
/* Add data to the table variable. */  
INSERT INTO @LocationTVP (LocationName, CostRate)  
    SELECT [Name], 0.00  
    FROM   
    [AdventureWorks2012].[Person].[StateProvince];  
  
/* Pass the table variable data to a stored procedure. */  
EXEC usp_InsertProductionLocation @LocationTVP;  
GO  
```  
  
##### <a name="h-using-an-output-cursor-parameter"></a>H. OUTPUT カーソル パラメーターを使用する  
 次の例では、OUTPUT カーソル パラメーターを使用して、プロシージャに対してローカルになっているカーソルを、呼び出し側のバッチ、プロシージャ、またはトリガーに戻します。  
  
 最初に、宣言し、カーソルをオープンするプロシージャを作成、`Currency`テーブル。  
  
```sql  
CREATE PROCEDURE dbo.uspCurrencyCursor   
    @CurrencyCursor CURSOR VARYING OUTPUT  
AS  
    SET NOCOUNT ON;  
    SET @CurrencyCursor = CURSOR  
    FORWARD_ONLY STATIC FOR  
      SELECT CurrencyCode, Name  
      FROM Sales.Currency;  
    OPEN @CurrencyCursor;  
GO  
```  
  
 次に、ローカル カーソル変数を宣言し、ローカル変数にカーソルを割り当てるプロシージャを実行した後、カーソルから行を取り出すバッチを実行します。  
  
```sql  
DECLARE @MyCursor CURSOR;  
EXEC dbo.uspCurrencyCursor @CurrencyCursor = @MyCursor OUTPUT;  
WHILE (@@FETCH_STATUS = 0)  
BEGIN;  
     FETCH NEXT FROM @MyCursor;  
END;  
CLOSE @MyCursor;  
DEALLOCATE @MyCursor;  
GO  
```  
  
###  <a name="Modify"></a>ストアド プロシージャを使用して、データの変更  
 このセクションの例では、プロシージャの定義にデータ操作言語 (DML) ステートメントを含めることで、テーブルまたはビューのデータを挿入または変更する方法を示します。  
  
#### <a name="i-using-update-in-a-stored-procedure"></a>I. UPDATE をストアド プロシージャで使用する  
 次の例では、UPDATE ステートメントをストアド プロシージャで使用しています。 このプロシージャは、1 つの入力パラメーター`@NewHours`と 1 つの出力パラメーター`@RowCount`です。 `@NewHours`パラメーターの値が列を更新する UPDATE ステートメントで使用される`VacationHours`表内の`HumanResources.Employee`します。 `@RowCount`をローカル変数に影響を受ける行の数を返す出力パラメーターを使用します。 `VacationHours` に設定する値は、SET 句で CASE 式を使用して条件に応じて決定しています。 ときに、従業員給与が時給ベース (`SalariedFlag` = 0)、`VacationHours`で指定された値の合計時間の現在の数に設定されている`@NewHours`、それ以外の`VacationHours`で指定された値に設定されている`@NewHours`です。  
  
```sql  
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
  
###  <a name="Error"></a>エラー処理  
 このセクションの例では、ストアド プロシージャの実行時に発生する可能性のあるエラーの処理方法を示します。  
  
#### <a name="j-using-trycatch"></a>J. TRY...CATCH の使用  
 この例では、TRY...CATCH 構造を使用して、ストアド プロシージャの実行中にキャッチしたエラーの情報を返します。  
  
```sql  
CREATE PROCEDURE Production.uspDeleteWorkOrder ( @WorkOrderID int )  
AS  
SET NOCOUNT ON;  
BEGIN TRY  
   BEGIN TRANSACTION   
   -- Delete rows from the child table, WorkOrderRouting, for the specified work order.  
   DELETE FROM Production.WorkOrderRouting  
   WHERE WorkOrderID = @WorkOrderID;  
  
   -- Delete the rows from the parent table, WorkOrder, for the specified work order.  
   DELETE FROM Production.WorkOrder  
   WHERE WorkOrderID = @WorkOrderID;  
  
   COMMIT  
  
END TRY  
BEGIN CATCH  
  -- Determine if an error occurred.  
  IF @@TRANCOUNT > 0  
     ROLLBACK  
  
  -- Return the error information.  
  DECLARE @ErrorMessage nvarchar(4000),  @ErrorSeverity int;  
  SELECT @ErrorMessage = ERROR_MESSAGE(),@ErrorSeverity = ERROR_SEVERITY();  
  RAISERROR(@ErrorMessage, @ErrorSeverity, 1);  
END CATCH;  
  
GO  
EXEC Production.uspDeleteWorkOrder 13;  
  
/* Intentionally generate an error by reversing the order in which rows 
   are deleted from the parent and child tables. This change does not 
   cause an error when the procedure definition is altered, but produces 
   an error when the procedure is executed.  
*/  
ALTER PROCEDURE Production.uspDeleteWorkOrder ( @WorkOrderID int )  
AS  
  
BEGIN TRY  
   BEGIN TRANSACTION   
      -- Delete the rows from the parent table, WorkOrder, for the specified work order.  
   DELETE FROM Production.WorkOrder  
   WHERE WorkOrderID = @WorkOrderID;  
  
   -- Delete rows from the child table, WorkOrderRouting, for the specified work order.  
   DELETE FROM Production.WorkOrderRouting  
   WHERE WorkOrderID = @WorkOrderID;  
  
   COMMIT TRANSACTION  
  
END TRY  
BEGIN CATCH  
  -- Determine if an error occurred.  
  IF @@TRANCOUNT > 0  
     ROLLBACK TRANSACTION  
  
  -- Return the error information.  
  DECLARE @ErrorMessage nvarchar(4000),  @ErrorSeverity int;  
  SELECT @ErrorMessage = ERROR_MESSAGE(),@ErrorSeverity = ERROR_SEVERITY();  
  RAISERROR(@ErrorMessage, @ErrorSeverity, 1);  
END CATCH;  
GO  
-- Execute the altered procedure.  
EXEC Production.uspDeleteWorkOrder 15;  
  
DROP PROCEDURE Production.uspDeleteWorkOrder;  
```  
  
###  <a name="Encrypt"></a>プロシージャの定義の難読化  
 このセクションの例では、ストアド プロシージャの定義を難読化する方法を示します。  
  
#### <a name="k-using-the-with-encryption-option"></a>K. WITH ENCRYPTION オプションを使用する  
 次の例を作成、`HumanResources.uspEncryptThis`プロシージャです。  
  
**適用されます**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]、SQL データベースです。  
  
```sql  
CREATE PROCEDURE HumanResources.uspEncryptThis  
WITH ENCRYPTION  
AS  
    SET NOCOUNT ON;  
    SELECT BusinessEntityID, JobTitle, NationalIDNumber, 
        VacationHours, SickLeaveHours   
    FROM HumanResources.Employee;  
GO  
```  
  
 `WITH ENCRYPTION`オプションの次の例で示すようにシステム カタログに対するクエリまたはメタデータを使用して次のように機能するときに、プロシージャの定義を難読化します。  
  
 Run `sp_helptext`:  
  
```sql  
EXEC sp_helptext 'HumanResources.uspEncryptThis';  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 `The text for object 'HumanResources.uspEncryptThis' is encrypted.`  
  
 直接クエリを実行、`sys.sql_modules`カタログ ビュー。  
  
```sql  
SELECT definition FROM sys.sql_modules  
WHERE object_id = OBJECT_ID('HumanResources.uspEncryptThis');  
```  
  
 [!INCLUDE[ssResult](../../includes/ssresult-md.md)]  
  
 ```  
 definition  
 --------------------------------  
 NULL  
 ```  
  
###  <a name="Recompile"></a>再コンパイルするプロシージャの強制  
 このセクションの例では、WITH RECOMPILE 句を使用して、プロシージャを実行するたびに再コンパイルするように強制します。  
  
#### <a name="l-using-the-with-recompile-option"></a>L. WITH RECOMPILE オプションを使用する  
 `WITH RECOMPILE`句は、プロシージャに指定されたパラメーターは通常、使用されない場合と、新しい実行プランをキャッシュしたりしないでメモリに格納されている場合に役立ちます。  
  
```sql  
IF OBJECT_ID ( 'dbo.uspProductByVendor', 'P' ) IS NOT NULL   
    DROP PROCEDURE dbo.uspProductByVendor;  
GO  
CREATE PROCEDURE dbo.uspProductByVendor @Name varchar(30) = '%'  
WITH RECOMPILE  
AS  
    SET NOCOUNT ON;  
    SELECT v.Name AS 'Vendor name', p.Name AS 'Product name'  
    FROM Purchasing.Vendor AS v   
    JOIN Purchasing.ProductVendor AS pv   
      ON v.BusinessEntityID = pv.BusinessEntityID   
    JOIN Production.Product AS p   
      ON pv.ProductID = p.ProductID  
    WHERE v.Name LIKE @Name;  
```  
  
###  <a name="Security"></a>セキュリティ コンテキストの設定  
 このセクションの例では、EXECUTE AS 句を使用して、ストアド プロシージャが実行されるセキュリティ コンテキストを設定します。  
  
#### <a name="m-using-the-execute-as-clause"></a>M. EXECUTE AS 句を使用する  
 次の例を使用して、 [EXECUTE AS](../../t-sql/statements/execute-as-clause-transact-sql.md)句を手順を実行できるセキュリティ コンテキストを指定します。 例では、オプションで`CALLER`を呼び出したユーザーのコンテキストでプロシージャを実行できることを指定します。  
  
```sql  
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
  
#### <a name="n-creating-custom-permission-sets"></a>N. カスタム権限セットを作成する  
 次の例では、EXECUTE AS を使用して、データベース操作に対するカスタム権限を作成します。 TRUNCATE TABLE など、許可できる権限のない操作もあります。 TRUNCATE TABLE ステートメントをストアド プロシージャ内に組み込み、テーブルを変更する権限が許可されているユーザーとしてそのプロシージャを実行するように指定すると、テーブルの切り捨てを行うための権限を、そのプロシージャの EXECUTE 権限が許可されたユーザーに拡張できます。  
  
```sql  
CREATE PROCEDURE dbo.TruncateMyTable  
WITH EXECUTE AS SELF  
AS TRUNCATE TABLE MyDB..MyTable;  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
  
### <a name="o-create-a-stored-procedure-that-runs-a-select-statement"></a>O.  SELECT ステートメントを実行するストアド プロシージャの作成します。  
 この例では、作成して、プロシージャを実行するための基本構文を使用します。 バッチを実行する場合、プロシージャの作成は最初のステートメントをする必要があります。 たとえば、次を作成するストアド プロシージャ[!INCLUDE[ssawPDW](../../includes/ssawpdw-md.md)]データベース コンテキストが最初に、設定、および CREATE PROCEDURE ステートメントを実行します。  
  
```sql  
-- Uses AdventureWorksDW database  
  
--Run CREATE PROCEDURE as the first statement in a batch.  
CREATE PROCEDURE Get10TopResellers   
AS   
BEGIN  
    SELECT TOP (10) r.ResellerName, r.AnnualSales  
    FROM DimReseller AS r  
    ORDER BY AnnualSales DESC, ResellerName ASC;  
END  
;  
  
--Show 10 Top Resellers  
EXEC Get10TopResellers;  
```  
  
## <a name="see-also"></a>参照  
 [ALTER PROCEDURE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-procedure-transact-sql.md)   
 [フロー制御言語 & #40 です。TRANSACT-SQL と #41 です。](~/t-sql/language-elements/control-of-flow.md)   
 [カーソル](../../relational-databases/cursors.md)   
 [データ型 &#40;Transact-SQL&#41;](../../t-sql/data-types/data-types-transact-sql.md)   
 [DECLARE @local_variable &#40;Transact-SQL&#41;](../../t-sql/language-elements/declare-local-variable-transact-sql.md)   
 [DROP PROCEDURE &#40;TRANSACT-SQL と #41 です。](../../t-sql/statements/drop-procedure-transact-sql.md)   
 [EXECUTE &#40;Transact-SQL&#41;](../../t-sql/language-elements/execute-transact-sql.md)   
 [実行 AS (& a) #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-transact-sql.md)   
 [ストアド プロシージャ &#40;データベース エンジン&#41;](../../relational-databases/stored-procedures/stored-procedures-database-engine.md)   
 [sp_procoption & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-procoption-transact-sql.md)   
 [sp_recompile & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-recompile-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.parameters &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-parameters-transact-sql.md)   
 [sys.procedures &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-procedures-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.numbered_procedures & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-numbered-procedures-transact-sql.md)   
 [sys.numbered_procedure_parameters & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-numbered-procedure-parameters-transact-sql.md)   
 [OBJECT_DEFINITION &#40;Transact-SQL&#41;](../../t-sql/functions/object-definition-transact-sql.md)   
 [ストアド プロシージャの作成](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [使用してテーブル値パラメーター (&) #40; データベース エンジン"&"#41;](../../relational-databases/tables/use-table-valued-parameters-database-engine.md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)  
  
  





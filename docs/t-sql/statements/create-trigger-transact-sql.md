---
title: "CREATE TRIGGER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 08/10/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- CREATE TRIGGER
- TRIGGER
- CREATE_TRIGGER_TSQL
- TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- recursive DML triggers [SQL Server]
- CREATE TRIGGER statement
- multiple triggers
- deferred name resolution, DML triggers
- DML triggers, creating
- nested triggers
- server-scoped triggers
- DDL triggers, creating
- triggers [SQL Server], creating
- database-scoped triggers [SQL Server]
ms.assetid: edeced03-decd-44c3-8c74-2c02f801d3e7
caps.latest.revision: 140
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Active
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 56011e892d5fbc5862f3d7c279bc297c3d0ac04c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-trigger-transact-sql"></a>CREATE TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  DML トリガー、DDL トリガー、またはログオン トリガーを作成します。 トリガーとは、特殊な種類のストアド プロシージャであり、データベース サーバーでイベントが発生したときに自動的に実行されます。 DML トリガーは、ユーザーがデータ操作言語 (DML) イベントを介してデータを変更しようとしたときに実行されます。 DML イベントは、テーブルやビューに対する INSERT、UPDATE、または DELETE ステートメントによって発生するイベントです。 これらのトリガーは、テーブル行が影響を受けるかどうかにかかわらず、有効なイベントが発生したときに起動されます。 詳しくは、「 [DML Triggers](../../relational-databases/triggers/dml-triggers.md)」をご覧ください。  
  
 DDL トリガーは、さまざまなデータ定義言語 (DDL) イベントに対応して実行されます。 これらのイベントは、主に対応して[!INCLUDE[tsql](../../includes/tsql-md.md)]CREATE、ALTER、および DROP ステートメント、および DDL と同様の操作を実行する特定のシステム ストアド プロシージャです。 ログオン トリガーは、ユーザー セッションの確立時に発生する LOGON イベントに応答して起動されます。 直接トリガーを作成することができます[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント内に作成されるアセンブリのメソッドから、または、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]共通言語ランタイム (CLR) のインスタンスにアップロードし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、特定のステートメントに対して複数のトリガーを作成できます。  
  
> [!IMPORTANT]  
>  上位の特権の下では、トリガー内の悪意のあるコードを実行できます。 この脅威を緩和する方法の詳細については、次を参照してください。[トリガーのセキュリティの管理](../../relational-databases/triggers/manage-trigger-security.md)です。  
  
> [!NOTE]  
>  SQL Server への .NET Framework CLR の統合はこのトピックで説明します。 CLR 統合は、Azure SQL Database には適用されません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- SQL Server Syntax  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table | view }   
[ WITH <dml_trigger_option> [ ,...n ] ]  
{ FOR | AFTER | INSTEAD OF }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
[ WITH APPEND ]  
[ NOT FOR REPLICATION ]   
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME <method specifier [ ; ] > }  
  
<dml_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
  
```  
  
```  
-- SQL Server Syntax  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a 
-- table (DML Trigger on memory-optimized tables)  
  
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table }   
[ WITH <dml_trigger_option> [ ,...n ] ]  
{ FOR | AFTER }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
AS { sql_statement  [ ; ] [ ,...n ] }  
  
<dml_trigger_option> ::=  
    [ NATIVE_COMPILATION ]  
    [ SCHEMABINDING ]  
    [ EXECUTE AS Clause ]  
  
```  
  
```  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, 
-- REVOKE or UPDATE statement (DDL Trigger)  
  
CREATE [ OR ALTER ] TRIGGER trigger_name   
ON { ALL SERVER | DATABASE }   
[ WITH <ddl_trigger_option> [ ,...n ] ]  
{ FOR | AFTER } { event_type | event_group } [ ,...n ]  
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME < method specifier >  [ ; ] }  
  
<ddl_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
```  
  
```  
-- Trigger on a LOGON event (Logon Trigger)  
  
CREATE [ OR ALTER ] TRIGGER trigger_name   
ON ALL SERVER   
[ WITH <logon_trigger_option> [ ,...n ] ]  
{ FOR| AFTER } LOGON    
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME < method specifier >  [ ; ] }  
  
<logon_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
```  
  
## <a name="syntax"></a>構文  
  
```  
-- Windows Azure SQL Database Syntax   
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  
  
CREATE [ OR ALTER ] TRIGGER [ schema_name . ]trigger_name   
ON { table | view }   
 [ WITH <dml_trigger_option> [ ,...n ] ]   
{ FOR | AFTER | INSTEAD OF }   
{ [ INSERT ] [ , ] [ UPDATE ] [ , ] [ DELETE ] }   
  AS { sql_statement  [ ; ] [ ,...n ] [ ; ] > }  
  
<dml_trigger_option> ::=   
        [ EXECUTE AS Clause ]  
  
```  
  
```  
-- Windows Azure SQL Database Syntax  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, 
-- REVOKE, or UPDATE STATISTICS statement (DDL Trigger)   
  
CREATE [ OR ALTER ] TRIGGER trigger_name   
ON { DATABASE }   
 [ WITH <ddl_trigger_option> [ ,...n ] ]   
{ FOR | AFTER } { event_type | event_group } [ ,...n ]   
AS { sql_statement  [ ; ] [ ,...n ]  [ ; ] }  
  
<ddl_trigger_option> ::=   
    [ EXECUTE AS Clause ]  
```  
  
## <a name="arguments"></a>引数
または変更  
 **適用されます**: Azure [!INCLUDE[ssSDS](../../includes/sssds-md.md)]、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] (以降で[!INCLUDE[ssSQL15](../../includes/sssql15-md.md)]SP1)。 
  
 条件付きでは既に存在する場合にのみ、トリガーを変更します。 
  
 *schema_name*  
 DML トリガーが属しているスキーマの名前を指定します。 DML トリガーのスコープは、そのトリガーが作成されたテーブルまたはビューのスキーマです。 *schema_name* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
 *trigger_name*  
 トリガーの名前を指定します。 A *trigger_name* 、規則に従う必要があります[識別子](../../relational-databases/databases/database-identifiers.md)する点を除いて、 *trigger_name*できません先頭に # または ## します。  
  
 *テーブル* | *ビュー*  
 DML トリガーを実行するテーブルまたはビューを指定します。これらはトリガー テーブルまたはトリガー ビューとも呼ばれます。 テーブルまたはビューの完全修飾名の指定は省略可能です。 ビューは INSTEAD OF トリガーでのみ参照できます。 DML トリガーは、ローカルまたはグローバルの一時テーブルに対しては定義できません。  
  
 DATABASE  
 DDL トリガーのスコープを現在のデータベースに適用します。 指定すると、トリガーが起動するたびに*event_type*または*event_group*現在のデータベースで発生します。  
  
 ALL SERVER  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 DDL トリガーまたはログオン トリガーのスコープを現在のサーバーに適用します。 指定すると、トリガーが起動するたびに*event_type*または*event_group*現在のサーバーで任意の場所が発生します。  
  
 WITH ENCRYPTION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 CREATE TRIGGER ステートメントのテキストを暗号化します。 WITH ENCRYPTION を使用してでは、トリガーがの一部としてパブリッシュされない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション。 WITH ENCRYPTION は、CLR トリガーに対しては指定できません。  
  
 EXECUTE AS  
 トリガーを実行するセキュリティ コンテキストを指定します。 これにより、トリガーが参照するデータベース オブジェクトの権限を検証するときに、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] インスタンスが使用するユーザー アカウントを制御できます。  
  
 このオプションは、メモリ最適化テーブルのトリガーに必要です。  
  
 詳細については、次を参照してください。[EXECUTE AS 句 & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/execute-as-clause-transact-sql.md).  
  
 NATIVE_COMPILATION  
 トリガーをネイティブでコンパイルすることを示します。  
  
 このオプションは、メモリ最適化テーブルのトリガーに必要です。  
  
 SCHEMABINDING  
 トリガーによって参照されているテーブルを削除または変更できないことを確認します。  
  
 このオプションは、メモリ最適化テーブルのトリガーに必要なは、従来のテーブルのトリガーはサポートされていません。  
  
 FOR | AFTER   
 AFTER を指定した場合は、トリガー元の SQL ステートメントで指定したすべての処理が正常に実行された場合のみ、DML トリガーが起動されます。 このトリガーの実行前には、連鎖して行われるすべての参照操作と制約チェックも完了している必要があります。  
  
 指定したキーワードが FOR だけの場合は、AFTER が既定値になります。  
  
 AFTER トリガーは、ビューに対しては定義できません。  
  
 INSTEAD OF  
 DML トリガーを実行することを指定*の代わりに*そのため、SQL ステートメントをトリガーする、トリガーを起動するステートメントの操作をオーバーライドします。 DDL トリガーまたはログオン トリガーでは INSTEAD OF を指定できません。  
  
 テーブルまたはビューでは、INSERT、UPDATE、または DELETE の各ステートメントに定義できる INSTEAD OF トリガーは 1 つだけですが、 ビューに別のビューを作成して、各ビューに独自の INSTEAD OF トリガーを定義することは可能です。  
  
 INSTEAD OF トリガーは、WITH CHECK OPTION を使用する更新可能なビューでは使用できません。 WITH CHECK OPTION が指定されている更新可能なビューに INSTEAD OF トリガーを追加した場合、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ではエラーが発生します。 ユーザーは、INSTEAD OF トリガーを定義する前に、ALTER VIEW を使用して WITH CHECK OPTION を削除する必要があります。  
  
 { [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
 テーブルまたはビューに対して DML トリガーが試行されたとき、そのトリガーを有効にするデータ変更ステートメントを指定します。 少なくとも 1 つのオプションを指定する必要があります。 これらのオプションは、トリガー定義において、どのような順序や組み合わせでも指定できます。  
  
 INSTEAD OF トリガーの場合、目的のテーブルに連鎖的な ON DELETE 参照操作を指定している参照関係があるときは、DELETE オプションを指定できません。 同様に、目的のテーブルに ON UPDATE 連鎖参照操作を指定している参照関係があるときは、UPDATE オプションを指定できません。  
  
 WITH APPEND  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssKilimanjaro](../../includes/sskilimanjaro-md.md)]  
  
 既存のトリガーに対して、新しいトリガーを追加します。 WITH APPEND は、INSTEAD OF トリガーと共に使用したり、AFTER トリガーが明示的に指定されている場合は使用できません。 旧バージョンとの互換性上の理由から、WITH APPEND を使用できるのは、FOR が指定されている場合 (INSTEAD OF と AFTER のどちらも指定されていない場合) だけです。 WITH APPEND は、EXTERNAL NAME が指定されている場合、つまり、トリガーが CLR トリガーの場合は指定できません。  
  
 *event_type*  
 名前を指定、[!INCLUDE[tsql](../../includes/tsql-md.md)]言語イベントを実行後、DDL トリガーを起動します。 DDL トリガーの有効なイベントは、「 [DDL イベント](../../relational-databases/triggers/ddl-events.md)です。  
  
 *event_group*  
 定義済みグループの名前を指定[!INCLUDE[tsql](../../includes/tsql-md.md)]言語イベントです。 任意の実行後に、DDL トリガーが起動[!INCLUDE[tsql](../../includes/tsql-md.md)]言語イベントが属している*event_group*です。 DDL トリガー イベント グループは、「 [DDL イベント グループ](../../relational-databases/triggers/ddl-event-groups.md)です。  
  
 CREATE TRIGGER の実行が終了したら*event_group*マクロとしても機能、イベントの種類を追加することでそれを sys.trigger_events カタログ ビューについて説明します。  
  
 NOT FOR REPLICATION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 トリガーに関係するテーブルがレプリケーション エージェントによって変更されるときに、トリガーを実行しないことを示します。  
  
 *sql_statement*  
 トリガー条件とトリガー動作です。 トリガーの条件では、試行した DML イベント、DDL イベント、またはログオン イベントによってトリガー動作が実行されるかどうかを判定するための補足の条件を指定します。  
  
 [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントで指定されたトリガー動作は、操作が試行されると有効になります。  
  
 トリガーは、任意の数と種類を含めることができますの[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント、例外をします。 詳細については、「解説」を参照してください。 トリガーは、データ変更またはデータ定義ステートメントに基づいてデータをチェックまたは変更するものであり、ユーザーに値は返されません。 [!INCLUDE[tsql](../../includes/tsql-md.md)]トリガーのステートメントを頻繁に含む[フロー制御言語](~/t-sql/language-elements/control-of-flow.md)します。  
  
 DML トリガーでは、deleted および inserted 論理 (概念) テーブルが使用されます。 論理テーブルは、トリガーが定義されるテーブル、つまり、ユーザー操作の対象となるテーブルと構造的に類似しています。 deleted および inserted テーブルには、ユーザー操作によって変更される行の古い値または新しい値が格納されます。 たとえばのすべての値を取得するため、`deleted`テーブルで使用します。  
  
```  
SELECT * FROM deleted;  
```  
  
 詳細については、次を参照してください。 [inserted および deleted テーブルを使用して](../../relational-databases/triggers/use-the-inserted-and-deleted-tables.md)です。  
  
 DDL およびログオン トリガーを使用して、トリガー起動イベントに関する情報をキャプチャする、 [EVENTDATA & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/eventdata-transact-sql.md)関数。 詳細については、次を参照してください。 [、EVENTDATA 関数を使用して](../../relational-databases/triggers/use-the-eventdata-function.md)です。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]更新では、**テキスト**、 **ntext**、または**イメージ**テーブルまたはビューに INSTEAD OF によって列をトリガーします。  
  
> [!IMPORTANT]  
>  **ntext**、**テキスト**、および**イメージ**データ型は、将来のバージョンで削除される予定[!INCLUDE[msCoName](../../includes/msconame-md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 新しい開発作業では、これらのデータ型の使用は避け、現在これらのデータ型を使用しているアプリケーションは修正するようにしてください。 代わりに、 [nvarchar(max)](../../t-sql/data-types/nchar-and-nvarchar-transact-sql.md)、 [varchar(max)](../../t-sql/data-types/char-and-varchar-transact-sql.md)、 [varbinary(max)](../../t-sql/data-types/binary-and-varbinary-transact-sql.md) を使用してください。 両方 AFTER トリガーと INSTEAD OF トリガー サポート**varchar (max)**、 **nvarchar (max)**、および**varbinary (max)** inserted および deleted テーブル内のデータ。  
  
 メモリ最適化テーブル上のトリガーに対してのみ*sql_statement* ATOMIC ブロックは最上位レベルに許可します。 ATOMIC ブロック内で使用できる T-SQL は、ネイティブ プロシージャ内で使用できる T-SQL によって制限されます。  
  
 \<method_specifier >**対象**:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。  
  
 CLR トリガーに対して、トリガーにバインドするアセンブリのメソッドを指定します。 このメソッドは引数を受け取らず、void を返す必要があります。 *class_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子アセンブリの可視性を持つアセンブリ内のクラスとして存在する必要があります。 このクラスの名前が名前空間で修飾されており、名前空間の部分がピリオド (.) で分けられている場合は、このクラス名を角かっこ ([ ]) または引用符 (" ") で区切る必要があります。 入れ子にされたクラスは使用できません。  
  
> [!NOTE]  
>  既定では、CLR コードを実行する [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の機能はオフになっています。 インスタンスでこれらの参照は実行されませんが、作成、変更、およびマネージ コード モジュールを参照するデータベース オブジェクトを削除することができます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]しない限り、 [clr enabled オプション](../../database-engine/configure-windows/clr-enabled-server-configuration-option.md)を使用して有効になっているは[sp _構成](../../relational-databases/system-stored-procedures/sp-configure-transact-sql.md)です。  
  
## <a name="remarks-dml-triggers"></a>「解説」の DML トリガー  
 DML トリガーは主に、ビジネス ルールとデータの整合性を設定するために使用します。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ALTER TABLE と CREATE TABLE ステートメントで宣言参照整合性 (DRI) を使用できます。 ただし、DRI ではデータベース間の参照整合性は提供されません。 参照整合性とは、テーブルの主キーと外部キー間の関係についての規則です。 参照整合性を設定するには、ALTER TABLE と CREATE TABLE で、PRIMARY KEY と FOREIGN KEY 制約を使用します。 トリガー テーブルに制約が存在する場合、これらは INSTEAD OF トリガーが実行された後、AFTER トリガーが実行される前にチェックされます。 制約違反の場合は、INSTEAD OF トリガーの動作がロールバックされ、AFTER トリガーは起動しません。  
  
 テーブルで実行される最初と最後の AFTER トリガーを、sp_settriggerorder を使用して指定できます。 1 つのテーブルで、INSERT、UPDATE、DELETE の各操作に対して指定できる最初の AFTER トリガーと最後の AFTER トリガーはそれぞれ 1 つだけです。 同じテーブルに他の AFTER トリガーが指定されている場合、トリガーはランダムに実行されます。  
  
 ALTER TRIGGER ステートメントを使って最初と最後のトリガーを変更し、変更したトリガーに設定されていた最初と最後を示す属性を削除した場合は、sp_settriggerorder を使用して順序の値を再設定する必要があります。  
  
 AFTER トリガーは、トリガーを起動する SQL ステートメントが正常に実行された後にのみ実行されます。 このステートメントの実行には、更新または削除されるオブジェクトに関連付けられている連鎖的なすべての参照操作と制約チェックの実行も含まれます。 AFTER トリガーは、同じテーブルで INSTEAD OF トリガーを再帰的に起動することはありません。  
  
 テーブルに定義された INSTEAD OF トリガーによって、そのテーブルに対して、通常は INSTEAD OF トリガーを再起動するステートメントが実行された場合、トリガーの再帰呼び出しは行われません。 代わりに、そのステートメントでは、テーブルに INSTEAD OF トリガーが存在しないものとして処理が行われ、制約操作と AFTER トリガーの実行が連鎖的に開始されます。 たとえば、あるテーブルに INSTEAD OF INSERT トリガーが定義されており、そのトリガーによって同じテーブルに対して INSERT ステートメントが実行された場合、INSTEAD OF トリガーによって実行された INSERT ステートメントでは、そのトリガーは再度呼び出されません。 トリガーによって INSERT が実行されると、制約動作の実行処理とそのテーブルに定義されている AFTER INSERT トリガーの起動処理が開始されます。  
  
 ビューに定義された INSTEAD OF トリガーによって、そのビューに対し、通常 INSTEAD OF トリガーを再起動するステートメントが実行された場合、そのトリガーの再帰呼び出しは行われません。 代わりに、そのステートメントは、そのビューの基になるベース テーブルに対する変更として解決されます。 この場合、ビューの定義では、更新可能なビューの制限をすべて満たしている必要があります。 更新可能なビューの定義では、次を参照してください。[変更データ ビューを経由した](../../relational-databases/views/modify-data-through-a-view.md)です。  
  
 たとえば、あるビューに INSTEAD OF UPDATE トリガーが定義されており、そのトリガーによって同じビューを参照する UPDATE ステートメントが実行された場合、INSTEAD OF トリガーによって実行された UPDATE ステートメントでは、そのトリガーは再度呼び出されません。 トリガーによって実行された UPDATE ステートメントでは、ビューに INSTEAD OF トリガーが存在しないものとして処理が行われます。 この UPDATE によって変更された列は、単一のベース テーブルに対して解決される必要があります。 基になるベース テーブルを変更するたびに、制約の適用とそのテーブルに定義された AFTER トリガーの起動が連鎖的に開始されます。  
  
### <a name="testing-for-update-or-insert-actions-to-specific-columns"></a>特定の列に対する UPDATE または INSERT 操作のテスト  
 特定の列に対する UPDATE または INSERT による変更に基づいて、操作を実行するよう [!INCLUDE[tsql](../../includes/tsql-md.md)] トリガーを設定できます。 使用して[UPDATE()](../../t-sql/functions/update-trigger-functions-transact-sql.md)または[COLUMNS_UPDATED](../../t-sql/functions/columns-updated-transact-sql.md)この目的のトリガーの本文にします。 UPDATE() では、1 つの列に対する UPDATE または INSERT の操作がテストされます。 COLUMNS_UPDATED では、複数の列に対する UPDATE 操作や INSERT 操作がテストされ、どの列が挿入または更新されたかを示すビット パターンが返されます。  
  
### <a name="trigger-limitations"></a>トリガーの制限  
 CREATE TRIGGER はバッチ内の最初のステートメントとして使用する必要があり、1 つのテーブルにのみ適用されます。  
  
 トリガーは現在のデータベース内でしか作成できませんが、他のデータベース内のオブジェクトを参照することができます。  
  
 トリガーを修飾するトリガー スキーマ名を指定する場合は、テーブル名を同じ方法で修飾します。  
  
 1 つのトリガー動作を、同じ CREATE TRIGGER ステートメント内の複数のユーザー操作 (たとえば、INSERT と UPDATE) に対して定義できます。  
  
 INSTEAD OF DELETE/UPDATE トリガーは、外部キーを持ち、DELETE/UPDATE 操作に対する連鎖操作が定義されているテーブルでは定義できません。  
  
 トリガーの内部では任意の SET ステートメントを指定できます。 選択した SET オプションは、トリガーの実行中有効で、終了後は元の設定に戻ります。  
  
 トリガーが起動すると、ストアド プロシージャの場合と同様に、呼び出し側アプリケーションに結果が返されます。 トリガーを実行しても結果がアプリケーションに返されないようにするには、結果を返す SELECT ステートメントや変数を割り当てるステートメントをトリガーから除外します。 ユーザーに結果を返す SELECT ステートメントや変数を割り当てるステートメントを含むトリガーは、トリガー テーブルの変更が許可される各アプリケーションに結果を書き込む必要があるという点から、特殊な扱いが必要です。 トリガー内で変数を割り当てる必要がある場合は、トリガーの先頭で SET NOCOUNT ステートメントを使用して、結果セットが返されないようにします。  
  
 TRUNCATE TABLE ステートメントは実質的には DELETE ステートメントですが、個別の行の削除がログに記録されないため、トリガーはアクティブになりません。 ただし、TRUNCATE TABLE ステートメントを実行する権限のあるユーザー以外は、このように DELETE トリガーが回避されてしまうことに注意を払う必要はありません。  
  
 ログに記録されるかどうかにかかわらず、WRITETEXT ステートメントによってトリガーがアクティブになることはありません。  
  
 次[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントは DML トリガーでは使用できません。  
  
||||  
|-|-|-|  
|ALTER DATABASE|CREATE DATABASE|DROP DATABASE|  
|RESTORE DATABASE|RESTORE LOG|RECONFIGURE|  
  
 また、次の [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、トリガーによって起動される操作の対象となるテーブルまたはビューに対して使用する場合は、DML トリガー内では使用できません。  
  
||||  
|-|-|-|  
|CREATE INDEX (CREATE SPATIAL INDEX および CREATE XML INDEX を含む)|ALTER INDEX|DROP INDEX|  
|DBCC DBREINDEX|ALTER PARTITION FUNCTION|DROP TABLE|  
|ALTER TABLE (次の操作で使用する場合)<br /><br /> 列の追加、変更、または削除<br /><br /> パーティションを切り替えます。<br /><br /> PRIMARY KEY 制約や UNIQUE 制約の追加または削除|||  
  
> [!NOTE]  
>  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]ユーザー定義トリガーをサポートしていませんでシステム テーブルをお勧めシステム テーブルでは、ユーザー定義トリガーを作成しないようにします。  
  
## <a name="remarks-ddl-triggers"></a>「解説」の DDL トリガー  
 DDL トリガーでは、標準のトリガーと同様、イベントに応答してストアド プロシージャが実行されますが、 標準のトリガーとは異なり、テーブルまたはビューの UPDATE、INSERT、DELETE ステートメントに応答して実行されることはありません。 このトリガーは、主にデータ定義言語 (DDL) ステートメントに応答して起動します。 このようなステートメントには、CREATE、ALTER、DROP、GRANT、DENY、REVOKE、UPDATE STATISTICS ステートメントなどがあります。 DDL と同様の操作を実行する特定のシステム ストアド プロシージャも DDL トリガーを起動できます。  
  
> [!IMPORTANT]  
>  DDL トリガーをテストして、システム ストアド プロシージャの実行に対する応答を確認してください。 たとえば、CREATE TYPE ステートメントおよび sp_addtype ストアド プロシージャと sp_rename ストアド プロシージャは、CREATE_TYPE イベントで作成される DDL トリガーを起動します。  
  
 DDL トリガーの詳細については、次を参照してください。 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)です。  
  
 DDL トリガーは、ローカルまたはグローバルの一時テーブルおよびストアド プロシージャに影響するイベントに応答して起動されることはありません。  
  
 DML トリガーと異なり、DDL トリガーのスコープはスキーマに設定されません。 このため、DDL トリガーに関するメタデータのクエリに、OBJECT_ID、OBJECT_NAME、OBJECTPROPERTY、OBJECTPROPERTYEX などの関数を使用することはできません。 代わりに、カタログ ビューを使用してください。 詳細については、次を参照してください。 [DDL トリガーに関する情報を取得](../../relational-databases/triggers/get-information-about-ddl-triggers.md)です。  
  
> [!NOTE]  
>  サーバー スコープの DDL トリガーの表示で、[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]オブジェクト エクスプ ローラーで、**トリガー**フォルダーです。 このフォルダーは、 **[Server Objects]** フォルダーにあります。 データベース スコープの DDL トリガーの表示で、**データベース トリガー**フォルダーです。 このフォルダーは対応するデータベースの **[Programmability]** フォルダーにあります。  
  
## <a name="logon-triggers"></a>ログオン トリガー  
 ログオン トリガーは、LOGON イベントに応答してストアド プロシージャを実行します。 このイベントは、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスでユーザー セッションが確立されるときに発生します。 ログオン トリガーは、ログインの認証段階が終了した後、ユーザー セッションが実際に確立されるまでの間に発生します。 したがって、通常、エラー メッセージや PRINT ステートメントからのメッセージはユーザーに通知されますが、このトリガー内で発生したすべてのメッセージは [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のエラー ログに記録されます。 詳細については、次を参照してください。[ログオン トリガー](../../relational-databases/triggers/logon-triggers.md)です。  
  
 認証に失敗した場合は、ログオン トリガーが作動しません。  
  
 分散トランザクションはログオン トリガーではサポートされていません。 分散トランザクションが含まれているログオン トリガーが起動されると、エラー 3969 が返されます。  
  
### <a name="disabling-a-logon-trigger"></a>ログオン トリガーを無効にする  
 ログオン トリガーを使用すると、 [!INCLUDE[ssDE](../../includes/ssde-md.md)] sysadmin **固定サーバー ロールのメンバーを含むすべてのユーザーの** への接続を効率的に禁止できます。 ログオン トリガーによって接続が禁止されているときでも、 **sysadmin** 固定サーバー ロールのメンバーは、専用管理者接続を使用するか、または [!INCLUDE[ssDE](../../includes/ssde-md.md)] を最小構成モード (-f) で起動することにより、接続できます。 詳細については、「 [データベース エンジン サービスのスタートアップ オプション](../../database-engine/configure-windows/database-engine-service-startup-options.md)」を参照してください。  
  
## <a name="general-trigger-considerations"></a>トリガーについての留意事項  
  
### <a name="returning-results"></a>結果の返送  
 今後のバージョンの SQL Server では、トリガーを使用して結果を返す機能が削除される予定です。 結果セットを返すトリガーは、それと連動するように設計されていないアプリケーションでは予期しない動作を起こすことがあります。 新しい開発作業では、トリガーを使用して結果セットを返すことを避け、現在この方法を使用しているアプリケーションについては変更を検討してください。 トリガーが結果セットを返すようにするに設定、 [disallow results from triggers オプション](../../database-engine/configure-windows/disallow-results-from-triggers-server-configuration-option.md)を 1 にします。  
  
 ログオン トリガーは、結果セットを返すことを常に禁止しているため、この動作は構成できません。 ログオン トリガーが結果セットを生成すると、トリガーは実行に失敗し、トリガーを起動したログイン試行は拒否されます。  
  
### <a name="multiple-triggers"></a>複数のトリガー  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]により、複数のトリガーを各 DML、DDL、またはログオン イベントを作成できます。 たとえば、既に UPDATE トリガーが作成されているテーブルに対して CREATE TRIGGER FOR UPDATE を実行すると、追加の更新トリガーが作成されます。 以前のバージョンの[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]1 つだけで、各テーブルに対して INSERT、UPDATE、または DELETE データ修正イベントが許可されるをトリガーします。  
  
### <a name="recursive-triggers"></a>再帰トリガー  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、ALTER DATABASE によって RECURSIVE_TRIGGERS 設定が有効になっていれば、トリガーの再帰呼び出しが行えます。  
  
 再帰トリガーでは、次の種類の再帰呼び出しが有効になります。  
  
-   間接再帰  
  
     間接再帰では、アプリケーションでテーブル T1 が更新されると、 この操作によってトリガー TR1 が起動し、テーブル T2 が更新されます。 この再帰呼び出しでは、次にトリガー TR2 が起動し、テーブル T1 が更新されます。  
  
-   直接再帰  
  
     直接再帰では、アプリケーションでテーブル T1 が更新されると、 この操作によってトリガー TR1 が起動し、テーブル T1 が更新されます。 テーブル T1 が更新されると、トリガー TR1 が再び起動するという動作が続きます。  
  
 次の例では、間接トリガー再帰と直接トリガー再帰の両方を使用します。ここでは、テーブル T1 で 2 つの更新トリガー TR1 と TR2 が定義されているとします。 トリガー TR1 によって、テーブル T1 が再帰的に更新されます。 UPDATE ステートメントでは、TR1 と TR2 が 1 回ずつ実行されます。 さらに、TR1 が実行されると、TR1 (再帰的) と TR2 が起動します。 トリガーの inserted テーブルと deleted テーブルには、そのトリガーを呼び出した UPDATE ステートメントのみに対応する行が格納されています。  
  
> [!NOTE]  
>  この動作は、ALTER DATABASE によって RECURSIVE_TRIGGERS 設定が有効になっている場合にのみ実行されます。 あるイベントに対して複数のトリガーが定義されている場合、それらの実行順序に決まりはありません。 個々のトリガーは自己完結している必要があります。  
  
 RECURSIVE_TRIGGERS の設定を無効にすると、直接再帰のみが無効になります。 間接再帰呼び出しを無効にするには、sp_configure を使用して、サーバー オプション nested triggers を 0 に設定します。  
  
 いずれかのトリガーで ROLLBACK TRANSACTION が実行されると、入れ子レベルにかかわらず、それ以降のトリガーは実行されません。  
  
### <a name="nested-triggers"></a>入れ子にされたトリガー  
 トリガーは 32 レベルまで入れ子にできます。 トリガーによって、別のトリガーが存在するテーブルが変更された場合、この 2 番目のトリガーがアクティブになり、さらに別のトリガーを呼び出すことができます。 この連鎖的なトリガーで無限ループが発生すると、入れ子レベルを超過した時点でトリガーは取り消されます。 ときに、[!INCLUDE[tsql](../../includes/tsql-md.md)]トリガーは、CLR ルーチン、型を参照してマネージ コードを実行するか、集計、この参照は、32 レベルの入れ子制限の 1 つのレベルとしてカウントします。 マネージ コード内から呼び出されたメソッドは、この制限としてはカウントされません。  
  
 入れ子にされたトリガーを無効にするには、sp_configure の nested triggers オプションを 0 (オフ) に設定します。 既定の構成では、入れ子になったトリガーは許可されています。 入れ子にされたトリガーがオフの場合、ALTER DATABASE によって RECURSIVE_TRIGGERS がどのように設定されていても、再帰トリガーは無効になります。  
  
 最初のトリガーを INSTEAD OF トリガーが起動場合であっても内部に入れ子にした後、**入れ子になったトリガー**サーバー構成オプションが 0 に設定します。 ただし、この設定では後で AFTER トリガーは起動されません。 入れ子になったトリガーのアプリケーションが動作に関してビジネス ルールに従っているかどうかを決定する、アプリケーションを確認することをお勧めときに、**入れ子になったトリガー**サーバー構成オプションが 0 に設定適切な変更を加えます。  
  
### <a name="deferred-name-resolution"></a>名前の遅延解決  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]により、[!INCLUDE[tsql](../../includes/tsql-md.md)]ストアド プロシージャ、トリガー、バッチがコンパイル時に存在しないテーブルを参照してください。 この機能を名前の遅延解決といいます。  
  
## <a name="permissions"></a>Permissions  
 DML トリガーを作成するには、トリガーを作成するテーブルまたはビューに対する ALTER 権限が必要です。  
  
 サーバー スコープ (ON ALL SERVER) の DDL トリガー、またはログオン トリガーを作成するには、サーバーに対する CONTROL SERVER 権限が必要です。 データベース スコープ (ON DATABASE) の DDL トリガーを作成するには、現在のデータベースに対する ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-using-a-dml-trigger-with-a-reminder-message"></a>A. DML トリガーを事前通知と組み合わせて使用する  
 データを追加または変更が試行されたときに、次の DML トリガーがクライアントにメッセージを出力、`Customer`テーブルに、[!INCLUDE[ssSampleDBnormal](../../includes/sssampledbnormal-md.md)]データベース。  
  
```  
CREATE TRIGGER reminder1  
ON Sales.Customer  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Customer Relations', 16, 10);  
GO  
```  
  
### <a name="b-using-a-dml-trigger-with-a-reminder-e-mail-message"></a>B. DML トリガーを電子メール メッセージと組み合わせて使用する  
 次の例は、`MaryM` テーブルが変更されたときに、指定したユーザー (`Customer`) に電子メールを送信します。  
  
```  
CREATE TRIGGER reminder2  
ON Sales.Customer  
AFTER INSERT, UPDATE, DELETE   
AS  
   EXEC msdb.dbo.sp_send_dbmail  
        @profile_name = 'AdventureWorks2012 Administrator',  
        @recipients = 'danw@Adventure-Works.com',  
        @body = 'Don''t forget to print a report for the sales force.',  
        @subject = 'Reminder';  
GO  
```  
  
### <a name="c-using-a-dml-after-trigger-to-enforce-a-business-rule-between-the-purchaseorderheader-and-vendor-tables"></a>C. DML AFTER トリガーを使用して、PurchaseOrderHeader テーブルと Vendor テーブルの間にビジネス ルールを設定する  
 CHECK 制約で参照できるのは、列レベルまたはテーブル レベルの制約が定義されている列のみであるため、テーブル間にまたがる制約 (ここでは、ビジネス ルール) はすべてトリガーとして定義する必要があります。  
  
 次の例は、DML トリガーを AdventureWorks2012 データベースに作成します。 このトリガーことを確認します信用格付け、仕入先が良い (5 ではない) に新しい発注を挿入する試行が行われたときに、`PurchaseOrderHeader`テーブル。 ベンダーの信用格付けを取得する、`Vendor`テーブルを参照する必要があります。 信用格付けが低い場合は、メッセージが表示され、挿入は実行されません。  
  
```  
-- This trigger prevents a row from being inserted in the Purchasing.PurchaseOrderHeader 
-- table when the credit rating of the specified vendor is set to 5 (below average).  
  
CREATE TRIGGER Purchasing.LowCredit ON Purchasing.PurchaseOrderHeader  
AFTER INSERT  
AS  
IF EXISTS (SELECT *  
           FROM Purchasing.PurchaseOrderHeader AS p   
           JOIN inserted AS i   
           ON p.PurchaseOrderID = i.PurchaseOrderID   
           JOIN Purchasing.Vendor AS v   
           ON v.BusinessEntityID = p.VendorID  
           WHERE v.CreditRating = 5  
          )  
BEGIN  
RAISERROR ('A vendor''s credit rating is too low to accept new  
purchase orders.', 16, 1);  
ROLLBACK TRANSACTION;  
RETURN   
END;  
GO  
  
-- This statement attempts to insert a row into the PurchaseOrderHeader table  
-- for a vendor that has a below average credit rating.  
-- The AFTER INSERT trigger is fired and the INSERT transaction is rolled back.  
  
INSERT INTO Purchasing.PurchaseOrderHeader (RevisionNumber, Status, EmployeeID,  
VendorID, ShipMethodID, OrderDate, ShipDate, SubTotal, TaxAmt, Freight)  
VALUES (  
2  
,3  
,261  
,1652  
,4  
,GETDATE()  
,GETDATE()  
,44594.55  
,3567.564  
,1114.8638 );  
GO  
  
```  
  
### <a name="d-using-a-database-scoped-ddl-trigger"></a>D. データベース スコープの DDL トリガーを使用する  
 次の例では、DDL トリガーを使用して、データベースのシノニムが削除されないようにします。  
  
```  
CREATE TRIGGER safety   
ON DATABASE   
FOR DROP_SYNONYM  
AS   
   RAISERROR ('You must disable Trigger "safety" to drop synonyms!',10, 1)  
   ROLLBACK  
GO  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
### <a name="e-using-a-server-scoped-ddl-trigger"></a>E. サーバー スコープの DDL トリガーを使用する  
 次の例は、場合は、CREATE DATABASE イベントは、現在のサーバー インスタンスで発生しを使用してメッセージを印刷する DDL トリガーを使用して、`EVENTDATA`の対応するテキストを取得する関数[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメントです。 DDL トリガーで EVENTDATA を使用しての詳細については、次を参照してください。 [、EVENTDATA 関数を使用して](../../relational-databases/triggers/use-the-eventdata-function.md)です。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
CREATE TRIGGER ddl_trig_database   
ON ALL SERVER   
FOR CREATE_DATABASE   
AS   
    PRINT 'Database Created.'  
    SELECT EVENTDATA().value('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
GO  
DROP TRIGGER ddl_trig_database  
ON ALL SERVER;  
GO  
```  
  
### <a name="f-using-a-logon-trigger"></a>F. ログオン トリガーを使用する  
 次のログオン トリガーの例を拒否にログインしようとすると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]のメンバーとして、 *login_test*ログインの場合はそのログインで実行されている 3 つのユーザー セッションが既に存在します。  
  
**適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
```  
USE master;  
GO  
CREATE LOGIN login_test WITH PASSWORD = '3KHJ6dhx(0xVYsdf' MUST_CHANGE,  
    CHECK_EXPIRATION = ON;  
GO  
GRANT VIEW SERVER STATE TO login_test;  
GO  
CREATE TRIGGER connection_limit_trigger  
ON ALL SERVER WITH EXECUTE AS 'login_test'  
FOR LOGON  
AS  
BEGIN  
IF ORIGINAL_LOGIN()= 'login_test' AND  
    (SELECT COUNT(*) FROM sys.dm_exec_sessions  
            WHERE is_user_process = 1 AND  
                original_login_name = 'login_test') > 3  
    ROLLBACK;  
END;  
  
```  
  
### <a name="g-viewing-the-events-that-cause-a-trigger-to-fire"></a>G. トリガーを起動するイベントを表示する  
 次の例は、`sys.triggers` および `sys.trigger_events` カタログ ビューをクエリし、どの [!INCLUDE[tsql](../../includes/tsql-md.md)] 言語イベントでトリガー `safety` が起動されるかを特定します。 `safety` は前の例で作成したものです。  
  
```  
SELECT TE.*  
FROM sys.trigger_events AS TE  
JOIN sys.triggers AS T ON T.object_id = TE.object_id  
WHERE T.parent_class = 0 AND T.name = 'safety';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)   
 [COLUMNS_UPDATED と #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/columns-updated-transact-sql.md)   
 [CREATE TABLE (Transact-SQL)](../../t-sql/statements/create-table-transact-sql.md)   
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [TRIGGER_NESTLEVEL & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/trigger-nestlevel-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sys.dm_sql_referenced_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referenced-entities-transact-sql.md)   
 [sys.dm_sql_referencing_entities &#40;Transact-SQL&#41;](../../relational-databases/system-dynamic-management-views/sys-dm-sql-referencing-entities-transact-sql.md)   
 [sys.sql_expression_dependencies &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-expression-dependencies-transact-sql.md)   
 [sp_help &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-help-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [sp_helptext &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptext-transact-sql.md)   
 [sp_rename &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-rename-transact-sql.md)   
 [sp_settriggerorder & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-settriggerorder-transact-sql.md)   
 [UPDATE &#40; #41& #40 です。TRANSACT-SQL と #41 です。](../../t-sql/functions/update-trigger-functions-transact-sql.md)   
 [DML トリガーに関する情報の取得](../../relational-databases/triggers/get-information-about-dml-triggers.md)   
 [DDL トリガーに関する情報を取得します。](../../relational-databases/triggers/get-information-about-ddl-triggers.md)   
 [sys.triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-triggers-transact-sql.md)   
 [sys.trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-trigger-events-transact-sql.md)   
 [sys.sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-sql-modules-transact-sql.md)   
 [sys.assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-assembly-modules-transact-sql.md)   
 [sys.server_triggers &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-triggers-transact-sql.md)   
 [sys.server_trigger_events &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-trigger-events-transact-sql.md)   
 [sys.server_sql_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-sql-modules-transact-sql.md)   
 [sys.server_assembly_modules &#40;Transact-SQL&#41;](../../relational-databases/system-catalog-views/sys-server-assembly-modules-transact-sql.md)  
  
  




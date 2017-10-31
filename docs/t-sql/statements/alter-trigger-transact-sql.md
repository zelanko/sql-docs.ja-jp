---
title: "ALTER TRIGGER (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 05/08/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ALTER TRIGGER
- ALTER_TRIGGER_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- DDL triggers, modifying
- triggers [SQL Server], modifying
- modifying triggers
- ALTER TRIGGER statement
- DML triggers, modifying
ms.assetid: 2a99c7c1-ac2f-4637-aa7c-3d1bf514e500
caps.latest.revision: 74
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1ae43399e1154e326ccee3d8760d59c71b73de5b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="alter-trigger-transact-sql"></a>ALTER TRIGGER (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  以前に CREATE TRIGGER ステートメントで作成された DML トリガー、DDL トリガー、またはログオン トリガーの定義を変更します。 トリガーは、CREATE TRIGGER を使用して作成します。 直接作成する必要が[!INCLUDE[tsql](../../includes/tsql-md.md)]ステートメント内に作成されるアセンブリのメソッドから、または、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)]共通言語ランタイム (CLR) のインスタンスにアップロードし、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 ALTER TRIGGER ステートメントで使用されるパラメーターの詳細については、次を参照してください。 [CREATE TRIGGER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-trigger-transact-sql.md).  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- SQL Server Syntax  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)  

ALTER TRIGGER schema_name.trigger_name   
ON  ( table | view )   
[ WITH <dml_trigger_option> [ ,...n ] ]  
 ( FOR | AFTER | INSTEAD OF )   
{ [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
[ NOT FOR REPLICATION ]   
AS { sql_statement [ ; ] [ ...n ] | EXTERNAL NAME <method specifier>   
[ ; ] }   
  
<dml_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ <EXECUTE AS Clause> ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
  
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table 
-- (DML Trigger on memory-optimized tables)  

ALTER TRIGGER schema_name.trigger_name   
ON  ( table  )   
[ WITH <dml_trigger_option> [ ,...n ] ]  
 ( FOR | AFTER )   
{ [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
AS { sql_statement [ ; ] [ ...n ] }   
  
<dml_trigger_option> ::=  
    [ NATIVE_COMPILATION ]  
    [ SCHEMABINDING ]  
    [ <EXECUTE AS Clause> ]  
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, 
-- or UPDATE statement (DDL Trigger)  
  
ALTER TRIGGER trigger_name   
ON { DATABASE | ALL SERVER }   
[ WITH <ddl_trigger_option> [ ,...n ] ]  
{ FOR | AFTER } { event_type [ ,...n ] | event_group }   
AS { sql_statement [ ; ] | EXTERNAL NAME <method specifier>   
[ ; ] }  
}   
  
<ddl_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ <EXECUTE AS Clause> ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
  
-- Trigger on a LOGON event (Logon Trigger)  

ALTER TRIGGER trigger_name   
ON ALL SERVER   
[ WITH <logon_trigger_option> [ ,...n ] ]  
{ FOR| AFTER } LOGON   
AS { sql_statement  [ ; ] [ ,...n ] | EXTERNAL NAME < method specifier >  
  [ ; ] }  
  
<logon_trigger_option> ::=  
    [ ENCRYPTION ]  
    [ EXECUTE AS Clause ]  
  
<method_specifier> ::=  
    assembly_name.class_name.method_name  
```  
  
```  
-- Windows Azure SQL Database Syntax   
-- Trigger on an INSERT, UPDATE, or DELETE statement to a table or view (DML Trigger)   
  
ALTER TRIGGER schema_name. trigger_name   
ON (table | view )   
 [ WITH <dml_trigger_option> [ ,...n ] ]   
 ( FOR | AFTER | INSTEAD OF )   
{ [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] }   
AS { sql_statement [ ; ] [...n ] }   
  
<dml_trigger_option> ::=   
    [ <EXECUTE AS Clause> ]   
  
-- Trigger on a CREATE, ALTER, DROP, GRANT, DENY, REVOKE, or UPDATE statement (DDL Trigger)   
  
ALTER TRIGGER trigger_name   
ON { DATABASE }   
 [ WITH <ddl_trigger_option> [ ,...n ] ]   
{ FOR | AFTER } { event_type [ ,...n ] | event_group }   
AS { sql_statement   
[ ; ] }  
}   
  
<ddl_trigger_option> ::=   
    [ <EXECUTE AS Clause> ]  
```  
  
## <a name="arguments"></a>引数  
 *schema_name*  
 DML トリガーが属しているスキーマの名前を指定します。 DML トリガーのスコープは、そのトリガーが作成されたテーブルまたはビューのスキーマです。 *スキーマ**名 (_n)* DML トリガーとその対応するテーブルまたはビューが既定のスキーマに属している場合にのみ省略可能です。 *schema_name* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
 *trigger_name*  
 変更する既存のトリガーです。  
  
 *テーブル* | *ビュー*  
 DML トリガーが実行されるテーブルまたはビューです。 テーブルまたはビューの完全修飾名を指定することはオプションです。  
  
 DATABASE  
 DDL トリガーのスコープを現在のデータベースに適用します。 指定すると、トリガーが起動するたびに*event_type*または*event_group*現在のデータベースで発生します。  
  
 ALL SERVER  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 DDL トリガーまたはログオン トリガーのスコープを現在のサーバーに適用します。 指定すると、トリガーが起動するたびに*event_type*または*event_group*現在のサーバーで任意の場所が発生します。  
  
 WITH ENCRYPTION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 ALTER TRIGGER ステートメントのテキストを含む sys.syscommentssys.sql_modules エントリを暗号化します。 WITH ENCRYPTION を使用してでは、トリガーがの一部としてパブリッシュされない[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]レプリケーション。 WITH ENCRYPTION は、CLR トリガーに対しては指定できません。  
  
> [!NOTE]  
>  トリガーが WITH ENCRYPTION を使用して作成されている場合、それを有効なままにするには、ALTER TRIGGER ステートメントで WITH ENCRYPTION を再度指定する必要があります。  
  
 EXECUTE AS  
 トリガーを実行するセキュリティ コンテキストを指定します。 インスタンスを使用するユーザー アカウントを制御できます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]トリガーによって参照されているすべてのデータベース オブジェクトに対するアクセス許可の検証に使用します。  
  
 詳細については、「[EXECUTE AS 句 &#40;Transact-SQL&#41;](../../t-sql/statements/execute-as-clause-transact-sql.md)」を参照してください。  
  
 NATIVE_COMPILATION  
 トリガーをネイティブでコンパイルすることを示します。  
  
 このオプションは、メモリ最適化テーブルのトリガーに必要です。  
  
 SCHEMABINDING  
 トリガーによって参照されているテーブルを削除または変更できないことを確認します。  
  
 このオプションは、メモリ最適化テーブルのトリガーに必要なは、従来のテーブルのトリガーはサポートされていません。  
  
 AFTER  
 トリガーをアクティブにする SQL ステートメントが正常に実行された後にのみ、そのトリガーを起動することを指定します。 このトリガーが起動される前に、すべての連鎖参照操作および制約チェックも正常に終了している必要があります。  
  
 FOR キーワードのみが指定されている場合は、AFTER が既定値です。  
  
 DML AFTER トリガーは、テーブルでのみ定義できます。  
  
 INSTEAD OF  
 その DML トリガーを、トリガーをアクティブにする SQL ステートメントの代わりに実行するように指定します。したがって、トリガーをアクティブにするステートメントの操作は無効になります。 DDL トリガーまたはログオン トリガーでは INSTEAD OF を指定できません。  
  
 テーブルまたはビューでは、INSERT、UPDATE、または DELETE の各ステートメントに定義できる INSTEAD OF トリガーは 1 つだけですが、 ビューに別のビューを作成して、各ビューに独自の INSTEAD OF トリガーを定義することは可能です。  
  
 INSTEAD OF トリガーは、WITH CHECK OPTION を使用して作成したビューでは使用できません。 WITH CHECK OPTION が指定されているビューに対して INSTEAD OF トリガーを追加すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] でエラーが発生します。 ユーザーは、INSTEAD OF トリガーを定義する前に、ALTER VIEW を使用してそのオプションを解除する必要があります。  
  
 { [ DELETE ] [ , ] [ INSERT ] [ , ] [ UPDATE ] } | { [INSERT ] [ , ] [ UPDATE ] }  
 このテーブルまたはビューに対して実行したときに DML トリガーをアクティブにするデータ変更ステートメントを指定します。 少なくとも 1 つのオプションを指定する必要があります。 トリガー定義では、このキーワードを指定する順序や組み合わせを問いません。 複数のオプションを指定するときは、オプションをコンマで区切ります。  
  
 INSTEAD OF トリガーの場合、目的のテーブルに連鎖的な ON DELETE 参照操作を指定している参照関係があるときは、DELETE オプションを指定できません。 同様に、目的のテーブルに ON UPDATE 連鎖参照操作を指定している参照関係があるときは、UPDATE オプションを指定できません。 詳細については、「[ALTER TABLE &#40;Transact-SQL&#41;](../../t-sql/statements/alter-table-transact-sql.md)」を参照してください。  
  
 *event_type*  
 名前を指定、[!INCLUDE[tsql](../../includes/tsql-md.md)]言語イベントを実行後、DDL トリガーを起動します。 DDL トリガーの有効なイベントは、「 [DDL イベント](../../relational-databases/triggers/ddl-events.md)です。  
  
 *event_group*  
 定義済みグループの名前を指定[!INCLUDE[tsql](../../includes/tsql-md.md)]言語イベントです。 任意の実行後に、DDL トリガーが起動[!INCLUDE[tsql](../../includes/tsql-md.md)]言語イベントが属している*event_group*です。 DDL トリガー イベント グループは、「 [DDL イベント グループ](../../relational-databases/triggers/ddl-event-groups.md)です。 ALTER TRIGGER の実行が終了したら*event_group*マクロとしても機能、イベントの種類を追加することでそれを sys.trigger_events カタログ ビューについて説明します。  
  
 NOT FOR REPLICATION  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 トリガーに関係するテーブルをレプリケーション エージェントが変更するときに、トリガーを実行してはいけないことを示します。  
  
 *sql_statement*  
 トリガー条件とトリガー動作です。  
  
 メモリ最適化テーブル上のトリガーに対してのみ*sql_statement* ATOMIC ブロックは最上位レベルに許可します。 ATOMIC ブロック内で使用できる T-SQL は、ネイティブ プロシージャ内で使用できる T-SQL によって制限されます。  
  
 外部名\<method_specifier >  
 **適用対象**: [!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)] から [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]  
  
 トリガーにバインドするアセンブリのメソッドを指定します。 このメソッドは引数を受け取らず、void を返す必要があります。 *class_name*は有効な[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]識別子アセンブリの可視性を持つアセンブリ内のクラスとして存在する必要があります。 入れ子にされたクラスは使用できません。  
  
## <a name="remarks"></a>解説  
 ALTER TRIGGER の詳細についてで「解説」を参照してください。 [CREATE TRIGGER & #40 です。TRANSACT-SQL と #41 です。](../../t-sql/statements/create-trigger-transact-sql.md).  
  
> [!NOTE]  
>  EXTERNAL_NAME オプションおよび ON_ALL_SERVER オプションは、包含データベースでは使用できません。  
  
## <a name="dml-triggers"></a>DML トリガー  
 ALTER TRIGGER では、テーブルおよびビューに対する INSTEAD OF トリガーを利用することで、更新可能なビューを手動で使用できるようになります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、ALTER TRIGGER を、他のすべての種類のトリガー (AFTER、INSTEAD-OF) と同様に適用します。  
  
 テーブルで実行される最初と最後の AFTER トリガーを、sp_settriggerorder を使用して指定できます。 1 つのテーブルにつき、最初と最後の AFTER トリガーはそれぞれ 1 つだけ指定できます。 同じテーブルに他の AFTER トリガーが指定されている場合、トリガーはランダムに実行されます。  
  
 ALTER TRIGGER ステートメントを使って最初と最後のトリガーを変更し、変更したトリガーに設定されていた最初と最後を示す属性を削除した場合は、sp_settriggerorder を使用して順序の値を再設定する必要があります。  
  
 AFTER トリガーは、トリガーを起動する SQL ステートメントが正常に実行された後にのみ実行されます。 このステートメントの実行には、更新または削除されるオブジェクトに関連付けられている連鎖的なすべての参照操作と制約チェックの実行も含まれます。 AFTER トリガー操作は、トリガーをアクティブにするステートメントの結果、およびそのステートメントによって発生するすべての UPDATE および DELETE 連鎖参照操作の結果を調べます。  
  
 子テーブルまたは参照元テーブルへの DELETE 操作が、親テーブルでの DELETE による CASCADE の結果として発生し、その子テーブルの中で DELETE での INSTEAD OF トリガーが定義されている場合、そのトリガーは無視され、DELETE 操作が実行されます。  
  
## <a name="ddl-triggers"></a>DDL トリガー  
 DML トリガーと異なり、DDL トリガーのスコープはスキーマに設定されません。 そのため、DDL トリガーについてメタデータに問い合わせる際に、OBJECT_ID、OBJECT_NAME、OBJECTPROPERTY、および OBJECTPROPERTY(EX) は使用できません。 代わりに、カタログ ビューを使用してください。 詳細については、次を参照してください。 [DDL トリガーに関する情報を取得](../../relational-databases/triggers/get-information-about-ddl-triggers.md)です。  
  
## <a name="logon-triggers"></a>ログオン トリガー  
 [!INCLUDE[ssSDSfull](../../includes/sssdsfull-md.md)] は、ログオン イベントによるトリガーをサポートしません。  
  
## <a name="permissions"></a>Permissions  
 DML トリガーを変更するには、トリガーが定義されているテーブルやビューに対する ALTER 権限が必要です。  
  
 サーバー スコープ (ON ALL SERVER) で定義されている DDL トリガー、またはログオン トリガーを変更するには、サーバーに対する CONTROL SERVER 権限が必要です。 データベース スコープ (ON DATABASE) で定義されている DDL トリガーを変更するには、現在のデータベースでの ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、ユーザーが追加または内のデータを変更しようとするときに、クライアントにユーザー定義メッセージを出力する AdventureWorks 2012 データベースで DML トリガーを作成、`SalesPersonQuotaHistory`テーブル。 次に `ALTER TRIGGER` を使用してトリガーを変更し、トリガーを `INSERT` 操作だけに適用します。 このトリガーは、テーブルの更新や行の挿入を行うユーザーに対して、 `Compensation` 部門にも変更を知らせる必要があることを連絡できるので有用です。  
  
```  
CREATE TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
WITH ENCRYPTION  
AFTER INSERT, UPDATE   
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  

-- Now, change the trigger.  
ALTER TRIGGER Sales.bonus_reminder  
ON Sales.SalesPersonQuotaHistory  
AFTER INSERT  
AS RAISERROR ('Notify Compensation', 16, 10);  
GO  
```  
  
## <a name="see-also"></a>参照  
 [DROP TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/drop-trigger-transact-sql.md)   
 [ENABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/enable-trigger-transact-sql.md)   
 [DISABLE TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/disable-trigger-transact-sql.md)   
 [EVENTDATA &#40;Transact-SQL&#41;](../../t-sql/functions/eventdata-transact-sql.md)   
 [sp_helptrigger &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-helptrigger-transact-sql.md)   
 [ストアド プロシージャの作成](../../relational-databases/stored-procedures/create-a-stored-procedure.md)   
 [sp_addmessage & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-addmessage-transact-sql.md)   
 [トランザクション](../../relational-databases/native-client-ole-db-transactions/transactions.md)   
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
 [パブリケーション データベースでのスキーマの変更](../../relational-databases/replication/publish/make-schema-changes-on-publication-databases.md)  
  
  


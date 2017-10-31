---
title: "EVENTDATA (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- EVENTDATA
- fn_event_data
- EVENTDATA_TSQL
- fn_event_data_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- server instance event data [SQL Server]
- event notifications [SQL Server], event status
- events [SQL Server], status infromation
- EVENTDATA function
- status information [SQL Server], events
- DDL triggers, returning event data
ms.assetid: 03a80e63-6f37-4b49-bf13-dc35cfe46c44
caps.latest.revision: 55
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3b385ee993ab576307b6609670761deae9a7a1f6
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx_md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  サーバーまたはデータベースのイベントに関する情報を返します。 EVENTDATA は、イベント通知が起動されると呼び出され、その結果は指定された Service Broker に返されます。 EVENTDATA は、DDL トリガーまたはログオン トリガーの内部でも使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>解説  
 EVENTDATA は、DDL トリガーまたはログオン トリガーの内部で直接参照された場合のみ、データを返します。 それ以外のルーチンで呼び出された EVENTDATA は、そのルーチンの呼び出し元が DDL トリガーまたはログオン トリガーであっても、NULL を返します。  
  
 EVENTDATA から返されたデータは、EVENTDATA を呼び出したトランザクションが暗黙的または明示的にコミットまたはロールバックを実行するまで有効となりません。  
  
> [!CAUTION]  
>  EVENTDATA は XML データを返します。 このデータは、1 文字に 2 バイトを使用する Unicode としてクライアントに送信されます。 次の Unicode コード ポイントは、EVENTDATA から返される XML で表現することができます。  
>   
>  `0x0009`  
>   
>  `0x000A`  
>   
>  `0x000D`  
>   
>  `>= 0x0020 && <= 0xD7FF`  
>   
>  `>= 0xE000 && <= 0xFFFD`  
>   
>  [!INCLUDE[tsql](../../includes/tsql-md.md)] の識別子やデータで使用できる文字の中には、XML で表現できないものや許可されていないものがあります。 上記の一覧に含まれていないコード ポイントを含んでいる文字やデータは、疑問符 (?) にマップされます。  
  
 ログインのセキュリティを保護するために、CREATE LOGIN ステートメントまたは ALTER LOGIN ステートメントの実行時にパスワードは表示されません。  
  
## <a name="schemas-returned"></a>返されるスキーマ  
 EVENTDATA は、型の値を返します**xml**です。 次のディレクトリに既定では、すべてのイベントのスキーマ定義がインストールされている: [!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd です。  
  
 イベントのスキーマを公開する代わりに、 [Microsoft SQL Server の XML スキーマ](http://go.microsoft.com/fwlink/?LinkID=31850)Web ページ。  
  
 特定のイベント スキーマを抽出するには、複合型のスキーマを検索`EVENT_INSTANCE_\<event_type>`です。 たとえば、DROP_TABLE イベントのスキーマを抽出するスキーマを検索します`EVENT_INSTANCE_DROP_TABLE`です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. DDL トリガーでイベント データをクエリする  
 次の例では、DDL トリガーを作成して、データベースに新しいテーブルが作成されないようにします。 トリガーを起動する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、EVENTDATA によって生成される XML データに対して XQuery を使用することでキャプチャされます。 詳細については、「[XQuery 言語リファレンス &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)」を参照してください。  
  
> [!NOTE]  
>  クエリの実行時、`\<TSQLCommand>`を使用して要素**結果をグリッドに**で[!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、コマンド テキスト内の改行は表示されません。 使用して**結果をテキスト**代わりにします。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TRIGGER safety   
ON DATABASE   
FOR CREATE_TABLE   
AS   
    PRINT 'CREATE TABLE Issued.'  
    SELECT EVENTDATA().value  
        ('(/EVENT_INSTANCE/TSQLCommand/CommandText)[1]','nvarchar(max)')  
   RAISERROR ('New tables cannot be created in this database.', 16, 1)   
   ROLLBACK  
;  
GO  
--Test the trigger.  
CREATE TABLE NewTable (Column1 int);  
GO  
--Drop the trigger.  
DROP TRIGGER safety  
ON DATABASE;  
GO  
```  
  
> [!NOTE]  
>  XQuery を使用することをお勧めする場合はイベント データを返す、 **value()**メソッドの代わりに、 **query()**メソッドです。 **Query()**メソッド返します XML およびアンパサンドでエスケープされる復帰と改行 (CR/LF) インスタンスの出力では中、 **value()**メソッドでは、出力で非表示の CR/LF インスタンスが表示されます。  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>B. DDL トリガーでイベント データを含んだログ テーブルを作成する  
 次の例では、データベース レベルのすべてのイベントに関する情報を格納するテーブルを作成し、DDL トリガーでそのテーブルにデータを設定します。 イベントの種類と[!INCLUDE[tsql](../../includes/tsql-md.md)]によって生成される XML データに対して XQuery を使用してステートメントがキャプチャされる`EVENTDATA`です。  
  
```  
USE AdventureWorks2012;  
GO  
CREATE TABLE ddl_log (PostTime datetime, DB_User nvarchar(100), Event nvarchar(100), TSQL nvarchar(2000));  
GO  
CREATE TRIGGER log   
ON DATABASE   
FOR DDL_DATABASE_LEVEL_EVENTS   
AS  
DECLARE @data XML  
SET @data = EVENTDATA()  
INSERT ddl_log   
   (PostTime, DB_User, Event, TSQL)   
   VALUES   
   (GETDATE(),   
   CONVERT(nvarchar(100), CURRENT_USER),   
   @data.value('(/EVENT_INSTANCE/EventType)[1]', 'nvarchar(100)'),   
   @data.value('(/EVENT_INSTANCE/TSQLCommand)[1]', 'nvarchar(2000)') ) ;  
GO  
--Test the trigger.  
CREATE TABLE TestTable (a int);  
DROP TABLE TestTable ;  
GO  
SELECT * FROM ddl_log ;  
GO  
--Drop the trigger.  
DROP TRIGGER log  
ON DATABASE;  
GO  
--Drop table ddl_log.  
DROP TABLE ddl_log;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [EVENTDATA 関数を使用します。](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)   
 [イベント通知](../../relational-databases/service-broker/event-notifications.md)   
 [ログオン トリガー](../../relational-databases/triggers/logon-triggers.md)  
  
  


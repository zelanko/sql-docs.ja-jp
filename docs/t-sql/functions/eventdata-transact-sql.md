---
title: EVENTDATA (Transact-SQL) | Microsoft Docs
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database
ms.service: 
ms.component: t-sql|functions
ms.reviewer: 
ms.suite: sql
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
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 45f9d434e5833180320dcb3184fdcceec56c715c
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="eventdata-transact-sql"></a>EVENTDATA (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  サーバーまたはデータベースのイベントに関する情報を返します。 EVENTDATA は、イベント通知が起動されると呼び出され、その結果は指定された Service Broker に返されます。 EVENTDATA は、DDL トリガーまたはログオン トリガーの内部でも使用できます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
EVENTDATA( )  
```  
  
## <a name="remarks"></a>Remarks  
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
 EVENTDATA は、型の値を返す xml**です。 既定では、すべてのイベントのスキーマ定義は、[!INCLUDE[ssInstallPath](../../includes/ssinstallpath-md.md)]Tools\Binn\schemas\sqlserver\2006\11\events\events.xsd ディレクトリにインストールされます。  
  
 イベント スキーマを公開する代わりに、 Microsoft SQL Server の XML スキーマ[](http://go.microsoft.com/fwlink/?LinkID=31850) Web ページ。  
  
 特定のイベントのスキーマを抽出するには、複合型 `EVENT_INSTANCE_\<event_type>` のスキーマを検索します。 たとえば、DROP_TABLE イベントのスキーマを抽出するには、`EVENT_INSTANCE_DROP_TABLE` のスキーマを検索します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-querying-event-data-in-a-ddl-trigger"></a>A. DDL トリガーでイベント データをクエリする  
 次の例では、DDL トリガーを作成して、データベースに新しいテーブルが作成されないようにします。 トリガーを起動する [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、EVENTDATA によって生成される XML データに対して XQuery を使用することでキャプチャされます。 詳細については、「[XQuery 言語リファレンス &#40;SQL Server&#41;](../../xquery/xquery-language-reference-sql-server.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] で **[結果をグリッドに表示]** を使用して `\<TSQLCommand>` 要素をクエリすると、コマンド テキストに改行が表示されません。 代わりに、**[結果をテキストで表示]** を使用してください。  
  
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
>  イベント データを返す場合は、**query()** メソッドの代わりに XQuery の **value()** を使用してください。 query()** メソッドでは、XML およびアンパサンドでエスケープされる復帰と改行 (CR/LF) インスタンスが出力に返されます。一方 **value()** メソッドでは、CR/LF インスタンスが出力に返されますが、表示はされません。  
  
### <a name="b-creating-a-log-table-with-event-data-in-a-ddl-trigger"></a>B. DDL トリガーでイベント データを含んだログ テーブルを作成する  
 次の例では、データベース レベルのすべてのイベントに関する情報を格納するテーブルを作成し、DDL トリガーでそのテーブルにデータを設定します。 イベントの種類および [!INCLUDE[tsql](../../includes/tsql-md.md)] ステートメントは、`EVENTDATA` によって生成される XML データに対して XQuery を使用することでキャプチャされます。  
  
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
 [EVENTDATA 関数の使用](../../relational-databases/triggers/use-the-eventdata-function.md)   
 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)   
 [イベント通知](../../relational-databases/service-broker/event-notifications.md)   
 [ログオン トリガー](../../relational-databases/triggers/logon-triggers.md)  
  
  

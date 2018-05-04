---
title: sp_settriggerorder (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_settriggerorder
- sp_settriggerorder_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_settriggerorder
ms.assetid: 8b75c906-7315-486c-bc59-293ef12078e8
caps.latest.revision: 54
author: edmacauley
ms.author: edmaca
manager: craigg
monikerRange: = azuresqldb-current || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 5059547366dbc167c4c73e3c8cabac53d0007382
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="spsettriggerorder-transact-sql"></a>sp_settriggerorder (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-asdb-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-asdb-xxxx-xxx-md.md)]

  最初または最後に起動される AFTER トリガーを指定します。 最初と最後のトリガーの間で起動される AFTER トリガーは、任意の順序で実行されます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_settriggerorder [ @triggername = ] '[ triggerschema. ] triggername'   
    , [ @order = ] 'value'   
    , [ @stmttype = ] 'statement_type'   
    [ , [ @namespace = ] { 'DATABASE' | 'SERVER' | NULL } ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@triggername=** ] **'**[ *triggerschema ***.**]*トリガー * * * '**  
 順序を設定または変更するトリガーの名前と、(該当する場合は) そのトリガーが属するスキーマを指定します。 [*triggerschema ***.**]* トリガー * は**sysname**です。 名前がトリガーに対応していない場合、または名前が INSTEAD OF トリガーに対応している場合は、エラーが返されます。 *triggerschema* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
 [ **@order=** ] **'***value***'**  
 新しいトリガー順序の設定です。 *値*は**varchar (10)** 値は次のいずれかを指定できます。  
  
> [!IMPORTANT]  
>  **最初**と**最後**トリガーは次の 2 つの異なるトリガーである必要があります。  
  
|値|Description|  
|-----------|-----------------|  
|**First**|トリガーは最初に起動されます。|  
|**Last**|トリガーは最後に起動されます。|  
|**なし**|トリガーの起動順序は定義されません。|  
  
 [  **@stmttype=** ] **'***statement_type***'**  
 トリガーを起動する SQL ステートメントを指定します。 *statement_type*は**varchar (50)** INSERT、UPDATE、DELETE、LOGON、またはいずれかを指定できます[!INCLUDE[tsql](../../includes/tsql-md.md)]で表示されているステートメント イベント[DDL イベント](../../relational-databases/triggers/ddl-events.md)です。 イベント グループを指定することはできません。  
  
 トリガーとして指定できる、**最初**または**最後**後は、そのトリガーは、そのステートメントの種類のトリガーとして定義されている種類のステートメントをトリガーします。 たとえば、トリガー **TR1**指定できるは**最初**テーブルに挿入**T1**場合**TR1**は INSERT トリガーとして定義します。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが返されます**TR1**、として設定されているが、INSERT トリガーとしてのみ定義されている、**最初**、または**最後**、UPDATE ステートメントをトリガーします。 詳細については、「解説」を参照してください。  
  
 **@namespace=** { **'DATABASE'** | **'SERVER'** |NULL}  
 ときに*トリガー* 、DDL トリガーは、 **@namespace**を指定するかどうか*トリガー*データベース スコープか、サーバー スコープで作成されました。 場合*トリガー*ログオン トリガーは、サーバーを指定する必要があります。 DDL トリガーのスコープの詳細については、次を参照してください。 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)です。 指定されていない場合、または NULL を指定すると、*トリガー* DML トリガーです。  
  
||  
|-|  
|SERVER の適用対象:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]です。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="remarks"></a>解説  
  
## <a name="dml-triggers"></a>DML トリガー  
 1 つのみできます**最初**と 1 つ**最後**1 つのテーブルの各ステートメントをトリガーします。  
  
 場合、**最初**トリガーがテーブル、データベース、またはサーバーで既に定義されている、として新しいトリガーを指定することはできません**最初**、同じテーブル、データベース、またはサーバーで、同じ*statement_type*. この制限は適用も**最後**トリガーします。  
  
 レプリケーションは、テーブルが即時更新サブスクリプションまたはキュー更新サブスクリプションに含まれる場合、自動的に最初のトリガーを生成します。 レプリケーションのトリガーは最初のトリガーであることが必要です。 レプリケーションでは、最初のトリガーを持つテーブルを即時更新サブスクリプションまたはキュー更新サブスクリプションに含めるよう設定すると、エラーが発生します。 テーブルをサブスクリプションに含めた後、トリガーを最初のトリガーに設定すると、 **sp_settriggerorder** はエラーを返します。 レプリケーション トリガーに ALTER TRIGGER を使用するかを使用してかどうか**sp_settriggerorder**にレプリケーション トリガーを変更する、**最後**または**なし**トリガー、サブスクリプションは正しく機能しません。  
  
## <a name="ddl-triggers"></a>DDL トリガー  
 データベース スコープの DDL トリガーとサーバー スコープの DDL トリガーは、同じイベントで存在する場合は、両方のトリガーがあることを指定することができます、**最初**トリガーまたは**最後**トリガーします。 ただし、サーバー スコープのトリガーは常に最初のトリガーになります。 通常、同一イベント上に存在する DDL トリガーの実行順序は次のようになります。  
  
1.  サーバー レベル トリガー**最初**です。  
  
2.  その他のサーバー レベル トリガー。  
  
3.  サーバー レベル トリガー**最後**です。  
  
4.  データベース レベル トリガー**最初**です。  
  
5.  その他のデータベース レベル トリガー。  
  
6.  データベース レベル トリガー**最後**です。  
  
## <a name="general-trigger-considerations"></a>トリガーについての留意事項  
 ALTER TRIGGER ステートメントには、最初と最後のトリガーが変更された場合、**最初**または**最後**トリガーに設定されていた属性は削除され、値が置き換え**None**です。 使用して、順序の値をリセットする必要があります**sp_settriggerorder**です。  
  
 場合は、同じトリガーを 1 つ以上のステートメントの種類に対する最初または最順序として指定する必要があります**sp_settriggerorder**ステートメントの種類ごとに実行する必要があります。 、トリガーする必要があります最初のも定義するステートメントの種類として指定できる前に、**最初**または**最後**トリガーをそのステートメントの種類を起動します。  
  
## <a name="permissions"></a>権限  
 サーバー スコープ (ON ALL SERVER で作成) で定義されている DDL トリガーまたはログオン トリガーの順序を設定するには、CONTROL SERVER 権限が必要です。  
  
 データベース スコープ (ON DATABASE で作成) で DDL トリガーの順序を設定するには、ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
 DML トリガーの順序を設定するには、そのトリガーが定義されているテーブルまたはビューに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-the-firing-order-for-a-dml-trigger"></a>A. DML トリガーの起動順序を設定する  
 次の例は、そのトリガーを指定`uSalesOrderHeader`最初のトリガーされた後に起動する、`UPDATE`で操作が発生、`Sales.SalesOrderHeader`テーブル。  
  
```  
USE AdventureWorks2012;  
GO  
sp_settriggerorder @triggername= 'Sales.uSalesOrderHeader', @order='First', @stmttype = 'UPDATE';  
```  
  
### <a name="b-setting-the-firing-order-for-a-ddl-trigger"></a>B. DDL トリガーの起動順序を設定する  
 次の例では、トリガー `ddlDatabaseTriggerLog` が、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)] データベースで `ALTER_TABLE` イベントの発生後、最初に起動されるトリガーとなるよう指定します。  
  
```  
USE AdventureWorks2012;  
GO  
sp_settriggerorder @triggername= 'ddlDatabaseTriggerLog', @order='First', @stmttype = 'ALTER_TABLE', @namespace = 'DATABASE';  
```  
  
## <a name="see-also"></a>参照  
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [データベース エンジン ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/database-engine-stored-procedures-transact-sql.md)   
 [ALTER TRIGGER &#40;Transact-SQL&#41;](../../t-sql/statements/alter-trigger-transact-sql.md)  
  
  

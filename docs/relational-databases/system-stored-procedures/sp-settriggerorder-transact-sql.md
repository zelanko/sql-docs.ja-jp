---
title: sp_settriggerorder (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_settriggerorder
- sp_settriggerorder_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_settriggerorder
ms.assetid: 8b75c906-7315-486c-bc59-293ef12078e8
author: stevestein
ms.author: sstein
monikerRange: =azuresqldb-current||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 55fedd154195b4f5abf230120a0e16e6a41ce6e3
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68032929"
---
# <a name="sp_settriggerorder-transact-sql"></a>sp_settriggerorder (TRANSACT-SQL)
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
`[ @triggername = ] '[ _triggerschema.] _triggername'` トリガーと、スキーマの名前は、それが属する、該当する場合、順序が設定または変更するのには。 [_triggerschema_ **.** ]*triggername*は**sysname**します。 名前がトリガーに対応していない場合、または名前が INSTEAD OF トリガーに対応している場合は、エラーが返されます。 *triggerschema* DDL トリガーまたはログオン トリガーを指定することはできません。  
  
`[ @order = ] 'value'` 新しいトリガー順序の設定です。 *値*は**varchar (10)** 値は次のいずれかを指定できます。  
  
> [!IMPORTANT]  
>  **First**と**Last**トリガーは 2 つの異なるトリガーである必要があります。  
  
|値|説明|  
|-----------|-----------------|  
|**First**|トリガーは最初に起動されます。|  
|**Last**|トリガーが最後に起動されます。|  
|**None**|トリガーは、任意の順序で起動されます。|  
  
`[ @stmttype = ] 'statement_type'` トリガーを起動する SQL ステートメントを指定します。 *statement_type*は**varchar (50)** INSERT、UPDATE、DELETE、LOGON、またはいずれかを指定できます[!INCLUDE[tsql](../../includes/tsql-md.md)]記載ステートメント イベント[DDL イベント](../../relational-databases/triggers/ddl-events.md)します。 イベント グループを指定することはできません。  
  
 トリガーとして指定できる、**First**または**Last**ステートメントの種類のトリガーとしてそのトリガーが定義した後にのみステートメントの種類のトリガー。 たとえば、トリガー **TR1**指定できるは**First**テーブルに挿入**T1**場合**TR1** INSERT トリガーとして定義されます。 [!INCLUDE[ssDE](../../includes/ssde-md.md)]エラーが返されます**TR1**、として設定されますが、INSERT トリガーとしてのみ定義されている、**First**、または**Last**、UPDATE ステートメントをトリガーします。 詳細については、「解説」を参照してください。  
  
 **@namespace=** { **'DATABASE'**  |  **'SERVER'** | NULL }  
 ときに*triggername* 、DDL トリガーは、 **@namespace** を指定するかどうか*triggername*データベース スコープか、サーバー スコープで作成されました。 場合*triggername* 、ログオン トリガーは、サーバーを指定する必要があります。 DDL トリガーのスコープの詳細については、次を参照してください。 [DDL トリガー](../../relational-databases/triggers/ddl-triggers.md)します。 指定しない場合、または NULL が指定されている場合*triggername* DML トリガーです。  
  
||  
|-|  
|SERVER の適用対象:[!INCLUDE[ssKatmai](../../includes/sskatmai-md.md)]を通じて[!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)]します。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) と 1 (失敗)  
  
## <a name="remarks"></a>コメント  
  
## <a name="dml-triggers"></a>DML トリガー  
 1 つのみ**First**と 1 つ**Last**1 つのテーブルの各ステートメントに対してトリガーします。  
  
 場合、**最初**トリガーがテーブル、データベース、またはサーバーで既に定義されている、として新しいトリガーを指定することはできません**最初**の同じテーブル、データベース、またはサーバーで、同じ*statement_type*. この制限は、**Last** トリガーにも適用されます。  
  
 レプリケーションは、テーブルが即時更新サブスクリプションまたはキュー更新サブスクリプションに含まれる場合、自動的に最初のトリガーを生成します。 レプリケーションのトリガーは最初のトリガーであることが必要です。 レプリケーションでは、最初のトリガーを持つテーブルを即時更新サブスクリプションまたはキュー更新サブスクリプションに含めるよう設定すると、エラーが発生します。 テーブルをサブスクリプションに含めた後、トリガーを最初のトリガーに設定すると、 **sp_settriggerorder** はエラーを返します。 レプリケーション トリガーに ALTER TRIGGER を使用して、または使用するかどうかは**sp_settriggerorder**レプリケーション トリガーを変更する、**最後**または**None**トリガーでは、サブスクリプションは正しく機能しません。  
  
## <a name="ddl-triggers"></a>DDL トリガー  
 両方のトリガーがあることを指定するにはデータベース スコープの DDL トリガーとサーバー スコープの DDL トリガーが、同じイベントで存在する場合、**最初**トリガーまたは**最後**トリガーします。 ただし、常にサーバー スコープのトリガーが最初に起動します。 一般に、同じイベント上に存在する DDL トリガーの実行の順序のとおりです。  
  
1.  サーバー レベル トリガー**最初**します。  
  
2.  その他のサーバー レベル トリガー。  
  
3.  サーバー レベル トリガー**最後**します。  
  
4.  データベース レベル トリガー**最初**します。  
  
5.  その他のデータベース レベル トリガー。  
  
6.  データベース レベル トリガー**最後**します。  
  
## <a name="general-trigger-considerations"></a>トリガーについての留意事項  
 ALTER TRIGGER ステートメントが最初と最後のトリガーの場合は、変更された場合、**最初**または**最後**トリガーに設定されていた属性が削除され、値が置き換え**None**します。 使用して、順序の値をリセットする必要があります**sp_settriggerorder**します。  
  
 1 つ以上のステートメントの種類の最初と最後の順序と同じトリガーを指定する必要がある場合**sp_settriggerorder**ステートメントの種類ごとに実行する必要があります。 また、トリガーする必要があります最初ステートメントの種類の前に定義することを指定できます、**最初**または**最後**にステートメントの種類に対して起動されるトリガー。  
  
## <a name="permissions"></a>アクセス許可  
 トリガーを (ON ALL SERVER を作成する)、サーバー スコープまたはログオンの DDL トリガーの順序を設定するには、CONTROL SERVER 権限が必要です。  
  
 データベースのスコープ (ON DATABASE が作成される) で DDL トリガーの順序を設定するには、ALTER ANY DATABASE DDL TRIGGER 権限が必要です。  
  
 トリガーを DML の順序を設定するには、テーブルまたはトリガーが定義されているビューに対する ALTER 権限が必要です。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-setting-the-firing-order-for-a-dml-trigger"></a>A. DML トリガーの起動順序を設定する  
 次の例では、そのトリガーを指定します。`uSalesOrderHeader`後に発生する最初のトリガーになる、`UPDATE`操作の発生、`Sales.SalesOrderHeader`テーブル。  
  
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
  
  

---
title: sp_fkeys (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 09/08/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_fkeys
- sp_fkeys_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fkeys
ms.assetid: 18110444-d38d-4cff-90d2-d1fc6236668b
caps.latest.revision: 32
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 076f3da85e652a6fd27c208159c64e147079dc90
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43072860"
---
# <a name="spfkeys-transact-sql"></a>sp_fkeys (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  現在の環境への論理外部キーの情報を返します。 このプロシージャは、無効化されている外部キーも含めて、外部キーのリレーションシップを示します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
sp_fkeys [ @pktable_name = ] 'pktable_name'   
     [ , [ @pktable_owner = ] 'pktable_owner' ]   
     [ , [ @pktable_qualifier = ] 'pktable_qualifier' ]   
     { , [ @fktable_name = ] 'fktable_name' }   
     [ , [ @fktable_owner = ] 'fktable_owner' ]   
     [ , [ @fktable_qualifier = ] 'fktable_qualifier' ]  
```  
  
## <a name="arguments"></a>引数  
 [ @pktable_name=] '*pktable_name*'  
 カタログ情報を返すために使用する、主キーが設定されたテーブルの名前を指定します。 *pktable_name*は**sysname**、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされていません。 このパラメーターまたは*fktable_name*パラメーター、またはその両方を指定する必要があります。  
  
 [ @pktable_owner=] '*pktable_owner*'  
 カタログ情報を返すために使用する (主キー) を含むテーブルの所有者の名前です。 *pktable_owner*は**sysname**、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされていません。 場合*pktable_owner*が指定されていない、基になる DBMS の既定のテーブル可視性規則が適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定した名前のテーブルを現在のユーザーが所有している場合、そのテーブルの列が返されます。 場合*pktable_owner*が指定されていない、現在のユーザーが、指定したテーブルを所有していない*pktable_name*、プロシージャは、指定したテーブルを探します*pktable_name*データベース所有者が所有します。 存在する場合は、そのテーブルの列が返されます。  
  
 [ @pktable_qualifier =] '*pktable_qualifier*'  
 (主キーが設定された) テーブル修飾子の名前を指定します。 *pktable_qualifier*が sysname で、既定値は NULL です。 さまざまな DBMS 製品は、3 つの部分がテーブルの名前付けをサポート (*qualifier.owner.name*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]修飾子は、データベース名を表します。 一部の製品で、テーブルのデータベース環境のサーバー名を表します。  
  
 [ @fktable_name=] '*fktable_name*'  
 カタログ情報を返すために使用する (外部キーが設定された) テーブルの名前を指定します。 *fktable_name*が sysname で、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされていません。 このパラメーターまたは*pktable_name*パラメーター、またはその両方を指定する必要があります。  
  
 [ @fktable_owner =] '*fktable_owner*'  
 カタログ情報を返すために使用する (外部キーが設定された) テーブルの所有者の名前を指定します。 *fktable_owner*は**sysname**、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされていません。 場合*fktable_owner*が指定されていない、基になる DBMS の既定のテーブル可視性規則が適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定した名前のテーブルを現在のユーザーが所有している場合、そのテーブルの列が返されます。 場合*fktable_owner*が指定されていない、現在のユーザーが、指定したテーブルを所有していない*fktable_name*、プロシージャは、指定したテーブルを探します*fktable_name*データベース所有者が所有します。 存在する場合は、そのテーブルの列が返されます。  
  
 [ @fktable_qualifier=] '*fktable_qualifier*'  
 (外部キーが設定された) テーブル修飾子の名前を指定します。 *fktable_qualifier*は**sysname**、既定値は NULL です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]修飾子は、データベース名を表します。 一部の製品で、テーブルのデータベース環境のサーバー名を表します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|PKTABLE_QUALIFIER|**sysname**|主キーが設定されたテーブルの修飾子の名前です。 このフィールドには NULL を指定できます。|  
|PKTABLE_OWNER|**sysname**|主キーが設定されたテーブルの所有者名です。 このフィールドは常に値を返します。|  
|PKTABLE_NAME|**sysname**|主キーが設定されたテーブルの名前です。 このフィールドは常に値を返します。|  
|PKCOLUMN_NAME|**sysname**|返される TABLE_NAME の各列に対する、主キー列の名前です。 このフィールドは常に値を返します。|  
|FKTABLE_QUALIFIER|**sysname**|外部キーが設定されたテーブルの修飾子の名前です。 このフィールドには NULL を指定できます。|  
|FKTABLE_OWNER|**sysname**|外部キーが設定されたテーブルの所有者名です。 このフィールドは常に値を返します。|  
|FKTABLE_NAME|**sysname**|外部キーが設定されたテーブルの名前です。 このフィールドは常に値を返します。|  
|FKCOLUMN_NAME|**sysname**|TABLE_NAME の各列の外部キー列の名前が返されます。 このフィールドは常に値を返します。|  
|KEY_SEQ|**smallint**|複数列の主キーにおける、列のシーケンス番号です。 このフィールドは常に値を返します。|  
|UPDATE_RULE|**smallint**|SQL の操作が更新であるとき、外部キーに適用される動作です。  有効値は次のとおりです。<br /> 0=CASCADE: 外部キーを変更します。<br /> 1=NO ACTION: 外部キーが存在する場合には変更します。<br />   2 = set null <br /> 3 = 既定値に設定 |  
|DELETE_RULE|**smallint**|SQL の操作が削除であるとき、外部キーに適用される動作です。 有効値は次のとおりです。<br /> 0=CASCADE: 外部キーを変更します。<br /> 1=NO ACTION: 外部キーが存在する場合には変更します。<br />   2 = set null <br /> 3 = 既定値に設定 |  
|FK_NAME|**sysname**|外部キー識別子です。 データ ソースに適用されない場合は NULL になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] は、FOREIGN KEY 制約の名前を返します。|  
|PK_NAME|**sysname**|主キー識別子。 データ ソースに適用されない場合は NULL になります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] 主キー制約の名前を返します。|  
  
 返される結果は、FKTABLE_QUALIFIER、FKTABLE_OWNER、FKTABLE_NAME、KEY_SEQ で並べ替えられます。  
  
## <a name="remarks"></a>コメント  
 無効な外部キーを持つテーブルを含むアプリケーションのコーディングは、以下のように実装できます。  
  
-   そのテーブルで作業している間は、一時的に制約チェックを無効にして (ALTER TABLE NOCHECK または CREATE TABLE NOT FOR REPLICATION)、その後再び有効にします。  
  
-   トリガーまたはアプリケーション コードを使用して、リレーションシップを設定します。  
  
主キー テーブルの名前を指定され、外部キー テーブルの名前が NULL の場合、sp_fkeys は指定されたテーブルに対する外部キーを含むすべてのテーブルを返します。 外部キー テーブルの名前を指定し、主キー テーブルの名前が NULL の場合、sp_fkeys は、主キー/外部キー関係によって外部キー テーブルの外部キーに関係付けられるすべてのテーブルを返します。  
  
Sp_fkeys ストアド プロシージャは、odbc SQLForeignKeys と同じです。  
  
## <a name="permissions"></a>アクセス許可  
 必要があります`SELECT`スキーマに対する権限。  
  
## <a name="examples"></a>使用例  
 次の例の外部キーの一覧の取得、`HumanResources.Department`テーブルに、`AdventureWorks2012`データベース。  
  
```sql  
USE AdventureWorks2012;  
GO  
EXEC sp_fkeys @pktable_name = N'Department'  
    ,@pktable_owner = N'HumanResources';  
```  
  
## <a name="examples-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例: [!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)] および [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例の外部キーの一覧の取得、`DimDate`テーブルに、`AdventureWorksPDW2012`データベース。 行が返されないため[!INCLUDE[ssDW](../../includes/ssdw-md.md)]は外部キーをサポートしていません。  
  
```sql  
EXEC sp_fkeys @pktable_name = N'DimDate;  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ カタログ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)   
 [sp_pkeys &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-pkeys-transact-sql.md)  
  
  


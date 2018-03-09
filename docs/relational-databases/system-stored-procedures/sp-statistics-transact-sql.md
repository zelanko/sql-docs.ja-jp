---
title: "sp_statistics (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_statistics_TSQL
- sp_statistics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_statistics
ms.assetid: 0bb6495f-258a-47ec-9f74-fd16671d23b8
caps.latest.revision: 
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: acb1e775a99bb3c296064a65aa9eed7be5d17745
ms.sourcegitcommit: 45e4efb7aa828578fe9eb7743a1a3526da719555
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="spstatistics-transact-sql"></a>sp_statistics (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-all-md](../../includes/tsql-appliesto-ss2008-all-md.md)]

  指定したテーブルまたはインデックス付きビュー上にあるすべてのインデックスおよび統計の一覧を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
-- Syntax for SQL Server, Azure SQL Database, Azure SQL Data Warehouse, Parallel Data Warehouse  
  
sp_statistics [ @table_name = ] 'table_name'    
     [ , [ @table_owner = ] 'owner' ]   
     [ , [ @table_qualifier = ] 'qualifier' ]   
     [ , [ @index_name = ] 'index_name' ]   
     [ , [ @is_unique = ] 'is_unique' ]  
     [ , [ @accuracy = ] 'accuracy' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table_name=** ] **'***table_name***'**  
 カタログ情報を返すために使用するテーブルを指定します。 *table_name*は**sysname**、既定値はありません。 ワイルドカードによるパターン照合はサポートされていません。  
  
 [  **@table_owner=** ] **'***所有者***'**  
 カタログ情報を返すために使用するテーブルのテーブル所有者の名前です。 *table_owner*は**sysname**、既定値は NULL です。 ワイルドカードによるパターン照合はサポートされていません。 場合*所有者*が指定されていない、基になる DBMS の既定のテーブル可視性規則が適用されます。  
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、現在のユーザー指定の名前を持つテーブルを所有している場合、そのテーブルのインデックスが返されます。 場合*所有者*が指定されていない、現在のユーザーが、指定したテーブルを所有していないと*名前*、このプロシージャは、指定したテーブルを探します*名前*が所有する、データベース所有者です。 テーブルが存在する場合は、そのテーブルのインデックスが返されます。  
  
 [  **@table_qualifier=** ] **'***修飾子***'**  
 テーブル識別子の名前です。 *修飾子*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子***.***所有者***.***名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、このパラメーターは、データベース名を表します。 一部の製品では、テーブルのデータベース環境のサーバー名を表します。  
  
 [  **@index_name=** ] **'***index_name***'**  
 インデックス名を指定します。 *index_name*は**sysname**、既定値は % です。 ワイルドカードによるパターン照合がサポートされています。  
  
 [  **@is_unique=** ] **'***is_unique***'**  
 あるかどうか一意インデックスのみ (場合**Y**) 返されます。 *is_unique*は**char (1)**、既定値は**N**です。  
  
 [  **@accuracy=** ] **'***精度***'**  
 統計の基数および統計のページの精度を指定します。 *精度*は**char (1)**、既定値は**Q**です。指定**E**基数やページは、正確に統計を更新するかどうかを確認します。  
  
 値**E** (sql_ensure)、ドライバーを無条件に統計を取得します。  
  
 値**Q** (SQL_QUICK) 基数を取得するドライバーを要求して、サーバーからすぐに使用できる場合にのみページします。 この場合、ドライバーで取得される値が最新であるかどうかは保証されません。 Open Group 標準に従って記述されているアプリケーションは常に、ODBC 3.x 準拠のドライバーから SQL_QUICK 動作を取得します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|テーブル修飾子の名前。 この列は、NULL の場合もあります。|  
|**TABLE_OWNER**|**sysname**|テーブル所有者名です。 この列は、常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 この列は、常に値を返します。|  
|**NON_UNIQUE**|**smallint**|NULL になります。<br /><br /> 0 = 一意<br /><br /> 1 = 一意ではない|  
|**INDEX_QUALIFIER**|**sysname**|インデックス所有者の名前。 DBMS 製品の中には、テーブル所有者以外のユーザーでもインデックスを作成できるものがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は常に、同じ**TABLE_NAME**です。|  
|**INDEX_NAME**|**sysname**|インデックスの名前。 この列は、常に値を返します。|  
|**TYPE**|**smallint**|この列は常に値を返します。<br /><br /> 0 = テーブルの統計<br /><br /> 1 = クラスター化<br /><br /> 2 = ハッシュ化<br /><br /> 3 = 非クラスター化|  
|**SEQ_IN_INDEX**|**smallint**|インデックス内での列の位置。|  
|**COLUMN_NAME**|**sysname**|各列の列名、 **TABLE_NAME**が返されます。 この列は、常に値を返します。|  
|**照合順序**|**char (1)**|照合順序で使用されている並べ替え順。 次の値をとります。<br /><br /> A = 昇順<br /><br /> D = 降順<br /><br /> NULL = 適用なし|  
|**基数**|**int**|テーブル内の行数またはインデックス内の一意な値の個数。|  
|**ページ**|**int**|インデックスまたはテーブルを格納するページ数。|  
|**FILTER_CONDITION**|**varchar (128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では値は返されません。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="remarks"></a>解説  
 列で昇順に表示される結果セット内のインデックス**NON_UNIQUE**、**型**、 **INDEX_NAME**、および**SEQ_IN_INDEX**です。  
  
 クラスター化インデックス型は、テーブルのデータがインデックスの順に格納されているインデックス型を指します。 これに対応して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックスをクラスター化します。  
  
 ハッシュ化インデックス型は、完全一致検索または範囲検索を受け付けますが、パターン照合検索ではインデックスは使用されません。  
  
 **sp_statistics**は等価**SQLStatistics** ODBC にします。 返される結果は並べ**NON_UNIQUE**、**型**、 **INDEX_QUALIFIER**、 **INDEX_NAME**、および**SEQ_IN_インデックス**です。 詳細については、次を参照してください。、 [ODBC API リファレンス](http://go.microsoft.com/fwlink/?LinkId=68323)です。  
  
## <a name="permissions"></a>Permissions  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="example-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と[!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、情報を返しますに関する、`DimEmployee`テーブル。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>参照  
 [カタログのストアド プロシージャと #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  


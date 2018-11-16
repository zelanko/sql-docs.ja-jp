---
title: sp_statistics (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-database, sql-data-warehouse, pdw
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_statistics_TSQL
- sp_statistics
dev_langs:
- TSQL
helpviewer_keywords:
- sp_statistics
ms.assetid: 0bb6495f-258a-47ec-9f74-fd16671d23b8
author: stevestein
ms.author: sstein
manager: craigg
monikerRange: '>=aps-pdw-2016||=azuresqldb-current||=azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current'
ms.openlocfilehash: 4b365ad16ce7f96ba3e0dd14f278b1ce4db60a32
ms.sourcegitcommit: 9c6a37175296144464ffea815f371c024fce7032
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/15/2018
ms.locfileid: "51657134"
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
  
 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、指定された名前のテーブルを現在のユーザーが所有している場合、そのテーブルのインデックスが返されます。 場合*所有者*が指定されていない、現在のユーザーが、指定したテーブルを所有していない*名前*、この手順は、指定したテーブルを探します*名前*によって所有されている、データベース所有者です。 テーブルが存在する場合は、そのテーブルのインデックスが返されます。  
  
 [  **@table_qualifier=** ] **'***修飾子***'**  
 テーブル識別子の名前です。 *修飾子*は**sysname**、既定値は NULL です。 さまざまな DBMS 製品は、3 つの部分がテーブルの名前付けをサポート (*修飾子 ***.*** 所有者 ***.*** 名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では、このパラメーターはデータベース名を表します。 一部の製品で、テーブルのデータベース環境のサーバー名を表します。  
  
 [  **@index_name=** ] **'***index_name***'**  
 インデックス名を指定します。 *index_name*は**sysname**、既定値は % です。 ワイルドカードによるパターン照合がサポートされています。  
  
 [  **@is_unique=** ] **'***is_unique***'**  
 あるかどうか一意インデックスのみ (場合**Y**) を返します。 *is_unique*は**char (1)**、既定値は**N**します。  
  
 [  **@accuracy=** ] **'***精度***'**  
 統計のカーディナリティおよび統計のページの精度を指定します。 *精度*は**char (1)**、既定値は**Q**します。指定**E**カーディナリティおよびページが正確になるように、統計が更新されるかどうかを確認します。  
  
 値**E** (sql_ensure) ドライバーを無条件に統計を取得します。  
  
 値**Q** (SQL_QUICK) は、カーディナリティを取得するドライバーを要求し、ページのサーバーからすぐに使用できる場合。 この場合、ドライバーで取得される値が最新であるかどうかは保証されません。 Open Group 標準に従って記述されているアプリケーションは常に、ODBC 3.x 準拠のドライバーから SQL_QUICK 動作を取得します。  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**TABLE_QUALIFIER**|**sysname**|テーブル修飾子の名前。 この列は、NULL の場合もあります。|  
|**TABLE_OWNER**|**sysname**|テーブルの所有者名です。 この列は常に値が返されます。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 この列は常に値が返されます。|  
|**NON_UNIQUE**|**smallint**|NULL 以外です。<br /><br /> 0 = 一意<br /><br /> 1 = 一意ではない|  
|**INDEX_QUALIFIER**|**sysname**|インデックス所有者の名前。 DBMS 製品の中には、テーブル所有者以外のユーザーでもインデックスを作成できるものがあります。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は常に同じ**TABLE_NAME**します。|  
|**INDEX_NAME**|**sysname**|インデックスの名前。 この列は常に値が返されます。|  
|**TYPE**|**smallint**|この列は常に値を返します。<br /><br /> 0 = テーブルの統計<br /><br /> 1 = クラスター化<br /><br /> 2 = ハッシュ化<br /><br /> 3 = 非クラスター化|  
|**SEQ_IN_INDEX**|**smallint**|インデックス内での列の位置。|  
|**COLUMN_NAME**|**sysname**|各列の列名、 **TABLE_NAME**が返されます。 この列は常に値が返されます。|  
|**COLLATION**|**char(1)**|照合順序で使用されている並べ替え順。 次の値をとります。<br /><br /> A = 昇順<br /><br /> D = 降順<br /><br /> NULL = 適用なし|  
|**カーディナリティ**|**int**|テーブル内の行数またはインデックス内の一意な値の個数。|  
|**ページ**|**int**|インデックスまたはテーブルを格納するページ数。|  
|**FILTER_CONDITION**|**varchar(128)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] では値は返されません。|  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="remarks"></a>コメント  
 結果セットのインデックス列で昇順には表示**NON_UNIQUE**、**型**、 **INDEX_NAME**、および**SEQ_IN_INDEX**します。  
  
 クラスター化インデックス型は、テーブルのデータがインデックスの順に格納されているインデックス型を指します。 これに対応して[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インデックスをクラスター化します。  
  
 ハッシュ化インデックス型は、完全一致検索または範囲検索を受け付けますが、パターン照合検索ではインデックスは使用されません。  
  
 **sp_statistics**と等価**SQLStatistics** ODBC にします。 返される結果は並べ**NON_UNIQUE**、**型**、 **INDEX_QUALIFIER**、 **INDEX_NAME**、および**SEQ_IN_インデックス**します。 詳細については、次を参照してください。、 [ODBC API リファレンス](https://go.microsoft.com/fwlink/?LinkId=68323)します。  
  
## <a name="permissions"></a>アクセス許可  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="example-includesssdwfullincludessssdwfull-mdmd-and-includesspdwincludessspdw-mdmd"></a>例:[!INCLUDE[ssSDWfull](../../includes/sssdwfull-md.md)]と [!INCLUDE[ssPDW](../../includes/sspdw-md.md)]  
 次の例では、に関する情報を返します、`DimEmployee`テーブル。  
  
```  
-- Uses AdventureWorks  
  
EXEC sp_statistics DimEmployee;  
```  
  
## <a name="see-also"></a>参照  
 [ストアド プロシージャ カタログ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/catalog-stored-procedures-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  


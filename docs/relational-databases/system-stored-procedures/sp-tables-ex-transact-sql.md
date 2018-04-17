---
title: sp_tables_ex (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_tables_ex
- sp_tables_ex_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_tables_ex
ms.assetid: 33755c33-7e1e-4ef7-af14-a9cebb1e2ed4
caps.latest.revision: 33
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: ffe5cadca156137608904aade40adba47ca83a7e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sptablesex-transact-sql"></a>sp_tables_ex (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  指定したリンク サーバーからテーブルに関するテーブル情報を返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_tables_ex [ @table_server = ] 'table_server'   
     [ , [ @table_name = ] 'table_name' ]   
     [ , [ @table_schema = ] 'table_schema' ]  
     [ , [ @table_catalog = ] 'table_catalog' ]   
     [ , [ @table_type = ] 'table_type' ]   
     [ , [@fUsePattern = ] 'fUsePattern' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@table_server=** ] **'***table_server***'**  
 テーブル情報を返すリンク サーバーの名前です。 *table_server*は**sysname**、既定値はありません。  
  
 [ **、** [  **@table_name=** ] **'***table_name***'**]  
 データ型情報を返すテーブルの名前です。 *table_name*は**sysname**、既定値は NULL です。  
  
 [  **@table_schema=** ] **'***、table_schema、***'**]  
 テーブル スキーマを指定します。 *table_schema、*は**sysname**、既定値は NULL です。  
  
 [  **@table_catalog=** ] **'***table_catalog***'**  
 対象となるデータベースの名前を指定した*table_name*が存在します。 *table_catalog*は**sysname**、既定値は NULL です。  
  
 [  **@table_type=** ] **'***table_type***'**  
 返すテーブルの種類です。 *table_type*は**sysname**NULL の場合、既定値は次の値のいずれかを持つことができます。  
  
|値|Description|  
|-----------|-----------------|  
|**エイリアス**|別名の名前です。|  
|**グローバル一時**|システム全体で使用可能な一時テーブルの名前です。|  
|**ローカルの一時**|現在のジョブでのみ使用可能な一時テーブルの名前です。|  
|**SYNONYM**|シノニムの名前です。|  
|**システム テーブル**|システム テーブルの名前です。|  
|**システム ビュー**|システム ビューの名前です。|  
|**TABLE**|ユーザー テーブルの名前です。|  
|**VIEW**|ビューの名前です。|  
  
 [  **@fUsePattern=** ] **'***fUsePattern***'**  
 決定するかどうか、文字**_**、 **%**、 **[**、および**]**ワイルドカード文字として解釈されます。 有効な値は 0 (パターン一致がオフ) および 1 (パターン一致がオン) です。 *fUsePattern*は**ビット**、既定値は 1 です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 なし  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**TABLE_CAT**|**sysname**|テーブル修飾子の名前。 さまざまな DBMS 製品は、3 部構成テーブルの名前付けをサポート (*修飾子***.***所有者***.***名前*)。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列は、データベースの名前を表します。 他のいくつかの製品では、これはテーブルのデータベース環境のサーバー名を表します。 このフィールドには NULL を指定できます。|  
|**TABLE_SCHEM**|**sysname**|テーブル所有者名です。 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、この列がテーブルを作成したデータベース ユーザーの名前を表します。 このフィールドは常に値を返します。|  
|**TABLE_NAME**|**sysname**|テーブル名です。 このフィールドは常に値を返します。|  
|**TABLE_TYPE**|**varchar (32)**|テーブル、システム テーブル、またはビューです。|  
|**「解説」**|**varchar(254)**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] この列の値を返しません。|  
  
## <a name="remarks"></a>解説  
 **sp_tables_ex**の TABLES 行セットをクエリすることによって実行される、 **IDBSchemaRowset**に対応する OLE DB プロバイダーのインターフェイス*table_server*です。 *Table_name*、 *、table_schema、*、 *table_catalog*、および*列*行を制限するには、このインターフェイスにパラメーターを渡す返されます。  
  
 **sp_tables_ex**空の結果のテーブルの行セットを指定したリンク サーバーの OLE DB プロバイダーがサポートしていない場合のセットを返します、 **IDBSchemaRowset**インターフェイスです。  
  
## <a name="permissions"></a>権限  
 スキーマに対する SELECT 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例に含まれているテーブルに関する情報を返します、`HumanResources`内のスキーマ、[!INCLUDE[ssSampleDBobject](../../includes/sssampledbobject-md.md)]上のデータベース、`LONDON2`リンク サーバー。  
  
```  
EXEC sp_tables_ex @table_server = 'LONDON2',   
@table_catalog = 'AdventureWorks2012',   
@table_schema = 'HumanResources',   
@table_type = 'TABLE';  
```  
  
## <a name="see-also"></a>参照  
 [分散クエリ ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/distributed-queries-stored-procedures-transact-sql.md)   
 [sp_catalogs &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-catalogs-transact-sql.md)   
 [sp_columns_ex &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-columns-ex-transact-sql.md)   
 [sp_column_privileges &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-column-privileges-transact-sql.md)   
 [sp_foreignkeys &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-foreignkeys-transact-sql.md)   
 [sp_indexes &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-indexes-transact-sql.md)   
 [sp_linkedservers & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-stored-procedures/sp-linkedservers-transact-sql.md)   
 [sp_table_privileges &#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/sp-table-privileges-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

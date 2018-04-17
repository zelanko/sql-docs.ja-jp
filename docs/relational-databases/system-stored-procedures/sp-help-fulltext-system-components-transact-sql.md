---
title: sp_help_fulltext_system_components (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.service: ''
ms.component: system-stored-procedures
ms.reviewer: ''
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_components_TSQL
- sp_help_fulltext_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_system_components
ms.assetid: ac1fc7a0-7f46-4a12-8c5c-8d378226a8ce
caps.latest.revision: 52
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
monikerRange: = azure-sqldw-latest || >= sql-server-2016 || = sqlallproducts-allversions
ms.openlocfilehash: 29ac6d68ff966d037f6f969d7483f3f1113fb127
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelpfulltextsystemcomponents-transact-sql"></a>sp_help_fulltext_system_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  登録済みのワード ブレーカー、フィルター、およびプロトコル ハンドラーの情報を返します。 **sp_help_fulltext_system_components**データベースや、指定されたコンポーネントを使用して、フルテキスト カタログの識別子の一覧も返します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_help_fulltext_system_components   
         { 'all'| [ @component_type = ] 'component_type' }  
    , [ @param = ] 'param'  
```  
  
## <a name="arguments"></a>引数  
 'all'  
 すべてのフルテキスト コンポーネントについての情報を返します。  
  
 [ **@component_type=** ] *component_type*  
 コンポーネントの種類を指定します。 *component_type*次のいずれかになります。  
  
-   **wordbreaker**  
  
-   **フィルター (filter)**  
  
-   **プロトコル ハンドラー**  
  
-   **fullpath**  
  
 完全パスを指定すると場合、 *param* DLL コンポーネントへの完全パスでも指定する必要がありますまたはエラー メッセージが返されます。  
  
 [ **@param=** ] *param*  
 コンポーネントの種類に応じて、ロケール識別子 (LCID)、"." プレフィックス付きのファイル拡張子、プロトコル ハンドラーの完全なコンポーネント名、または DLL コンポーネントへの完全なパスのいずれかを指定します。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または (1) の失敗  
  
## <a name="result-sets"></a>結果セット  
 システム コンポーネントについて、次の結果セットが返されます。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**componenttype**|**sysname**|コンポーネントの型。 次のいずれかです。<br /><br /> フィルター (filter)<br /><br /> protocol handler<br /><br /> wordbreaker|  
|**componentname**|**sysname**|コンポーネント名。|  
|**clsid**|**uniqueidentifier**|コンポーネントのクラス ID。|  
|**fullpath**|**nvarchar (256)**|コンポーネントの場所へのパス。<br /><br /> NULL のメンバーでない呼び出し元を = **serveradmin**固定サーバー ロール。|  
|**version**|**nvarchar(30)**|コンポーネントのバージョンです。|  
|**manufacturer**|**sysname**|コンポーネントの製造元の名前。|  
  
 1 つがある場合にのみ、次の結果セットが返されます、または 1 つ以上のフルテキスト カタログを使用してが存在する*component_type*です。  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**dbid**|**int**|データベースの ID です。|  
|**ftcatid**|**int**|フルテキスト カタログの ID です。|  
  
## <a name="permissions"></a>権限  
 メンバーシップが必要、**パブリック**ロールです。 ただし、のみを表示する対象の VIEW DEFINITION 権限がある、フルテキスト カタログに関する情報。 メンバーにのみ、 **serveradmin**に値が表示できる固定サーバー ロール、 **fullpath**列です。  
  
## <a name="remarks"></a>解説  
 アップグレードの準備をする場合、このメソッドは特に重要です。 特定のデータベース内でこのストアド プロシージャを実行し、その結果を使用して、特定のカタログがアップグレードの影響を受けているかどうかを判断します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-full-text-system-components"></a>A. フルテキスト システム コンポーネントをすべて一覧表示する  
 次の例は、サーバー インスタンスに登録されているフルテキスト システム コンポーネントをすべて一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'all';  
GO  
```  
  
### <a name="b-listing-word-breakers"></a>B. ワード ブレーカーを一覧表示する  
 次の例では、サービス インスタンスに登録されたワード ブレーカーをすべて一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'wordbreaker';  
GO  
```  
  
### <a name="c-determining-whether-a-specific-word-breaker-is-registered"></a>C. 特定のワード ブレーカーが登録されているかどうかを確認する  
 次の例では、トルコ語 (LCID = 1055) がシステムにインストールされ、サービス インスタンスに登録されている場合のトルコ語のワード ブレーカーを一覧表示します。 この例は、パラメーター名を指定**@component_type**と **@param**です。  
  
```  
EXEC sp_help_fulltext_system_components @component_type = 'wordbreaker', @param = 1055;  
GO  
```  
  
 既定では、このワード ブレーカーはインストールされていないので、結果セットは空になります。  
  
### <a name="d-determining-whether-a-specific-filter-has-been-registered"></a>D. 特定のフィルターが登録されているかどうかを確認する  
 次の例では、.xdoc コンポーネントのフィルターがシステムに手動でインストールされ、サーバー インスタンスに登録されている場合の、.xdoc コンポーネントのフィルターを一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'filter', '.xdoc';  
GO  
```  
  
 既定では、このフィルターはインストールされていないので、結果セットは空になります。  
  
### <a name="e-listing-a-specific-dll-file"></a>E. 特定の .dll ファイルを一覧表示する  
 次の例では、既定でインストールされている特定の .ddl ファイル `nlhtml.dll` を一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'fullpath',   
   'C:\Program Files\Microsoft SQL Server\MSSQL13.MSSQLSERVER\MSSQL\Binn\nlhtml.dll';  
GO  
  
```  
  
## <a name="see-also"></a>参照  
 [登録済みフィルターとワード ブレーカーの表示または変更](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)   
 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [フルテキスト検索およびセマンティック検索ストアド プロシージャの&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  

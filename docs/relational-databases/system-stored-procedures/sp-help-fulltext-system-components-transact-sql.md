---
description: sp_help_fulltext_system_components (Transact-SQL)
title: sp_help_fulltext_system_components (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine, sql-data-warehouse
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_help_fulltext_components_TSQL
- sp_help_fulltext_components
dev_langs:
- TSQL
helpviewer_keywords:
- sp_help_fulltext_system_components
ms.assetid: ac1fc7a0-7f46-4a12-8c5c-8d378226a8ce
author: CarlRabeler
ms.author: carlrab
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: 0686017e612b5d9d7d2c1f932321a965b7f1448a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88493207"
---
# <a name="sp_help_fulltext_system_components-transact-sql"></a>sp_help_fulltext_system_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  登録されているワードブレーカー、フィルター、およびプロトコルハンドラーの情報を返します。 **sp_help_fulltext_system_components** は、指定されたコンポーネントを使用したデータベースとフルテキストカタログの識別子の一覧も返します。  
  
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
  
`[ @component_type = ] component_type` コンポーネントの種類を指定します。 *component_type* には、次のいずれかを指定できます。  
  
-   **wordbreaker**  
  
-   **filter**  
  
-   **プロトコルハンドラー**  
  
-   **fullpath**  
  
 完全なパスが指定されている場合は、コンポーネント DLL への完全パスで *param* も指定する必要があります。指定しない場合、エラーメッセージが返されます。  
  
`[ @param = ] param` コンポーネントの種類に応じて、次のいずれかになります。ロケール識別子 (LCID)、"." プレフィックスが付いたファイル拡張子、プロトコルハンドラーの完全なコンポーネント名、またはコンポーネント DLL への完全パスです。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または (1) エラー  
  
## <a name="result-sets"></a>結果セット  
 システム コンポーネントについて、次の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**componenttype**|**sysname**|コンポーネントの種類。 次のいずれかになります。<br /><br /> filter<br /><br /> protocol handler<br /><br /> wordbreaker|  
|**componentname**|**sysname**|コンポーネント名。|  
|**clsid**|**uniqueidentifier**|コンポーネントのクラス ID。|  
|**fullpath**|**nvarchar (256)**|コンポーネントの場所へのパス。<br /><br /> NULL = 呼び出し元は、 **serveradmin** 固定サーバーロールのメンバーではありません。|  
|**version**|**nvarchar(30)**|コンポーネントのバージョン。|  
|**manufacturer**|**sysname**|コンポーネントの製造元の名前。|  
  
 *Component_type*を使用するフルテキストカタログが1つ以上存在する場合にのみ、次の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**dbid**|**int**|データベースの ID です。|  
|**ftcatid**|**int**|フルテキストカタログの ID。|  
  
## <a name="permissions"></a>アクセス許可  
 **Public**ロールのメンバーシップが必要です。ただし、ユーザーは、VIEW DEFINITION 権限を持つフルテキストカタログに関する情報のみを表示できます。 **Serveradmin**固定サーバーロールのメンバーだけが、 **fullpath**列の値を参照できます。  
  
## <a name="remarks"></a>解説  
 この方法は、アップグレードを準備するときに特に重要です。 特定のデータベース内でストアドプロシージャを実行し、その出力を使用して、アップグレードによって特定のカタログが影響を受けるかどうかを判断します。  
  
## <a name="examples"></a>例  
  
### <a name="a-listing-all-full-text-system-components"></a>A. フルテキスト システム コンポーネントをすべて一覧表示する  
 次の例は、サーバー インスタンスに登録されているフルテキスト システム コンポーネントをすべて一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'all';  
GO  
```  
  
### <a name="b-listing-word-breakers"></a>B. ワード ブレーカーを一覧表示する  
 次の例では、サービスインスタンスに登録されているすべてのワードブレーカーを一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'wordbreaker';  
GO  
```  
  
### <a name="c-determining-whether-a-specific-word-breaker-is-registered"></a>C. 特定のワード ブレーカーが登録されているかどうかを確認する  
 次の例では、トルコ語 (LCID = 1055) がシステムにインストールされ、サービス インスタンスに登録されている場合のトルコ語のワード ブレーカーを一覧表示します。 この例では、パラメーター名、 ** \@ component_type**および** \@ param**を指定します。  
  
```  
EXEC sp_help_fulltext_system_components @component_type = 'wordbreaker', @param = 1055;  
GO  
```  
  
 既定では、このワードブレーカーはインストールされていないため、結果セットは空になります。  
  
### <a name="d-determining-whether-a-specific-filter-has-been-registered"></a>D. 特定のフィルターが登録されているかどうかを確認する  
 次の例では、システムに手動でインストールされ、サーバーインスタンスに登録されている場合、xdoc コンポーネントのフィルターを一覧表示します。  
  
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
 [登録済みのフィルターとワードブレーカーを表示または変更する](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)   
 [検索用のワードブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [検索用のフィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [Transact-sql&#41;&#40;のフルテキスト検索およびセマンティック検索ストアドプロシージャ ](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  

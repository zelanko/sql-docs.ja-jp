---
title: sp_help_fulltext_system_components (TRANSACT-SQL) |Microsoft Docs
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
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
monikerRange: =azure-sqldw-latest||>=sql-server-2016||=sqlallproducts-allversions||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: b8090ea1080fa7528d3a8297e14760190e8aadfe
ms.sourcegitcommit: 5ed48c7dc6bed153079bc2b23a1e0506841310d1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/21/2019
ms.locfileid: "65980255"
---
# <a name="sphelpfulltextsystemcomponents-transact-sql"></a>sp_help_fulltext_system_components (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-asdw-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-asdw-xxx-md.md)]

  登録済みのワード ブレーカー、フィルター、およびプロトコル ハンドラーの情報を返します。 **sp_help_fulltext_system_components**もデータベースや、指定したコンポーネントを使用しているフルテキスト カタログの識別子の一覧を返します。  
  
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
  
`[ @component_type = ] component_type` コンポーネントの種類を指定します。 *component_type*次のいずれかを指定できます。  
  
-   **wordbreaker**  
  
-   **フィルター (filter)**  
  
-   **プロトコル ハンドラー**  
  
-   **fullpath**  
  
 完全なパスが指定されている場合*param* DLL コンポーネントへの完全パスも指定する必要がありますまたはエラー メッセージが返されます。  
  
`[ @param = ] param` コンポーネントの種類に応じてこれは、次のいずれか: ロケール識別子 (LCID) を使用して、ファイル拡張子"."プロトコル ハンドラー、または DLL コンポーネントへの完全なパスの完全なコンポーネント名のプレフィックスします。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または (1) の失敗  
  
## <a name="result-sets"></a>結果セット  
 システム コンポーネントについて、次の結果セットが返されます。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**componenttype**|**sysname**|コンポーネントの型。 次のいずれかです。<br /><br /> フィルター (filter)<br /><br /> protocol handler<br /><br /> wordbreaker|  
|**componentname**|**sysname**|コンポーネント名。|  
|**clsid**|**uniqueidentifier**|コンポーネントのクラス ID。|  
|**fullpath**|**nvarchar (256)**|コンポーネントの場所へのパス。<br /><br /> NULL のメンバーでない呼び出し元を = **serveradmin**固定サーバー ロール。|  
|**version**|**nvarchar(30)**|コンポーネントのバージョンです。|  
|**manufacturer**|**sysname**|コンポーネントの製造元の名前です。|  
  
 1 つがある場合にのみ、次の結果セットが返される、または 1 つ以上のフルテキスト カタログを使用してが存在する*component_type*します。  
  
|列名|データ型|説明|  
|-----------------|---------------|-----------------|  
|**dbid**|**int**|データベースの ID です。|  
|**ftcatid**|**int**|フルテキスト カタログの ID。|  
  
## <a name="permissions"></a>アクセス許可  
 メンバーシップが必要です、**パブリック**ロールです。 ただし、ユーザーには VIEW DEFINITION 権限がある、フルテキスト カタログに関する情報が表示できるのみです。 メンバーのみ、 **serveradmin**固定サーバー ロールが内の値を参照してください、 **fullpath**列。  
  
## <a name="remarks"></a>コメント  
 アップグレードを準備するときにこのメソッドは特に重要です。 特定のデータベース内でストアド プロシージャを実行し、出力を使用して、アップグレード、特定のカタログの影響を受けるかどうかを判断します。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-all-full-text-system-components"></a>A. フルテキスト システム コンポーネントをすべて一覧表示する  
 次の例は、サーバー インスタンスに登録されているフルテキスト システム コンポーネントをすべて一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'all';  
GO  
```  
  
### <a name="b-listing-word-breakers"></a>B. ワード ブレーカーを一覧表示する  
 次の例は、サービス インスタンスに登録されているすべてのワード ブレーカーを一覧表示します。  
  
```  
EXEC sp_help_fulltext_system_components 'wordbreaker';  
GO  
```  
  
### <a name="c-determining-whether-a-specific-word-breaker-is-registered"></a>C. 特定のワード ブレーカーが登録されているかどうかを確認する  
 次の例では、トルコ語 (LCID = 1055) がシステムにインストールされ、サービス インスタンスに登録されている場合のトルコ語のワード ブレーカーを一覧表示します。 この例では、パラメーターの名前を指定します。 **@component_type**と **@param**します。  
  
```  
EXEC sp_help_fulltext_system_components @component_type = 'wordbreaker', @param = 1055;  
GO  
```  
  
 既定では、このワード ブレーカーがインストールされていないので、結果セットは空。  
  
### <a name="d-determining-whether-a-specific-filter-has-been-registered"></a>D. 特定のフィルターが登録されているかどうかを確認する  
 次の例では、ことが手動でシステムにインストールされ、サーバー インスタンスに登録されている場合、.xdoc コンポーネントのフィルターが一覧表示します。  
  
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
 [登録済みフィルターおよびワード ブレーカーの表示または変更](../../relational-databases/search/view-or-change-registered-filters-and-word-breakers.md)   
 [検索用のワード ブレーカーとステミング機能の構成と管理](../../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)   
 [検索用フィルターの構成と管理](../../relational-databases/search/configure-and-manage-filters-for-search.md)   
 [フルテキスト検索およびセマンティック検索ストアド プロシージャ&#40;TRANSACT-SQL&#41;](../../relational-databases/system-stored-procedures/full-text-search-and-semantic-search-stored-procedures-transact-sql.md)  
  
  

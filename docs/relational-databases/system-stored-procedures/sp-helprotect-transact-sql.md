---
title: sp_helprotect (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/15/2017
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
- sp_helprotect
- sp_helprotect_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_helprotect
ms.assetid: faaa3e40-1c95-43c2-9fdc-c61a1d3cc0c3
caps.latest.revision: 24
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: On Demand
ms.openlocfilehash: 3e0942b8d2b66a76db9e50616f63d6d7a3cc959e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="sphelprotect-transact-sql"></a>sp_helprotect (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のデータベースにおける、オブジェクトに対するユーザー権限、またはステートメント権限に関する情報のレポートを返します。  
  
> [!IMPORTANT]  
>  **sp_helprotect**で導入されたセキュリティ保護可能な情報を返さない[!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]です。 使用して[sys.database_permissions](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)と[fn_builtin_permissions](../../relational-databases/system-functions/sys-fn-builtin-permissions-transact-sql.md)代わりにします。  
  
 固定サーバー ロールまたは固定データベース ロールに常に割り当てられる権限は表示されません。 ロールのメンバーシップに基づいて権限が与えられるログインまたはユーザーは含まれません。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
sp_helprotect [ [ @name = ] 'object_statement' ]   
     [ , [ @username = ] 'security_account' ]   
     [ , [ @grantorname = ] 'grantor' ]   
     [ , [ @permissionarea = ] 'type' ]  
```  
  
## <a name="arguments"></a>引数  
 [  **@name =** ] **'***object_statement***'**  
 レポートする権限が存在する、現在のデータベースのオブジェクトまたはステートメントの名前を指定します *object_statement*は**nvarchar (776)**の既定値は NULL には、すべてのオブジェクトとステートメントの権限が返されます。 値がオブジェクト (テーブル、ビュー、ストアド プロシージャ、または拡張ストアド プロシージャ) の場合は、現在のデータベース内の有効なオブジェクトであることが必要です。 オブジェクト名は、フォームで、所有者の修飾子を含めることができます*所有者***.***オブジェクト*です。  
  
 場合*object_statement*ステートメント、CREATE ステートメントであることができます。  
  
 [  **@username =** ] **'***これ***'**  
 レポートされる権限に関連するプリンシパルの名前を指定します。 *これ*は**sysname**の既定値は NULL には、現在のデータベース内のすべてのプリンシパルが返されます。 *これ*現在のデータベースに存在する必要があります。  
  
 [  **@grantorname =** ] **'***grantor***'**  
 権限を許可したプリンシパルの名前を指定します。 *権限の許可者*は**sysname**の既定値は NULL には、データベース内のすべてのプリンシパルにより許可された権限のすべての情報が返されます。  
  
 [ **@permissionarea =** ] **'***type***'**  
 オブジェクトのアクセス許可を表示するかどうかを示す文字の文字列 (文字の文字列**o**)、ステートメント権限 (文字の文字列**s**)、またはその両方 (**os**)。 *型*は**varchar (10)**、既定値は**os**です。 *型*の組み合わせにすることができます**o**と**s**、または間の空白またはコンマなしの**o**と**s**です。  
  
## <a name="return-code-values"></a>リターン コードの値  
 0 (成功) または 1 (失敗)  
  
## <a name="result-sets"></a>結果セット  
  
|列名|データ型|Description|  
|-----------------|---------------|-----------------|  
|**所有者**|**sysname**|オブジェクト所有者の名前。|  
|**オブジェクト**|**sysname**|オブジェクトの名前。|  
|**権限付与対象ユーザー**|**sysname**|権限が許可されたプリンシパルの名前。|  
|**Grantor**|**sysname**|指定したユーザーに権限を許可したプリンシパルの名前。|  
|**ProtectType**|**nvarchar(10)**|保護の種類の名前。<br /><br /> GRANT REVOKE|  
|**操作**|**nvarchar(60)**|アクセス許可の名前です。 有効な権限ステートメントは、オブジェクトの種類によって異なります。|  
|**列**|**sysname**|アクセス許可の種類です。<br /><br /> All = オブジェクトの現在の列すべてに対する権限<br /><br /> New = 今後 ALTER ステートメントを使用して変更される可能性のある、オブジェクトの新しい列に対する権限<br /><br /> All+New = All と New を組み合わせた権限<br /><br /> 権限の種類が列に適用されない場合は、ピリオドを返します。|  
  
## <a name="remarks"></a>解説  
 次のプロシージャでは、すべてのパラメーターが省略可能です。 パラメーターなしで実行される場合`sp_helprotect`現在のデータベースで許可または拒否されているすべての権限を表示します。  
  
 すべてではなく一部のパラメーターだけを指定する場合は、特定のパラメーターを示す名前付きのパラメーターを使用するか、プレースホルダーとして `NULL` を使用します。 例については、データベース所有者のすべての権限をレポートする (`dbo`)、次を実行します。  
  
```  
EXEC sp_helprotect NULL, NULL, dbo;  
```  
  
 または  
  
```  
EXEC sp_helprotect @grantorname = 'dbo';  
```  
  
 レポートは、権限カテゴリ、所有者、オブジェクト、被許可者、許可者、保護の種類のカテゴリ、保護の種類、動作、列順序 ID で並べ替えられます。  
  
## <a name="permissions"></a>権限  
 ロール **public** のメンバーシップが必要です。  
  
 返される情報は、メタデータへのアクセスに関する制限の対象となります。 プリンシパルに権限がないエンティティは表示されません。 詳細については、「 [Metadata Visibility Configuration](../../relational-databases/security/metadata-visibility-configuration.md)」を参照してください。  
  
## <a name="examples"></a>使用例  
  
### <a name="a-listing-the-permissions-for-a-table"></a>A. テーブルに対する権限を一覧表示する  
 次の例では、テーブル `titles` の権限に関するレポートを一覧表示します。  
  
```  
EXEC sp_helprotect 'titles';  
```  
  
### <a name="b-listing-the-permissions-for-a-user"></a>B. ユーザーに対する権限を一覧表示する  
 次の例はそのユーザーのすべての権限を一覧表示`Judy`に現在のデータベースが含まれています。  
  
```  
EXEC sp_helprotect NULL, 'Judy';  
```  
  
### <a name="c-listing-the-permissions-granted-by-a-specific-user"></a>C. 特定のユーザーに許可されている権限を一覧表示する  
 次の例では、現在のデータベース内でユーザー `Judy` に許可されたすべての権限を一覧表示します。指定しないパラメーターについては、プレースホルダーとして `NULL` を使用します。  
  
```  
EXEC sp_helprotect NULL, NULL, 'Judy';  
```  
  
### <a name="d-listing-the-statement-permissions-only"></a>D. ステートメント権限だけを一覧表示する  
 次の例では、現在のデータベース内のすべてのステートメント権限を表示します。指定しないパラメーターについては、プレースホルダーとして `NULL` を使用します。  
  
```  
EXEC sp_helprotect NULL, NULL, NULL, 's';   
```  
  
### <a name="e-listing-the-permissions-for-a-create-statement"></a>e. CREATE ステートメントの権限だけを一覧表示する  
 次の例では、CREATE TABLE 権限が与えられたすべてのユーザーを一覧表示します。  
  
```  
EXEC sp_helprotect @name = 'CREATE TABLE';  
```  
  
## <a name="see-also"></a>参照  
 [セキュリティ ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/security-stored-procedures-transact-sql.md)   
 [DENY &#40;Transact-SQL&#41;](../../t-sql/statements/deny-transact-sql.md)   
 [GRANT &#40;Transact-SQL&#41;](../../t-sql/statements/grant-transact-sql.md)   
 [REVOKE &#40;Transact-SQL&#41;](../../t-sql/statements/revoke-transact-sql.md)   
 [システム ストアド プロシージャ &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/system-stored-procedures-transact-sql.md)  
  
  

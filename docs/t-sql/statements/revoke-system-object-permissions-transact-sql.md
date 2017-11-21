---
title: "システム オブジェクトの権限 (TRANSACT-SQL) を取り消す |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: sql-database
ms.service: 
ms.component: t-sql|statements
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- TSQL
helpviewer_keywords:
- REVOKE statement, system objects
- permissions [SQL Server], system objects
ms.assetid: 84983238-dd7d-45bd-99bb-52c9d8e96a87
caps.latest.revision: 20
author: edmacauley
ms.author: edmaca
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 17b371e839d27c065628def8a7be56e6bef650a0
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="revoke-system-object-permissions-transact-sql"></a>REVOKE (システム オブジェクトの権限の取り消し) (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  ストアド プロシージャ、拡張ストアド プロシージャ、関数、ビューなどのシステム オブジェクトに対する権限を、プリンシパルから取り消します。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```  
  
REVOKE { SELECT | EXECUTE } ON [sys.]system_object FROM principal   
```  
  
## <a name="arguments"></a>引数  
 [**sys です。**] .  
 **Sys**カタログ ビューおよび動的管理ビューを参照している場合にのみ、修飾子が必要です。  
  
 *system_object*  
 権限を取り消すオブジェクトを指定します。  
  
 *プリンシパル*  
 権限を取り消すプリンシパルを指定します。  
  
## <a name="remarks"></a>解説  
 このステートメントは、特定ストアド プロシージャ、拡張ストアド プロシージャ、テーブル値関数、スカラー関数、ビュー、カタログ ビュー、互換ビュー、INFORMATION_SCHEMA ビュー、動的管理ビュー、およびシステムに対する権限を取り消すために使用できます。によってインストールされているテーブル[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 Resource データベースに一意なレコードとして存在するこれらのシステム オブジェクトの各 (**mssqlsystemresource**)。 リソース データベースは読み取り専用です。 オブジェクトへのリンクが内のレコードとして公開されている、 **sys**すべてのデータベースのスキーマです。  
  
 既定の名前解決では、修飾子のないプロシージャ名はリソース データベースとして解釈されます。 したがって、 **sys です。** 修飾子は、カタログ ビューと動的管理ビューを指定する場合にのみ必要です。  
  
> [!CAUTION]  
>  システム オブジェクトに対する権限を取り消すと、そのシステム オブジェクトに依存するアプリケーションは失敗します。 [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]使用してでは、カタログ ビューおよびカタログ ビューの既定のアクセス許可を変更するかどうかは、正常に機能しない可能性があります。  
  
 システム オブジェクトのトリガーおよび列に対する権限の取り消しはサポートされていません。  
  
 アップグレード中にシステム オブジェクトに対する権限は保持されます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 システム オブジェクトは、 [sys.system_objects](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md) カタログ ビューで確認できます。  
  
## <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では失効`EXECUTE`に対する権限`sp_addlinkedserver`から`public`です。  
  
```  
REVOKE EXECUTE ON sys.sp_addlinkedserver FROM public;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [sys.system_objects & #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-system-objects-transact-sql.md)   
 [sys.database_permissions および #40 です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-database-permissions-transact-sql.md)   
 [システム オブジェクトの権限 &#40; を許可します。TRANSACT-SQL と #41 です。](../../t-sql/statements/grant-system-object-permissions-transact-sql.md)   
 [システム オブジェクトの権限 &#40; を拒否します。TRANSACT-SQL と #41 です。](../../t-sql/statements/deny-system-object-permissions-transact-sql.md)  
  
  


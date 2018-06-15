---
title: sys.fulltext_semantic_language_statistics_database (TRANSACT-SQL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.component: system-catalog-views
ms.reviewer: ''
ms.suite: sql
ms.technology: system-objects
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- sys.fulltext_semantic_language_statistics_database_TSQL
- fulltext_semantic_language_statistics_database_TSQL
- fulltext_semantic_language_statistics_database
- sys.fulltext_semantic_language_statistics_database
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_language_statistics_database catalog view
ms.assetid: 32e95614-ed88-4068-8c37-1e21544717bc
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e5e84ee0b65a38766f7d6a58e0488cb98c1b7a99
ms.sourcegitcommit: f1caaa156db2b16e817e0a3884394e7b30fb642f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33180098"
---
# <a name="sysfulltextsemanticlanguagestatisticsdatabase-transact-sql"></a>sys.fulltext_semantic_language_statistics_database (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  現在のインスタンスにインストールされているセマンティック言語統計データベースに関する行を返します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 このビューに対するクエリを実行して、セマンティックな処理のために必要なセマンティック言語統計コンポーネントについて確認できます。  
   
  
||||  
|-|-|-|  
|**列名**|**型**|**Description**|  
|**database_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意のデータベースの ID です。|  
|**register_date**|**datetime**|セマンティックな処理にデータベースが登録された日付です。|  
|**registered_by**|**int**|セマンティックな処理にデータベースを登録したサーバー プリンシパルの ID です。|  
|**version**|**nvarchar(128)**|セマンティック言語統計データベースに固有の、最新のバージョン情報です。|  
  
## <a name="general-remarks"></a>全般的な解説  
 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 セマンティック インデックス作成でサポートされている言語については、カタログ ビューに対してクエリ[sys.fulltext_semantic_languages &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)です。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。  
  
## <a name="examples"></a>使用例  
 次の例を照会する方法**sys.fulltext_semantic_language_statistics_database**の現在のインスタンスに登録されているセマンティック言語統計データベースに関する情報を取得する[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

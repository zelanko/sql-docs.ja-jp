---
title: "sys.fulltext_semantic_languages (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-catalog-views
ms.reviewer: 
ms.suite: sql
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- fulltext_semantic_languages
- fulltext_semantic_languages_TSQL
- sys.fulltext_semantic_languages
- sys.fulltext_semantic_languages_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sys.fulltext_semantic_languages catalog view
ms.assetid: b42a85e6-1db9-4a22-8a70-014574c95198
caps.latest.revision: 
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 109bd4b37a3cd6b243fb1ce8bf05ba33e6c71ea1
ms.sourcegitcommit: c556eaf60a49af7025db35b7aa14beb76a8158c5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/03/2018
---
# <a name="sysfulltextsemanticlanguages-transact-sql"></a>sys.fulltext_semantic_languages (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  統計モデルが [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスに登録されている各言語の行を返します。 言語モデルが登録されている場合、その言語はセマンティック インデックス作成に対応しています。  
  
 このカタログ ビューがに似ていますが[sys.fulltext_languages &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-fulltext-languages-transact-sql.md)。  
    
||||  
|-|-|-|  
|**列名**|**型**|**Description**|  
|lcid|int|言語の Microsoft Windows ロケール識別子 (LCID) です。|  
|name|sysname|内の別名のいずれかの値は、 [sys.syslanguages &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-compatibility-views/sys-syslanguages-transact-sql.md)の値に対応する**lcid**、または LCID の数値の文字列形式。|  
  
## <a name="general-remarks"></a>全般的な解説  
 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 セマンティック インデックス作成をサポートするためにインストールされているセマンティック言語統計データベースに関する詳細については、カタログ ビューに対してクエリ[sys.fulltext_semantic_language_statistics_database &#40;です。TRANSACT-SQL と #41 です](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>権限  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。  
  
## <a name="examples"></a>使用例  
 次の例を照会する方法**sys.fulltext_semantic_languages**情報を取得するための言語モデルが登録されているすべての現在のインスタンスでセマンティック インデックス作成[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
```  
SELECT * FROM sys.fulltext_semantic_languages;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

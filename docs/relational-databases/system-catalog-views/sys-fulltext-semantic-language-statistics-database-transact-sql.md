---
title: fulltext_semantic_language_statistics_database (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.technology: system-objects
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
author: pmasl
ms.author: pelopes
ms.reviewer: mikeray
ms.openlocfilehash: 0decfac8cf28727a3ba3f4bf5ad54e8f9ff8bee9
ms.sourcegitcommit: f7ac1976d4bfa224332edd9ef2f4377a4d55a2c9
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2020
ms.locfileid: "85902179"
---
# <a name="sysfulltext_semantic_language_statistics_database-transact-sql"></a>fulltext_semantic_language_statistics_database (Transact-sql)
[!INCLUDE [SQL Server](../../includes/applies-to-version/sqlserver.md)]

  の現在のインスタンスにインストールされているセマンティック言語統計データベースに関する行を返し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
 このビューに対してクエリを実行すると、セマンティック処理に必要なセマンティック言語統計コンポーネントについて調べることができます。  
   
  
||||  
|-|-|-|  
|**列名**|**Type**|**説明**|  
|**database_id**|**int**|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンス内で一意のデータベースの ID です。|  
|**register_date**|**datetime**|データベースがセマンティック処理用に登録された日付。|  
|**registered_by**|**int**|セマンティック処理のためにデータベースを登録したサーバープリンシパルの ID。|  
|**version**|**nvarchar(128)**|セマンティック言語統計データベースに固有の最新バージョン情報。|  
  
## <a name="general-remarks"></a>全般的な解説  
 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>Metadata  
 セマンティックインデックス作成でサポートされている言語の詳細については、カタログビューの[fulltext_semantic_languages &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-languages-transact-sql.md)を参照してください。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 カタログ ビューでのメタデータの表示が、ユーザーが所有しているかそのユーザーが権限を許可されている、セキュリティ保護可能なメタデータに制限されます。  
  
## <a name="examples"></a>例  
 次の例では、の現在のインスタンスに登録されているセマンティック言語統計データベースに関する情報を取得するために、 **fulltext_semantic_language_statistics_database**のクエリを実行する方法を示し [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ます。  
  
```  
SELECT * FROM sys.fulltext_semantic_language_statistics_database;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

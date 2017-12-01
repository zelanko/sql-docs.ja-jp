---
title: "sp_fulltext_semantic_unregister_language_statistics_db (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.service: 
ms.component: system-stored-procedures
ms.reviewer: 
ms.suite: sql
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db_TSQL
- sp_fulltext_semantic_unregister_language_statistics_db
dev_langs: TSQL
helpviewer_keywords: sp_fulltext_semantic_unregister_language_statistics_db
ms.assetid: 1426ca4a-9a76-489e-98da-8f6d13ff9732
caps.latest.revision: "11"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: f8798d626a64a56d1dd57222abea1458347b01f5
ms.sourcegitcommit: 9fbe5403e902eb996bab0b1285cdade281c1cb16
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/27/2017
---
# <a name="spfulltextsemanticunregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_unregister_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のセマンティック言語統計データベースの現在のインスタンスからの登録を解除[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、関連付けられているメタデータを削除します。  
  
 このステートメントが、データベースをデタッチしたり、ファイル システムから物理的なデータベース ファイルを削除することはありません。 データベースの登録の解除後は、それをデタッチし、物理的なデータベース ファイルを削除することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```tsql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
##  <a name="Arguments"></a> 引数  
 このプロシージャは、引数を必要としません。 インスタンスから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]は 1 つだけセマンティック言語統計データベースは、データベースを特定するために必要です。  
  
## <a name="return-code-value"></a>リターン コード値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
 [なし] :  
  
## <a name="general-remarks"></a>全般的な解説  
 セマンティック言語統計データベースの登録が解除されると、それに関連付けられているすべてのメタデータも削除されます。  
  
 **sp_fulltext_semantic_unregister_language_statistics_db**は、次の手順を実行します。  
  
1.  現在のインスタンスに対して進行中のセマンティックな作成処理がないことを確認[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
2.  指定されたセマンティック言語統計データベースに関連付けられているすべてのメタデータを削除します。  
  
 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 インスタンスにインストールされているセマンティック言語統計データベースに関する情報の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、カタログ ビューに対してクエリを[sys.fulltext_semantic_language_statistics_database &#40;です。TRANSACT-SQL と #41 です;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>Permissions  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、呼び出すことによって、セマンティック言語統計データベースを登録解除する方法を示しています。 **sp_fulltext_semantic_unregister_language_statistics_db**です。  
  
```tsql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

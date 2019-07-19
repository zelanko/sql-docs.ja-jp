---
title: sp_fulltext_semantic_unregister_language_statistics_db (TRANSACT-SQL) |Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db_TSQL
- sp_fulltext_semantic_unregister_language_statistics_db
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_unregister_language_statistics_db
ms.assetid: 1426ca4a-9a76-489e-98da-8f6d13ff9732
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 7d0443190e3febdb2730c7c8b8bc06786daf6fe7
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68124247"
---
# <a name="spfulltextsemanticunregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_unregister_language_statistics_db (TRANSACT-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  既存のセマンティック言語統計データベースの現在のインスタンスからの登録を解除します[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]し、関連付けられているメタデータを削除します。  
  
 このステートメントはいないデータベースをデタッチします。 または、ファイル システムから物理的なデータベース ファイルを削除します。 データベースの登録の解除後は、それをデタッチし、物理的なデータベース ファイルを削除することができます。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
##  <a name="Arguments"></a> 引数  
 このプロシージャは、引数を必要としません。 インスタンスから[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]1 つしかセマンティック言語統計データベースを必要はありません、データベースを識別するためにします。  
  
## <a name="return-code-value"></a>リターン コード値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
 [なし] :  
  
## <a name="general-remarks"></a>全般的な解説  
 セマンティック言語統計データベースの登録が解除されると、それに関連付けられているすべてのメタデータも削除されます。  
  
 **sp_fulltext_semantic_unregister_language_statistics_db**は、次の手順を実行します。  
  
1.  現在のインスタンスに対して進行中のセマンティックな作成処理がないことを確認します。[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]します。  
  
2.  指定されたセマンティック言語統計データベースに関連付けられているすべてのメタデータを削除します。  

[!INCLUDE[freshInclude](../../includes/paragraph-content/fresh-note-steps-feedback.md)]

 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 インスタンスにインストールされているセマンティック言語統計データベースに関する情報の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、カタログ ビューに対してクエリ[sys.fulltext_semantic_language_statistics_database &#40;TRANSACT-SQL&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)します。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、呼び出すことによって、セマンティック言語統計データベースを登録解除する方法を示しています。 **sp_fulltext_semantic_unregister_language_statistics_db**します。  
  
```sql  
EXEC sp_fulltext_semantic_unregister_language_statistics_db;  
GO  
```  
  
## <a name="see-also"></a>関連項目  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

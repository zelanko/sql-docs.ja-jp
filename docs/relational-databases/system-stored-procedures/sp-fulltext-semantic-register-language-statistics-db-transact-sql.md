---
title: sp_fulltext_semantic_register_language_statistics_db (Transact-sql) |Microsoft Docs
ms.custom: ''
ms.date: 06/10/2016
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: system-objects
ms.topic: language-reference
f1_keywords:
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs:
- TSQL
helpviewer_keywords:
- sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
author: MikeRayMSFT
ms.author: mikeray
ms.openlocfilehash: 59cf70574a73827887542221f556e65e46090395
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "68124209"
---
# <a name="sp_fulltext_semantic_register_language_statistics_db-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-sql)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスで、事前にデータが設定されているセマンティック言語統計データベースを登録します。  
  
 セマンティック抽出は、この言語統計データベースをアタッチし、このストアドプロシージャを使用して登録した後にのみ開始できます。 このタスクは、の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスごとに1回だけ実行する必要があります。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] 'database_name';  
GO  
```  
  
##  <a name="arguments"></a><a name="Arguments"></a>数値  
 [ @dbname = ]'*database_name*'  
 の現在の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに登録するセマンティック言語統計データベースの名前を指定します。 データベースが既にアタッチされている必要があります。 *database_name*は**sysname**であり、NULL にすることはできません。  
  
## <a name="return-code-value"></a>リターン コード値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
 なし。  
  
## <a name="general-remarks"></a>全般的な解説  
 セマンティック言語統計データベースには、テキストコンテンツのセマンティック処理に必要な言語関連の統計情報が含まれています。  
  
 **sp_fulltext_semantic_register_language_statistics_db**では、次の手順を実行します。  
  
1.  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスがセマンティック処理をサポートするバージョンであることを確認します。  
  
2.  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスに、セマンティック言語統計データベースが定義されていないことを確認します。  
  
3.  データベースが有効なセマンティック言語統計データベースであることを確認します。  
  
4.  セマンティック言語統計データベースに対する権限を設定して、ユーザーによるデータベースへのアクセスを制限します。  
  
5.  の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスのセマンティック言語統計データベースの名前を定義するメタデータを挿入します。  
  
6.  インストールされているセマンティック言語統計データベースと内部言語モデルテーブル間のマッピングを定義するメタデータを挿入します。  
  
7.  データベースを使用する準備ができているかどうかを確認します。  
  
 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>Metadata  
 の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]インスタンスにインストールされているセマンティック言語統計データベースの詳細については、カタログビューの[fulltext_semantic_language_statistics_database &#40;transact-sql&#41;](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md)に対してクエリを実行します。  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例では、 **sp_fulltext_semantic_register_language_statistics_db**を呼び出して、セマンティック言語統計データベースを登録する方法を示します。  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

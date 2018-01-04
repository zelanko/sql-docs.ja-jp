---
title: "sp_fulltext_semantic_register_language_statistics_db (TRANSACT-SQL) |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/10/2016
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
- sp_fulltext_semantic_register_language_statistics_db
- sp_fulltext_semantic_register_language_statistics_db_TSQL
dev_langs: TSQL
helpviewer_keywords: sp_fulltext_semantic_register_language_statistics_db
ms.assetid: bef1b104-5a44-4327-9ae4-45eae3000f7e
caps.latest.revision: "12"
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7036aeab4ff8573e07d27aae1b1b486bd5b34fe0
ms.sourcegitcommit: 2208a909ab09af3b79c62e04d3360d4d9ed970a7
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/02/2018
---
# <a name="spfulltextsemanticregisterlanguagestatisticsdb-transact-sql"></a>sp_fulltext_semantic_register_language_statistics_db (Transact-SQL)
[!INCLUDE[tsql-appliesto-ss2008-xxxx-xxxx-xxx-md](../../includes/tsql-appliesto-ss2008-xxxx-xxxx-xxx-md.md)]

  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] の現在のインスタンスで、事前にデータが設定されているセマンティック言語統計データベースを登録します。  
  
 セマンティックな抽出は、この言語統計データベースをアタッチし、このストアド プロシージャを使用して登録した後でのみ開始できます。 各インスタンスにつき 1 回このタスクを実行するだけ済みます[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
 ![トピック リンク アイコン](../../database-engine/configure-windows/media/topic-link.gif "トピック リンク アイコン") [Transact-SQL 構文表記規則](../../t-sql/language-elements/transact-sql-syntax-conventions-transact-sql.md)  
  
## <a name="syntax"></a>構文  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db  
    [ @dbname = ] ‘database_name’;  
GO  
```  
  
##  <a name="Arguments"></a> 引数  
 [ @dbname =] '*database_name*'  
 現在のインスタンスに登録するセマンティック言語統計データベースの名前を指定[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。 データベースが既にアタッチされている必要があります。 *database_name*は**sysname**NULL ができない場合があります。  
  
## <a name="return-code-value"></a>リターン コード値  
 **0** (成功) または**1** (失敗)  
  
## <a name="result-set"></a>結果セット  
 [なし] :  
  
## <a name="general-remarks"></a>全般的な解説  
 セマンティック言語統計データベースには、テキスト コンテンツのセマンティックな処理に必要な、言語関連の統計が格納されます。  
  
 **sp_fulltext_semantic_register_language_statistics_db**は、次の手順を実行します。  
  
1.  確認のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]セマンティックな処理をサポートしているバージョンします。  
  
2.  確認のインスタンス[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]まだ定義されているセマンティック言語統計データベースがないです。  
  
3.  データベースが有効なセマンティック言語統計データベースであることを確認します。  
  
4.  ユーザーによるセマンティック言語統計データベースへのアクセスを制限するために、データベースに対する権限を設定します。  
  
5.  インスタンスにセマンティック言語統計データベースの名前を定義するメタデータを挿入[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]です。  
  
6.  インストールされたセマンティック言語統計データベースと内部言語モデル テーブル間のマッピングを定義するメタデータを挿入します。  
  
7.  データベースが使用可能な状態であることを確認します。  
  
 詳細については、「 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)」を参照してください。  
  
## <a name="metadata"></a>メタデータ  
 インスタンスにインストールされているセマンティック言語統計データベースに関する情報の[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]、カタログ ビューに対してクエリを[sys.fulltext_semantic_language_statistics_database &#40;です。TRANSACT-SQL と #41 です。](../../relational-databases/system-catalog-views/sys-fulltext-semantic-language-statistics-database-transact-sql.md).  
  
## <a name="security"></a>Security  
  
### <a name="permissions"></a>アクセス許可  
 CONTROL SERVER 権限が必要です。  
  
## <a name="examples"></a>使用例  
 次の例は、呼び出すことによって、セマンティック言語統計データベースを登録する方法を示しています。 **sp_fulltext_semantic_register_language_statistics_db**です。  
  
```sql  
EXEC sp_fulltext_semantic_register_language_statistics_db @dbname = 'semanticsDb';  
GO  
```  
  
## <a name="see-also"></a>参照  
 [セマンティック検索のインストールと構成](../../relational-databases/search/install-and-configure-semantic-search.md)  
  
  

---
title: 新しいフルテキスト ストップ リスト ([全般] ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
caps.latest.revision: 16
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 5217bd995855ff33e6b21b883c854cb3db474e03
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36085282"
---
# <a name="new-full-text-stoplist-general-page"></a>[新しいフルテキスト ストップリスト] ([全般] ページ)
  このダイアログ ボックスを使用すると、フルテキスト ストップリストを作成できます。 *ストップリスト* とは、一般的に使用される単語のセットのことです。これらの単語は *ストップワード*と呼ばれ、ストップリストを使用するテーブルのフルテキスト インデックスから省略されます。 詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)」を参照してください。  
  
 **SQL Server Management Studio を使用してストップ リストを作成するには**  
  
-   [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>および  
 **フルテキスト ストップ リスト名**  
 フルテキスト ストップリストの名前を入力します。  
  
 **[所有者]**  
 フルテキスト ストップリストの所有者を指定します。 自分自身 (現在のユーザー) に所有権を割り当てる場合は、このフィールドを空のままにします。  
  
 別のユーザーを指定するには、参照ボタンをクリックします。  
  
### <a name="create-stoplist-options"></a>ストップリスト作成オプション  
 以下のいずれかの作成オプションをクリックします。  
  
 **[空のストップリストを作成する]**  
 新しいストップリストにストップワードは含まれません。  
  
 **[システム ストップリストから作成する]**  
 [リソース データベース](../relational-databases/databases/resource-database.md)に既定で存在するストップリストから新しいストップリストを作成します。  
  
 **[既存のフルテキスト ストップリストから作成する]**  
 既存のストップリストをコピーして新しいストップリストを作成します。  
  
 **ソース データベース**  
 既存のストップリストが属しているデータベースの名前を指定します。 既定では、現在のデータベースが選択されています。 必要に応じて、リスト ボックスから別のデータベースを選択します。  
  
 **ソース ストップ リスト**  
 既存のストップリストの名前を指定します。 利用可能なストップリストの一覧から、基になるストップリストを選択します。 利用可能なストップリストは、オブジェクト エクスプローラーに表示される順序で一覧表示されます。  
  
 ソース ストップリストのストップワードに指定された言語が現在のデータベースに登録されていない場合、CREATE FULLTEXT STOPLIST は成功しますが、警告が表示され、対応するストップワードは追加されません。  
  
## <a name="see-also"></a>参照  
 [ALTER FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [CREATE FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [DROP FULLTEXT STOPLIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  

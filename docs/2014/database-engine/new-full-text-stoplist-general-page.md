---
title: 新しいフルテキストストップリスト ([全般] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.fulltextsearch.ftstoplist.general.f1
ms.assetid: 97f8e82d-82ab-4525-91c9-1ee3ae217309
author: rothja
ms.author: jroth
ms.openlocfilehash: a6272fb570b85989f38c8187e29712966862710d
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84930468"
---
# <a name="new-full-text-stoplist-general-page"></a>[新しいフルテキスト ストップリスト] ([全般] ページ)
  このダイアログ ボックスを使用すると、フルテキスト ストップリストを作成できます。 *ストップリスト* とは、一般的に使用される単語のセットのことです。これらの単語は *ストップワード*と呼ばれ、ストップリストを使用するテーブルのフルテキスト インデックスから省略されます。 詳細については、「 [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)」を参照してください。  
  
 **SQL Server Management Studio を使用してストップリストを作成するには**  
  
-   [フルテキスト検索に使用するストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)  
  
## <a name="options"></a>オプション  
 **[フルテキスト ストップリスト名]**  
 フルテキスト ストップリストの名前を入力します。  
  
 **所有者**  
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
  
 **ソースデータベース**  
 既存のストップリストが属しているデータベースの名前を指定します。 既定では、現在のデータベースが選択されています。 必要に応じて、リスト ボックスから別のデータベースを選択します。  
  
 **[基になるストップリスト]**  
 既存のストップリストの名前を指定します。 利用可能なストップリストの一覧から、基になるストップリストを選択します。 利用可能なストップリストは、オブジェクト エクスプローラーに表示される順序で一覧表示されます。  
  
 ソース ストップリストのストップワードに指定された言語が現在のデータベースに登録されていない場合、CREATE FULLTEXT STOPLIST は成功しますが、警告が表示され、対応するストップワードは追加されません。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;フルテキストストップリストの変更](/sql/t-sql/statements/alter-fulltext-stoplist-transact-sql)   
 [Transact-sql&#41;&#40;のフルテキストストップリストの作成](/sql/t-sql/statements/create-fulltext-stoplist-transact-sql)   
 [Transact-sql&#41;&#40;のフルテキストストップリストの削除](/sql/t-sql/statements/drop-fulltext-stoplist-transact-sql)   
 [フルテキスト検索のためのストップワードとストップリストの構成と管理](../relational-databases/search/full-text-search.md)   
 [sys.fulltext_stoplists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-fulltext-stoplists-transact-sql)  
  
  

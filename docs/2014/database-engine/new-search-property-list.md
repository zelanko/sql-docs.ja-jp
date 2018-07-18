---
title: 新しい検索プロパティ リスト |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: search
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
caps.latest.revision: 21
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 3019133dd0fa326a1595f2815698e10eb9586427
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37159307"
---
# <a name="new-search-property-list"></a>新しい検索プロパティ リスト
  このダイアログ ボックスを使用すると、検索プロパティ リストを作成できます。  
  
## <a name="options"></a>および  
 **検索プロパティ リスト名**  
 検索プロパティ リストの名前を入力します。  
  
 **[所有者]**  
 検索プロパティ リストの所有者を指定します。 自分自身 (現在のユーザー) に所有権を割り当てる場合は、このフィールドを空のままにします。 別のユーザーを指定するには、参照ボタンをクリックします。  
  
### <a name="create-search-property-list-options"></a>検索プロパティ リストの作成オプション  
 以下のいずれかのオプションをクリックします。  
  
 **[空の検索プロパティ リストを作成する]**  
 プロパティが指定されていない検索プロパティ リストを作成します。  
  
 **[既存の検索プロパティ リストから作成する]**  
 既存の検索のプロパティ リストのプロパティを新しいプロパティ リストにコピーします。 検索プロパティ リストはデータベース オブジェクトであるため、コピーするプロパティ リストを含むデータベースを指定する必要があります。  
  
 **ソース データベース**  
 既存の検索プロパティ リストが属しているデータベースの名前を指定します。 既定では、現在のデータベースが選択されています。 現在の接続がそのデータベース内のユーザー ID に関連付けられている場合、必要に応じて、リスト ボックスを使用して別のデータベースを選択することができます。  
  
 **ソース検索プロパティ リスト**  
 選択したデータベースに属している既存の検索プロパティ リストの名前を選択します。  
  
## <a name="permissions"></a>アクセス許可  
 参照してください[CREATE SEARCH PROPERTY LIST &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)します。  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>SQL Server Management Studio を使用した検索プロパティ リストの管理  
 プロパティ検索用のフルテキスト インデックスを構成する方法の詳細と作成、表示、変更、または、検索プロパティ リストを削除する方法については、次を参照してください。[検索プロパティ リストを使用したドキュメント プロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)します。  
  
## <a name="see-also"></a>参照  
 [CREATE SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  

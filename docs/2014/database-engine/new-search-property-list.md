---
title: 新しい検索プロパティリスト |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
f1_keywords:
- sql12.swb.spl.newsearchpropertylist.f1
ms.assetid: ffca78e9-8608-4b15-bd38-b2d78da4247a
author: craigg-msft
ms.author: craigg
manager: craigg
ms.openlocfilehash: 2aff15a42c8bffeb5a54e92b9ce7a09ace282ce4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "62774504"
---
# <a name="new-search-property-list"></a>新しい検索プロパティ リスト
  このダイアログ ボックスを使用すると、検索プロパティ リストを作成できます。  
  
## <a name="options"></a>オプション  
 **[検索プロパティ リスト名]**  
 検索プロパティ リストの名前を入力します。  
  
 **[所有者]**  
 検索プロパティ リストの所有者を指定します。 自分自身 (現在のユーザー) に所有権を割り当てる場合は、このフィールドを空のままにします。 別のユーザーを指定するには、参照ボタンをクリックします。  
  
### <a name="create-search-property-list-options"></a>検索プロパティ リストの作成オプション  
 以下のいずれかのオプションをクリックします。  
  
 **空の検索プロパティリストを作成する**  
 プロパティが指定されていない検索プロパティ リストを作成します。  
  
 **既存の検索プロパティリストから作成する**  
 既存の検索のプロパティ リストのプロパティを新しいプロパティ リストにコピーします。 検索プロパティ リストはデータベース オブジェクトであるため、コピーするプロパティ リストを含むデータベースを指定する必要があります。  
  
 **ソースデータベース**  
 既存の検索プロパティ リストが属しているデータベースの名前を指定します。 既定では、現在のデータベースが選択されています。 現在の接続がそのデータベース内のユーザー ID に関連付けられている場合、必要に応じて、リスト ボックスを使用して別のデータベースを選択することができます。  
  
 **[基になる検索プロパティ リスト]**  
 選択したデータベースに属している既存の検索プロパティ リストの名前を選択します。  
  
## <a name="permissions"></a>アクセス許可  
 「 [CREATE SEARCH PROPERTY LIST &#40;transact-sql&#41;](/sql/t-sql/statements/create-search-property-list-transact-sql)」を参照してください。  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>SQL Server Management Studio を使用した検索プロパティ リストの管理  
 検索プロパティ リストを作成、表示、変更、または削除する方法、およびプロパティ検索用にフルテキスト インデックスを構成する方法については、「 [Search Document Properties with Search Property Lists](../relational-databases/search/search-document-properties-with-search-property-lists.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [Transact-sql&#41;&#40;の検索プロパティリストの作成](/sql/t-sql/statements/create-search-property-list-transact-sql)   
 [検索プロパティリストを使用したドキュメントプロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [registered_search_property_lists &#40;Transact-sql&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  

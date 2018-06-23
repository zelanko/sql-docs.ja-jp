---
title: 検索プロパティ リスト エディター |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-search
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.swb.spl.searchpropertylisteditor.f1
ms.assetid: 0f3ced6e-0dfd-49fc-b175-82378c3d668e
caps.latest.revision: 26
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: e34bcf522675e13e9b1fa987f0f3bfc6aba36efb
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36164350"
---
# <a name="search-property-list-editor"></a>検索プロパティ リスト エディター
  このダイアログ ボックスを使用すると、検索プロパティ リストの検索プロパティを追加または削除できます。  
  
## <a name="to-use-sql-server-management-studio-to-manage-search-property-lists"></a>SQL Server Management Studio を使用した検索プロパティ リストの管理  
 作成、表示、または検索プロパティ リストを削除する方法について、およびプロパティ検索用のフルテキスト インデックスを構成する方法の詳細については、次を参照してください。[検索プロパティ リストとドキュメント プロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)です。  
  
## <a name="options"></a>および  
 **プロパティ名**  
 フルテキスト クエリのプロパティを識別するために使用される名前を指定します。 プロパティ名の内部にはスペースを含めることができます。 **プロパティ名** の長さは最大 256 文字です。 この名前は "作成者" や "ホーム アドレス" などのわかりやすい名前、または、Windows の正規のプロパティ名 (`System.Author` または `System.Contact.HomeAddress` など) にすることができます。 **プロパティ名** は、プロパティ セット内でプロパティを一意に識別する名前である必要があります。  
  
 開発者がプロパティ名を使用して、プロパティを識別、 [CONTAINS](/sql/t-sql/queries/contains-transact-sql)述語。 したがって、プロパティを追加する場合は、そのプロパティの意味を明確に表す名前を指定することが重要です。  
  
 **プロパティ セット GUID**  
 プロパティが属するプロパティ セットの識別子を指定します。 これはグローバル一意識別子 (GUID) です。 プロパティ セットは論理的に関連するプロパティのグループです。 この値の取得に関する情報については、このトピックの「解説」を参照してください。  
  
 **プロパティ整数 ID**  
 プロパティのプロパティ整数識別子を指定します。 このあらかじめ割り当てられた値は、プロパティ セット内で一意の正の整数です。 この値の取得に関する情報については、このトピックの「解説」を参照してください。  
  
> [!NOTE]  
>  文字列識別子を使用するドキュメント プロパティはフルテキスト検索でサポートされていません。  
  
 **プロパティの説明**  
 必要に応じてプロパティの説明を指定します。 これは最大 512 文字までの文字列です。 説明には、たとえばプロパティのプロパティ セットに関する情報、または名前からはその内容がわかりにくいプロパティに関する情報などが含まれる場合があります。  
  
## <a name="remarks"></a>コメント  
 検索プロパティ リストに検索プロパティを追加するには、プロパティが属するプロパティ セットのグローバル一意識別子 (GUID) とプロパティのプロパティ整数識別子を指定する必要があります。 これらの識別子の組み合わせが、検索プロパティ リスト内で一意である必要があります。 既存の組み合わせを追加しようとすると、操作が失敗しエラーが発生します。 つまり、1 つの名前は 1 つのプロパティに対してのみ構成できます。  
  
 このプロパティの説明は省略できます。  
  
 **フルテキスト インデックスの検索プロパティ リストを構成するには**  
  
-   [検索プロパティ リストを使用したドキュメント プロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)  
  
## <a name="permissions"></a>アクセス許可  
 参照してください[ALTER SEARCH PROPERTY LIST &#40;TRANSACT-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)です。  
  
## <a name="see-also"></a>参照  
 [ALTER SEARCH PROPERTY LIST &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-search-property-list-transact-sql)   
 [検索プロパティ リストを使用したドキュメント プロパティの検索](../relational-databases/search/search-document-properties-with-search-property-lists.md)   
 [sys.registered_search_property_lists &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/sys-registered-search-property-lists-transact-sql)  
  
  

---
title: フルテキスト インデックスのプロパティ ([列] ページ) |Microsoft ドキュメント
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
- sql12.swb.fulltextsearch.fulltextindexproperties.columns.f1
ms.assetid: 75e52edb-0d07-4393-9345-8b5af4561e35
caps.latest.revision: 17
author: craigg-msft
ms.author: craigg
manager: jhubbard
ms.openlocfilehash: 223a3e0db58b73f2b841cebd23d41bc36ba4a85b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074041"
---
# <a name="full-text-index-properties-columns-page"></a>[フルテキスト インデックスのプロパティ] ([列] ページ)
  **フルテキスト インデックスのプロパティを表示または変更**  
  
-   [フルテキスト インデックスの管理](../relational-databases/indexes/indexes.md)  
  
## <a name="uielement-list"></a>UI 要素の一覧  
 **一意のインデックス**  
 ドロップダウン リストからインデックスを選択します。 インデックスは、単一キー列の、一意で NULL 値が許容されないインデックスである必要があります。  
  
 **フルテキスト インデックスとなる条件を満たす列を選択します。**  
 このフルテキスト インデックスを作成できるテーブル列がグリッドに表示されます。 現在フルテキスト インデックスが作成されている列のチェック ボックスがオンになります。 必要に応じて、フルテキスト インデックスを作成する追加の列のチェック ボックスをオンにすることができます。  
  
> [!IMPORTANT]  
>  [OK] をクリックする前に、少なくとも 1 つの列のチェック ボックスがオンになっていることを確認してください。  
  
|||  
|-|-|  
|**使用可能な列**|列名。|  
|**ワード ブレーカーの言語**|すべてのフルテキスト インデックス データに対する言語分析を実行するワード ブレーカーおよびステミング機能を含む言語。<br /><br /> 詳細については、次を参照してください。[構成と管理ワード ブレーカーとステマーの検索](../relational-databases/search/configure-and-manage-word-breakers-and-stemmers-for-search.md)と[、フルテキスト インデックスを作成時の言語を選択](../relational-databases/search/choose-a-language-when-creating-a-full-text-index.md)です。|  
|**Type**|選択された列のドキュメント型を保持するテーブル列の名前。 これは、読み取り専用プロパティです。|  
|**[統計的セマンティクス]**|選択されている列に対するセマンティック インデックスを有効にするかどうかを選択します。 詳細については、「[セマンティック検索 &#40;SQL Server&#41;](../relational-databases/search/semantic-search-sql-server.md)」を参照してください。<br /><br /> **[統計的セマンティクス]** を選択する前に **[言語]** を選択した場合、選択した言語にセマンティック言語モデルが関連付けられていなければ、**[統計的セマンティクス]** チェック ボックスは無効になります。 **[言語]** を選択する前に **[統計的セマンティクス]** を選択した場合、ドロップダウン コンボ ボックスで使用できる言語は、セマンティック言語モデルでサポートされているものだけに制限されます。|  
  
## <a name="see-also"></a>参照  
 [フルテキスト インデックスの作成](../relational-databases/search/populate-full-text-indexes.md)  
  
  
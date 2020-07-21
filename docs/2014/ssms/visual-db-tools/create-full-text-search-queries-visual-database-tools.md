---
title: フルテキスト検索クエリの作成 (Visual Database Tools) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: stevestein
ms.author: sstein
ms.openlocfilehash: f84ab465da0a1b7ac1da1211de1d5199fd28ee95
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/18/2020
ms.locfileid: "85058175"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>フルテキスト検索クエリの作成 (Visual Database Tools)
  フルテキスト検索は、CONTAINS 述語を使用して、特定の列内に指定したテキストを持つ行を探します。 フルテキスト検索は、アクティブなフルテキスト インデックスが設定されている列でのみ実行できます。 現在アクティブなフルテキスト インデックスが設定されていない列に対して CONTAINS 句を使用すると、エラーが返されます。 フルテキストインデックスと CONTAINS 句の詳細については、「[フルテキスト検索](../../relational-databases/search/full-text-search.md)」と「 [Transact-sql&#41;を含む &#40;](/sql/t-sql/queries/contains-transact-sql)」を参照してください。  
  
### <a name="to-create-a-full-text-search-query"></a>フルテキスト検索クエリを作成するには  
  
1.  ソリューション エクスプローラーでクエリを開くか、新しいクエリを作成します。  
  
2.  クエリの WHERE 句で、CONTAINS 関数を使用してフルテキスト列を検索します。  
  
## <a name="see-also"></a>参照  
 [Visual Database Tools &#40;サポートされているクエリの種類&#41;](visual-database-tools.md)   
 [クエリおよびビューのデザイン方法に関するトピック &#40;Visual Database Tools&#41;](design-queries-and-views-how-to-topics-visual-database-tools.md)   
 [クエリに関する基本操作の実行 (Visual Database Tools)](perform-basic-operations-with-queries-visual-database-tools.md)  
  
  

---
title: フルテキスト検索クエリの作成
ms.custom: seo-lt-2019
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: sql-tools
ms.technology: ssms
ms.topic: conceptual
helpviewer_keywords:
- CONTAINS predicate (Transact-SQL)
- queries [full-text search], creating
- full-text queries [SQL Server], creating
ms.assetid: 537fa556-390e-4c88-9b8e-679848d94abc
author: markingmyname
ms.author: maghan
ms.manager: jroth
ms.reviewer: ''
ms.openlocfilehash: eb7029f81e784df63a283a4ef12766d5deb97d37
ms.sourcegitcommit: b78f7ab9281f570b87f96991ebd9a095812cc546
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/31/2020
ms.locfileid: "75254346"
---
# <a name="create-full-text-search-queries-visual-database-tools"></a>フルテキスト検索クエリの作成 (Visual Database Tools)
[!INCLUDE[appliesto-ss-asdb-asdw-pdw-md](../../includes/appliesto-ss-asdb-asdw-pdw-md.md)]
フルテキスト検索は、CONTAINS 述語を使用して、特定の列内に指定したテキストを持つ行を探します。 フルテキスト検索は、アクティブなフルテキスト インデックスが設定されている列でのみ実行できます。 現在アクティブなフルテキスト インデックスが設定されていない列に対して CONTAINS 句を使用すると、エラーが返されます。 フルテキスト インデックスと CONTAINS 句に関する詳細については、「 [フルテキスト検索](../../relational-databases/search/full-text-search.md) 」と「 [CONTAINS (Transact-SQL)](https://msdn.microsoft.com/996c72fc-b1ab-4c96-bd12-946be9c18f84)」を参照してください。  
  
### <a name="to-create-a-full-text-search-query"></a>フルテキスト検索クエリを作成するには  
  
1.  ソリューション エクスプローラーでクエリを開くか、新しいクエリを作成します。  
  
2.  クエリの WHERE 句で、CONTAINS 関数を使用してフルテキスト列を検索します。  
  
## <a name="see-also"></a>参照  
[サポートされるクエリの種類 (Visual Database Tools)](../../ssms/visual-db-tools/supported-query-types-visual-database-tools.md)  
[クエリおよびビューのデザインの操作方法に関するトピック (Visual Database Tools)](../../ssms/visual-db-tools/design-queries-and-views-how-to-topics-visual-database-tools.md)  
[クエリに関する基本操作の実行 (Visual Database Tools)](../../ssms/visual-db-tools/perform-basic-operations-with-queries-visual-database-tools.md)  
  

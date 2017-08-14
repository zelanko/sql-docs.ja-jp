---
title: "[OData ソース エディター]\\ ([接続] ページ) |Microsoft ドキュメント"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.odatasource.connection.f1
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
caps.latest.revision: 8
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6bb7a97ddbcae4868ee7b737358d4b30608e4df2
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odata-source-editor-connection-page"></a>[OData ソース エディター]\ ([接続] ページ)
  **[ODBC ソース エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、OData ソースに対応する ODBC 接続マネージャーを選択できます。 また、このページで、コレクションまたはリソースのパスと、どのデータを OData ソースから取得する必要があるかを示すクエリ オプションを指定することができます。 OData ソースの詳細については、「 [OData ソース](../../integration-services/data-flow/odata-source.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **OData 接続マネージャー**  
 既存の接続マネージャーを一覧から選択するか、 **[新規作成]**をクリックして新しい接続を作成します。  
  
 接続マネージャーを選択または作成すると、接続マネージャーで使用されている OData プロトコルのバージョンがダイアログ ボックスに表示されます。  
  
 **[新規作成]**  
 新しい接続マネージャーを作成するには、 **[OData 接続マネージャー エディター]** ダイアログ ボックスを使用します。  
  
 **コレクションまたはリソースのパスを使用します。**  
 ソースからデータを選択する方法を指定します。  
  
|オプション|Description|  
|------------|-----------------|  
|Collection|コレクション名を使用して、Odata ソースからデータを取得します。|  
|リソースのパス|リソースのパスを使用して、Odata ソースからデータを取得します。|  
  
 **クエリ オプション**  
 クエリのオプションを指定します。  例: $top=5  
  
 **フィード URL**  
 このダイアログ ボックスで選択したオプションに基づいて、読み取り専用のフィード URL を表示します。  
  
 **プレビュー**  
 **[プレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 **プレビュー** では、最大で 20 行を表示できます。  
  
## <a name="dynamic-options"></a>動的オプション  
  
### <a name="use-collection-or-resource-path--collection"></a>コレクション、またはリソースのパス = Collection を使用します。  
 **Collection**  
 ドロップダウン リストからコレクションを選択します。  
  
### <a name="use-collection-or-resource-path--resource-path"></a>コレクションまたはリソースのパス = Resource Path を使用します。  
 **Resource path**  
 リソースのパスを入力します。 例: Employees  
  
## <a name="see-also"></a>参照  
 [OData ソース エディターと &#40; です。「列」 ページと &#41; です。](../../integration-services/data-flow/odata-source-editor-columns-page.md)   
 [OData ソース エディターと &#40; です。エラー出力 ページと &#41; です。](../../integration-services/data-flow/odata-source-editor-error-output-page.md)   
 [OData 接続マネージャー](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  

---
title: "[OData ソース エディター] ([接続] ページ) | Microsoft Docs"
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.odatasource.connection.f1"
ms.assetid: 20bcd347-4547-4fad-b182-9571030101df
caps.latest.revision: 8
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 8
---
# [OData ソース エディター] ([接続] ページ)
  **[ODBC ソース エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、OData ソースに対応する ODBC 接続マネージャーを選択できます。 また、このページで、コレクションまたはリソースのパスと、どのデータを OData ソースから取得する必要があるかを示すクエリ オプションを指定することができます。 OData ソースの詳細については、「[OData ソース](../../integration-services/data-flow/odata-source.md)」を参照してください。  
  
## 静的オプション  
 **OData 接続マネージャー**  
 既存の接続マネージャーを一覧から選択するか、**[新規作成]** をクリックして新しい接続を作成します。  
  
 接続マネージャーを選択または作成すると、接続マネージャーで使用されている OData プロトコルのバージョンがダイアログ ボックスに表示されます。  
  
 **新規**  
 新しい接続マネージャーを作成するには、**[OData 接続マネージャー エディター]** ダイアログ ボックスを使用します。  
  
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
 **[プレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 **プレビュー**では、最大で 20 行を表示できます。  
  
## 動的オプション  
  
### コレクション、またはリソースのパス = Collection を使用します。  
 **Collection**  
 ドロップダウン リストからコレクションを選択します。  
  
### コレクションまたはリソースのパス = Resource Path を使用します。  
 **リソースのパス**  
 リソースのパスを入力します。 例: Employees  
  
## 参照  
 [OData ソース エディター ([列] ページ)](../Topic/OData%20Source%20Editor%20\(Columns%20Page\).md)   
 [OData ソース エディター ([エラー出力] ページ)](../Topic/OData%20Source%20Editor%20\(Error%20Output%20Page\).md)   
 [OData 接続マネージャー](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  
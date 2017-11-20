---
title: "OData ソース |Microsoft ドキュメント"
ms.date: 03/01/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: data-flow
ms.reviewer: 
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.DTS.DESIGNER.ODATASOURCE.F1
- sql13.dts.designer.odatasource.connection.f1
- sql13.dts.designer.odatasource.columns.f1
- sql13.dts.designer.odatasource.erroroutput.f1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: ee79d0f1b31963b7d13aa07bf4603246139c3a7c
ms.openlocfilehash: 1e0ef2b7cca9509a58aeadca3903e8aec3b7b9b9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/23/2017

---
# <a name="odata-source"></a>OData ソース
Open Data Protocol (OData) サービスからのデータを使用するには、SSIS パッケージの OData ソース コンポーネントを使用します。 このコンポーネントは、OData v3 プロトコルと v4 プロトコルをサポートします。  
  
-   OData V3 プロトコルでは、コンポーネントは、ATOM と JSON データ形式をサポートします。  
  
-   OData V4 プロトコルでは、コンポーネントは、JSON データ形式をサポートします。  

OData ソースには、次のデータ ソースのサポートが含まれています。
-   Microsoft Dynamics AX オンラインや Microsoft Dynamics CRM Online
-   SharePoint が一覧表示します。 SharePoint サーバー上のすべての一覧を表示するには、次の URL を使用: http://\<サーバー >/_vti_bin/ListData.svc です。 SharePoint の URL の規則に関する詳細については、「 [SharePoint Foundation REST インターフェイス](http://msdn.microsoft.com/library/ff521587.aspx)」を参照してください。
  
## <a name="odata-format-and-performance"></a>OData 形式とパフォーマンス
 ほとんどの OData サービスは、複数の形式で結果を返すことができます。 使用して、結果セットの形式を指定することができます、`$format`クエリ オプション。 JSON と JSON Light のような形式は、ATOM または XML より効率的であり、大量のデータを転送する場合により高いパフォーマンスを達成できる可能性があります。 次の表に、サンプル テストの結果を示します。 ここから理解できるように、ATOM から JSON に切り替えるとパフォーマンスが 30 ～ 53% 向上し、Atom から新しい JSON Light 形式 (WCF Data Services 5.1 で使用可能) に切り替えるとパフォーマンスが 67% 向上します。  
  
|行数|ATOM|JSON|JSON (Light)|  
|-|-|-|-|  
|10000|113 秒|74 秒|68 秒|  
|1000000|1110 秒|853 秒|665 秒|  
  
## <a name="related-topics-in-this-section"></a>このセクション内の関連トピック  
  
-   [チュートリアル: OData ソースの使用](../../integration-services/data-flow/tutorial-using-the-odata-source.md)  
  
-   [実行時の OData ソース クエリの変更](../../integration-services/data-flow/modify-odata-source-query-at-runtime.md)  
  
-   [OData ソースのプロパティ](../../integration-services/data-flow/odata-source-properties.md)  
  
## <a name="odata-source-editor-connection-page"></a>[OData ソース エディター]\ ([接続] ページ)
  **[ODBC ソース エディター]** ダイアログ ボックスの **[接続]** ページを使用すると、OData ソースに対応する ODBC 接続マネージャーを選択できます。 また、このページで、コレクションまたはリソースのパスと、どのデータを OData ソースから取得する必要があるかを示すクエリ オプションを指定することができます。 
  
### <a name="static-options"></a>静的オプション  
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
 クエリのオプションを指定します。 例: `$top=5` 
  
 **フィード URL**  
 読み取り専用の表示フィードのこのダイアログ ボックスで選択したオプションに基づく URL。  
  
 **プレビュー**  
 **[プレビュー]** ダイアログ ボックスを使用して、結果をプレビューします。 **プレビュー** では、最大で 20 行を表示できます。  
  
### <a name="dynamic-options"></a>動的オプション  
  
#### <a name="use-collection-or-resource-path--collection"></a>コレクション、またはリソースのパス = Collection を使用します。  
 **Collection**  
 ドロップダウン リストからコレクションを選択します。  
  
#### <a name="use-collection-or-resource-path--resource-path"></a>コレクションまたはリソースのパス = Resource Path を使用します。  
 **Resource path**  
 リソースのパスを入力します。 例: Employees  
  
## <a name="odata-source-editor-columns-page"></a>[OData ソース エディター]\ ([列] ページ)
  出力に含める外部 (変換元) 列を選択し、それらを出力列にマップするには、 **[OData ソース エディター]** ダイアログ ボックスの **[列]** ページを使用します。  
  
### <a name="options"></a>オプション  
 **使用できる外部列**  
 データ ソース内にある使用可能なソース列の一覧を表示します。 ページの下部にあるテーブルに対して列を追加または削除するには、一覧にあるチェック ボックスを使用します。 選択した列は、出力に追加されます。  
  
 **外部列**  
 出力に含めるように選択したソース列を表示します。  
  
 **出力列**  
 各出力列の一意な名前を表示します。 既定では選択された外部 (変換元) 列の名前になりますが、一意でわかりやすい名前を付けることもできます。  
  
## <a name="odata-source-editor-error-output-page"></a>[OData ソース エディター]\ ([エラー出力] ページ)
  **[OData ソース エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを選択したり、エラー出力列のプロパティを設定したりできます。  
  
### <a name="options"></a>オプション  
 **入力/出力**  
 データ ソースの名前を表示します。  
  
 **列**  
 **[ODBC ソース エディター]** ダイアログ ボックスの **[接続マネージャー]** ページで選択されている外部 (変換元) 列を表示します。  
  
 **[エラー]**  
 エラーが発生した場合に、障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **関連項目:** [データのエラー処理](../../integration-services/data-flow/error-handling-in-data.md)  
  
 **切り捨て**  
 切り捨てが発生したときの処理方法 (エラーを無視する、行をリダイレクトする、またはコンポーネントを失敗させる) を指定します。  
  
 **Description**  
 エラーの説明を表示します。  
  
 **この値を選択したセルに設定します。**  
 エラーまたは切り捨てが発生した場合に、選択したすべてのセルに対して障害を無視するか、行をリダイレクトするか、コンポーネントを失敗させるかを指定します。  
  
 **適用**  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="see-also"></a>参照  
 [OData 接続マネージャー](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  


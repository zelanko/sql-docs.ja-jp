---
title: "OData ソース |Microsoft ドキュメント"
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.DTS.DESIGNER.ODATASOURCE.F1
ms.assetid: cc9003c9-638e-432b-867e-e949d50cec90
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: c52506dcfa582cc3e0992fe4fda772489d544247
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="odata-source"></a>OData ソース
  Open Data Protocol (OData) サービスからのデータを使用するには、SSIS パッケージの OData ソース コンポーネントを使用します。 このコンポーネントは、OData v3 プロトコルと v4 プロトコルをサポートします。  
  
-   OData V3 プロトコルでは、ATOM データ形式と JSON データ形式をサポートします。  
  
-   OData V4 プロトコルでは、JSON データ形式をサポートします。  
  
> [!NOTE]  
>  OData ソースを使用して、SharePoint リストから読み取りを行うこともできます。 SharePoint サーバー上のすべての一覧を表示するには、次の URL を使用: http://\<サーバー >/_vti_bin/ListData.svc です。 SharePoint の URL の規則に関する詳細については、「 [SharePoint Foundation REST インターフェイス](http://msdn.microsoft.com/library/ff521587.aspx)」を参照してください。  OData ソースでは、Microsoft Dynamics AX Online および Microsoft Dynamics CRM Online 製品がサポートされるようになりました。
  
## <a name="odata-format"></a>OData の形式  
 ほとんどの OData サービスは、結果を複数の形式で返します。 $format クエリ オプションを使用して、結果セットの形式を指定することができます。 JSON と JSON Light のような形式は、ATOM または XML より効率的であり、大量のデータを転送する場合により高いパフォーマンスを達成できる可能性があります。 次の表に、サンプル テストの結果を示します。 ここから理解できるように、ATOM から JSON に切り替えるとパフォーマンスが 30 ～ 53% 向上し、Atom から新しい JSON Light 形式 (WCF Data Services 5.1 で使用可能) に切り替えるとパフォーマンスが 67% 向上します。  
  
|||||  
|-|-|-|-|  
|行数|ATOM|JSON|JSON (Light)|  
|10000|113 秒|74 秒|68 秒|  
|1000000|1110 秒|853 秒|665 秒|  
  
> [!NOTE]  
>  SSIS OData ソースでは、5.6.1 を使用して OData V3 フィードを解析し、ODataLib 6.12.0 を使用して OData V4 フィードを解析します。  
  
## <a name="in-this-section"></a>このセクションの内容  
  
-   [チュートリアル: OData ソースの使用](../../integration-services/data-flow/tutorial-using-the-odata-source.md)  
  
-   [実行時の OData ソース クエリの変更](../../integration-services/data-flow/modify-odata-source-query-at-runtime.md)  
  
-   [[OData ソース エディター] &#40;[接続] ページ&#41;](../../integration-services/data-flow/odata-source-editor-connection-page.md)  
  
-   [[OData ソース エディター] &#40;[列] ページ&#41;](../../integration-services/data-flow/odata-source-editor-columns-page.md)  
  
-   [OData ソース エディター &#40;[エラー出力] ページ&#41;](../../integration-services/data-flow/odata-source-editor-error-output-page.md)  
  
-   [OData ソースのプロパティ](../../integration-services/data-flow/odata-source-properties.md)  
  
## <a name="see-also"></a>参照  
 [OData 接続マネージャー](../../integration-services/connection-manager/odata-connection-manager.md)  
  
  

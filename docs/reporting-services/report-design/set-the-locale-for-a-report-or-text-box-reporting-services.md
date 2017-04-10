---
title: "レポートまたはテキスト ボックスのロケールの設定 (Reporting Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ロケール [Reporting Services]"
ms.assetid: df115b01-184b-47f0-b5ec-0ad965ff9bee
caps.latest.revision: 43
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
caps.handback.revision: 43
---
# レポートまたはテキスト ボックスのロケールの設定 (Reporting Services)
  レポートまたはテキスト ボックスの **Language** プロパティでは、ローカル設定を指定します。ローカル設定は、言語や地域ごとに異なるレポート データ (日付、通貨、数値など) を表示するための既定の形式を指定します。 テキスト ボックスの **Language** プロパティは、レポートの **Language** プロパティに優先します。 **Language** プロパティに値が指定されてない場合、Reporting Services は、パブリッシュされたレポートのレポート サーバーの OS のロケールか、またはレポート プレビューを行うレポート作成コンピューターのロケールを使用します。  
  
 HTML レポートの場合、既定の **Language** 値を無視し、ブラウザー クライアントの HTTP ヘッダーで指定している言語を使用できます。この操作を行うには、レポートまたはテキスト ボックスの **Language** プロパティの式で組み込みフィールド User!Language を使用します。  
  
 レポートの **Language** プロパティを URL で指定することもできます。 詳細については、「[URL でレポート パラメーターの言語を設定する](../../reporting-services/set-the-language-for-report-parameters-in-a-url.md)」を参照してください。  
  
### レポートのロケールを設定するには  
  
1.  デザイン ビューで、レポートのデザイン画面の外側をクリックして、レポートを選択します。  
  
2.  プロパティ ペインの **[Language]** プロパティで、レポートに使用する言語を入力または選択します。  
  
### テキスト ボックスのロケールを設定するには  
  
1.  デザイン ビューで、ロケール設定を適用するテキスト ボックスを選択します。  
  
2.  プロパティ ペインで、次の操作を行います。  
  
    -   **[Calendar]** プロパティで、日付に使用するカレンダーを入力または選択します。  
  
    -   **[Direction]** プロパティで、テキストを記述する方向を入力または選択します。  
  
    -   **[Language]** プロパティで、テキスト ボックスに使用する言語を入力または選択します。 この値は、レポートの **[Language]** プロパティに優先します。  
  
    -   **[NumeralLanguage]** プロパティで、テキスト ボックスの数字に使用する形式を入力または選択します。  
  
    -   **[NumeralVariant]** プロパティで、テキスト ボックスの数字に使用する形式の変化形を入力または選択します。  
  
    -   **[UnicodeBiDi]** プロパティで、テキスト ボックスで使用する双方向の埋め込みレベルを選択します。  
  
## 参照  
 [レポートでの式の使用 &#40;レポート ビルダーおよび SSRS&#41;](../../reporting-services/report-design/expression-uses-in-reports-report-builder-and-ssrs.md)   
 [多言語配置やグローバル配置のソリューション設計に関する考慮事項 (Reporting Services)](http://msdn.microsoft.com/ja-jp/55630eca-d1e5-4ac6-93c7-9a3f15c0d08a)  
  
  
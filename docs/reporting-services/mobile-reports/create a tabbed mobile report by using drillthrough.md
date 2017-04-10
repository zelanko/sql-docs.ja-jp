---
title: "ドリルスルーを使用してタブ付きモバイル レポートを作成する | Reporting Services のモバイル レポート | Microsoft Docs"
ms.custom: ""
ms.date: "12/09/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: "maggiesMSFT"
ms.author: "maggies"
manager: "erikre"
---
# ドリルスルーを使用してタブ付きモバイル レポートを作成する | Reporting Services のモバイル レポート
ドリルスルーとパラメーターを使用して、タブ付きレポートのような外観と動作の [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] モバイル レポートを作成する方法について説明します。

たとえば、このレポートでは、上部にあるゲージはタブのように動作します。 輸送ゲージをクリックすると、他のグラフのデータがフィルターされ、輸送データのみが表示されます。

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

実際には、これは 5 つの独立したレポートのセットであり、それぞれがレポート上部で選択されたゲージと一致するようにレポートをフィルター処理する異なるパラメーターを備えています。 

この例では、最初に 5 つのレポートをすべて作成した後、それぞれについて、他の 4 つのゲージで他の 4 つのレポートにドリルスルーできるようにします。 

手順の概要は次のとおりです。

1. 次の5 つのゲージを持つ売上という名前のレポートを作成します。
     - 売上
     - 輸送
     - 燃料
     - ストレージ
     - その他諸経費
2. 以下の名前でレポートのコピーを 4 つ作成します。 
     - 輸送
     - 燃料
     - ストレージ
     - その他諸経費
3.  売上レポートで、4 つの各ゲージ (売上ゲージ以外) をそれぞれのレポートへのドリルスルーとして設定します。

4. 売上レポートで、他のレポートより売上レポートが目立つように売上レポートの [アクセント] プロパティを設定します。

5.  次に、輸送レポートで、売上ゲージを売上レポートへのドリルスルーとして、また他の 3 つのゲージをそれぞれのレポートへのドリルスルーとして設定します。

6. 輸送レポートで、他のレポートから目立つように輸送レポートの [アクセント] プロパティを設定します。

5. 燃料、ストレージ、その他諸経費の各レポートについてこれを繰り返します。 







  

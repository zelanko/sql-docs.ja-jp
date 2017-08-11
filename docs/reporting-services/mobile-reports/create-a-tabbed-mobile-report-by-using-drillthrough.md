---
title: "ドリルスルーを使用して、タブ付きのモバイル レポートを作成 |Reporting Services モバイル レポート |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c4d5d80d-370a-4a6d-8b76-698bd5ba5ba6
caps.latest.revision: 9
author: maggiesMSFT
ms.author: maggies
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 6554f808c19540d2a3b7cbe3fdf4e86c5fe7a357
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="create-a-tabbed-mobile-report-by-using-drillthrough"></a>ドリルスルーを使用して、タブ付きのモバイル レポートを作成します。
ドリルスルーとパラメーターを使用して、タブ付きレポートのような外観と動作の [!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)] モバイル レポートを作成する方法について説明します。

たとえば、このレポートでは、上部にあるゲージはタブのように動作します。 輸送ゲージをクリックすると、他のグラフのデータがフィルターされ、輸送データのみが表示されます。

![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/tabbed-mobile-report-web-viewer-transportation-complete.png)

実際には、これは 5 つの独立したレポートのセットであり、それぞれがレポート上部で選択されたゲージと一致するようにレポートをフィルター処理する異なるパラメーターを備えています。 最初に、5 つのすべてのレポートを作成し、5 つのレポートのそれぞれについて、その他の 4 つのゲージ drillthroughs に加えたその他の 4 つのレポートします。

この例の手順を以下に示します。

## <a name="create-the-basic-report"></a>基本的なレポートを作成します。

1. 次の5 つのゲージを持つ売上という名前のレポートを作成します。

    * 売上
    * 輸送
    * 燃料
    * ストレージ
    * その他諸経費

   ![01-sales-モバイルのレポート-パブリッシャー](../../reporting-services/mobile-reports/media/01-sales-mobile-report-publisher.png)
    
2. 設定**アクセント**に**で**Sales ゲージのためには」と比較して、--このケースでは、レポートの白に黒の rest。

    ![01a-Sales-Accent-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/01a-sales-accent-mobile-report-publisher.png)
    
3. 保存して、[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]レポート サーバー。

## <a name="make-copies-of-the-report"></a>レポートのコピーを作成します。

1. 売上レポートの 4 つのコピーを作成し、名前を付けます。 

    * 輸送
    * 燃料
    * ストレージ
    * その他諸経費

3. 保存する、[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]レポート サーバー。

## <a name="set-the-gauge-as-a-drillthrough"></a>ドリル スルー、ゲージに設定します。

ここでは、各ゲージには (Sales ゲージ) 以外を設定するとして、個々 のレポートにドリルスルーします。

1. 売上レポートでは、輸送ゲージを選択します。

    ![02-Sales-Create-DrillThrough-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/02-sales-create-drillthrough-mobile-report-publisher.png)

2. **レイアウト** タブをオンにした場合、 **Visual プロパティ**ペインを選択**ドリルスルー ターゲット**です。

3. 選択**モバイル レポート**です。

4. 移動し、この場合、ドリルスルー--destination なりますレポートを選択して"Financials - 運輸"。

    ![03-Sales-Select-Dashboard-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/03-sales-select-dashboard-mobile-report-publisher.png)

5. **ターゲット レポートを構成する**、パラメーターを選択して、レポートをフィルター処理して選択**適用**です。

   ![04-Sales-Apply-Parameters-Mobile-Report-Publisher](../../reporting-services/mobile-reports/media/04-sales-apply-parameters-mobile-report-publisher.png)
   
6. 売上レポートにその他のゲージのそれぞれについて次の手順を繰り返します。 

## <a name="set-the-gauges-for-the-other-reports"></a>その他のレポートのゲージを設定します。

1.  輸送レポートを開き、売上レポート、およびその他の 3 つへのドリルスルーは、それぞれのレポートに drillthroughs としてゲージに Sales ゲージを設定します。

2. まだ輸送レポートで、次のように設定します。**アクセント**を輸送ゲージの**で**、と比較して、レポートの残りの部分です。

3. 燃料、ストレージ、および他の諸経費レポートの次の手順を繰り返します。 

## <a name="view-the-report-in-the-web-portal"></a>Web ポータルでレポートを表示します。

1. 移動して、[!INCLUDE[ssRSnoversion_md](../../includes/ssrsnoversion-md.md)]レポート サーバーとレポートのいずれかを開きます。 

2. 右上隅で、ドリルスルー アイコンがあります、ゲージの各ことに注意してください。

    ![Web-Viewer-drillthrough-icon-mobile-report-builder](../../reporting-services/mobile-reports/media/web-viewer-drillthrough-icon-mobile-report-builder.png)

3. そのゲージのデータをフィルター処理してレポートに移動するゲージのいずれかを選択します。

   ![06-Mobile-Report-Web-Viewer-Transportation](../../reporting-services/mobile-reports/media/06-mobile-report-web-viewer-transportation.png)

### <a name="see-also"></a>参照
    
* [モバイル レポートにパラメーターを追加する](../../reporting-services/mobile-reports/add-parameters-to-a-mobile-report-reporting-services.md)
* [モバイル レポートから他のモバイル レポートまたは URL にドリルスルーを追加する](../../reporting-services/mobile-reports/add-drillthrough-from-a-mobile-report-to-other-mobile-reports-or-urls.md)




  



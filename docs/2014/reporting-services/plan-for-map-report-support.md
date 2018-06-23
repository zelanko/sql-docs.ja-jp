---
title: マップ レポートのサポートの計画 |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5ddc97a7-7ee5-475d-bc49-3b814dce7e19
caps.latest.revision: 10
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: cf56a62b3ef129d9d725aa54d05544f776d4f6ac
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072282"
---
# <a name="plan-for-map-report-support"></a>マップ レポートのサポートを計画する
  [!INCLUDE[ssRSCurrent](../includes/ssrscurrent-md.md)] 空間データ ソースを使用するマップ レポートをサポートしています。 空間データは、SQL Server データベース、ESRI シェープファイル、または Reporting Services かレポート ビルダーを使用してインストールされたマップ ギャラリーから取得できます。 また、マップには Bing のマップ タイルの背景も表示できます。 レポートの作成者は、動的と実行時に取得した、または静的と、レポート定義に埋め込まれているとして空間データまたは Bing のマップ タイルを指定するレポートを作成できます。  
  
## <a name="support-for-bing-maps"></a>Bing Maps のサポート  
 マップには、Bing のマップ タイルを表示する背景レイヤーを含めることができます。 マップ タイル レイヤーを含むパブリッシュ済みレポートを表示するには、Bing Maps Web サービスからタイルを取得するようにレポート サーバーを構成する必要があります。 詳しくは、「 [RSReportServer Configuration File](report-server/rsreportserver-config-configuration-file.md)」をご覧ください。  
  
 各レポートについて、レポート作成者は、タイル サーバーからタイルを取得する際に SSL (Secure Sockets Layer) 接続を使用するかどうかを指定できます。 タイル レイヤーのプロパティ ウィンドウで、これには、ブール型プロパティ UseSecureConnection を設定する必要がありますに`true`です。  
  
> [!NOTE]  
>  レポート内での Bing のマップ タイルの使用については、「 [追加使用条件](http://go.microsoft.com/fwlink/?LinkId=151371) 」および「 [プライバシーに関する声明](http://go.microsoft.com/fwlink/?LinkId=151372)」を参照してください。  
  
## <a name="report-design-recommendations"></a>レポートのデザインに関する推奨事項  
 マップ レポートを適切にデザインするには、静的な空間データと動的な空間データのトレードオフを評価し、レポートのユーザーにとって最適なバランスを見極める必要があります。 マップ要素を埋め込んだ場合、レポート定義のサイズが著しく増加しますが、レポート内でマップを表示するために要する時間が短縮されます。 動的なマップ要素の場合、レポート定義のサイズが小さくなりますが、マップを処理して表示するために要する時間が増加します。 レポートの作成者は、この相反する要因の間で適切にバランスをとる必要があります。  
  
 レポート定義のサイズが問題となる場合、レポート サーバーの管理者は、レポートの設計者にレポート定義の空間データの量を削減するように促してもよいでしょう。  
  
 次のような場合には、マップ要素がレポート定義に埋め込まれます。  
  
-   レポートの作成時に、空間データ ソースがローカルのファイル システムに置かれている。 これには、ローカルにインストールされた ESRI シェープファイルまたはマップ ギャラリーからの空間データも含まれます。 既定で、マップ ウィザードおよびマップ レイヤー ウィザードでは、ローカル ファイル システム上のデータ ソースに由来する空間データが埋め込まれます。  
  
-   レポートの作成者が、レポートに空間データを手動で埋め込むオプションを選択した。  
  
 マップを含むレポート定義のサイズを削減するには、次の選択肢を 1 つ以上実行します。  
  
-   レポート デザイナーから[!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]、ESRI シェープファイルをレポート サーバー プロジェクトには空間データ ソースを追加します。 プロジェクトの配置時に、レポートに加えて ESRI シェープファイルがレポート サーバーにパブリッシュされます。 マップ ウィザードを実行する際に、レポート サーバー プロジェクトの空間データ ソースを指定すると、既定でマップ要素はレポート定義に埋め込まれません。  
  
-   レポート ビルダーからレポート サーバーからシェープファイルを選択して ESRI シェープファイルである空間データ ソースを追加します。 マップ ウィザードを実行する際に、レポート サーバーの空間データ ソースを参照して指定すると、既定でマップ要素はレポート定義に埋め込まれません。  
  
-   マップ データを埋め込みマップ データにする必要がある場合、ビューポートの中心位置とズーム レベルを調整して、レポートに必要なマップ データのみが含まれるようにする。  
  
 詳細については、[マップ&#40;レポート ビルダーおよび SSRS&#41;](report-design/maps-report-builder-and-ssrs.md)です。  
  
## <a name="see-also"></a>参照  
 [レポートのトラブルシューティング: レポートにマップ&#40;レポート ビルダーおよび SSRS&#41;](report-design/troubleshoot-reports-map-reports-report-builder-and-ssrs.md)  
  
  
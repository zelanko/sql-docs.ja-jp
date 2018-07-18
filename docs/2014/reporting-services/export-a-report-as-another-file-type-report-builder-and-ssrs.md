---
title: 別のファイルの種類 (レポート ビルダーおよび SSRS) としてエクスポートする |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: b577568b-ecbd-44c3-be88-31dab6fc38a2
caps.latest.revision: 9
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 88d0969efabebe3da05ebfce8d666eb78ff4ba2d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37166203"
---
# <a name="export-a-report-as-another-file-type-report-builder-and-ssrs"></a>別の種類のファイルとしてレポートをエクスポートする (レポート ビルダーおよび SSRS)
  レポートは、レポート ビルダーまたはレポート デザイナーでプレビュー中に、CSV、Image、PDF、[!INCLUDE[ofprword](../includes/ofprword-md.md)]、[!INCLUDE[ofprexcel](../includes/ofprexcel-md.md)] などの他のファイル形式に変換できます。また、レポート サーバーで閲覧中に変換することもできます。 レポートを特定の形式で表示することが便利であるのは、レポートをレポート サーバーにパブリッシュせずにすぐに別のファイルの種類で保存する場合や、レポートを特定の形式でユーザーに配信する際にレポートのデザインがどのように表示されるかを確認する場合です。 レポート サーバーでレポートを変換するのが便利なのは、サブスクリプションを設定したり電子メールでレポートを配信したりする場合や、レポート サーバーで利用可能なレポートを保存する場合です。 詳細については「[サブスクリプションと配信 &#40;Reporting Services&#41](subscriptions/subscriptions-and-delivery-reporting-services.md)」を参照してください。  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-export-a-report-as-another-file-type-in-report-builder"></a>レポート ビルダーでレポートを別の種類のファイルとしてエクスポートするには  
  
1.  レポートをプレビューします。  
  
2.  リボンの **[エクスポート]** をクリックします。  
  
3.  使用する形式を選択します。  
  
     **[名前を付けて保存]** ダイアログ ボックスが表示されます。 既定では、ファイル名はエクスポートしたレポートの名前になります。 必要に応じてファイル名を変更できます。  
  
4.  レポートを保存した場所へ移動して、レポートを開きます。  
  
> [!NOTE]  
>  ファイルの種類に関連付けられたプログラムがないことが原因で、レポートを選択した形式で開くことができない場合は、エクスポートされたファイルを保存するか、レポートを開くためのプログラムをオンライン上で探すことが求められます。  
  
### <a name="to-export-a-report-as-another-file-type-in-report-manager"></a>レポート マネージャーでレポートを別の種類のファイルとしてエクスポートするには  
  
1.  レポート マネージャーの **[ホーム]** ページから、エクスポートするレポートに移動します。  
  
2.  レポートをクリックします。  
  
     レポートが生成されます。  
  
3.  レポート ビューアー ツール バーで、 **[形式の選択]** ボックスの矢印をクリックします。  
  
4.  使用する形式を選択します。  
  
5.  **[エクスポート]** をクリックします。  
  
     ファイルを開くか保存するかを確認するメッセージが表示されます。  
  
6.  選択したエクスポート形式でレポートを表示するには、 **[開く]** をクリックします。  
  
     \- または -  
  
     選択したエクスポート形式でレポートをすぐに保存するには、 **[保存]** をクリックします。  
  
     選択した形式に関連付けられているアプリケーションを使用して、レポートが表示または保存されます。 **[保存]** をクリックした場合、レポートを保存する場所を指定するよう求められます。  
  
     **注** ファイルの種類に関連付けられたプログラムがないことが原因で、レポートを選択した形式で開くことができない場合は、エクスポートされたファイルを保存するか、レポートを開くためのプログラムをオンライン上で探すことが求められます。  
  
### <a name="to-export-a-report-as-another-file-type-in-a-sharepoint-library"></a>SharePoint ライブラリでレポートを別の種類のファイルとしてエクスポートするには  
  
1.  レポートをプレビューします。  
  
2.  ツール バーの **[アクション]** をクリックし、 **[エクスポート]** をポイントして、使用する形式を選択します。  
  
     **[ファイルのダウンロード]** ダイアログ ボックスが開きます。  
  
3.  選択したエクスポート形式でレポートを表示するには、 **[開く]** をクリックします。  
  
     \- または -  
  
     選択したエクスポート形式でレポートをすぐに保存するには、 **[保存]** をクリックします。  
  
     選択した形式に関連付けられているアプリケーションを使用して、レポートが表示または保存されます。 **[保存]** をクリックした場合、レポートを保存する場所を指定するよう求められます。  
  
     必要に応じて、エクスポートしたレポートのファイル名を変更します。  
  
     **注** ファイルの種類に関連付けられたプログラムがないことが原因で、レポートを選択した形式で開くことができない場合は、エクスポートされたファイルを保存するか、レポートを開くためのプログラムをオンライン上で探すことが求められます。  
  
## <a name="see-also"></a>参照  
 [レポートのエクスポート&#40;レポート ビルダーおよび SSRS&#41;](report-builder/export-reports-report-builder-and-ssrs.md)   
 [Reporting Services の改ページ &#40;レポート ビルダーおよび SSRS&#41;](report-design/pagination-in-reporting-services-report-builder-and-ssrs.md)   
 [さまざまなレポート表示拡張機能の対話機能&#40;レポート ビルダーおよび SSRS&#41;](report-builder/interactive-functionality-different-report-rendering-extensions.md)  
  
  

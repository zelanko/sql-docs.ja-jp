---
title: ReportViewer コントロール 2016 でのデータ収集
uthor: markingmyname
ms.author: maghan
manager: kfile
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native, reporting-services-sharepoint
ms.technology: application-integration
ms.topic: reference
ms.custom: ''
ms.date: 09/18/2018
ms.openlocfilehash: 52f23cd615179b774392920c84ab4370892e1dd5
ms.sourcegitcommit: 78e32562f9c1fbf2e50d3be645941d4aa457e31f
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2019
ms.locfileid: "54100197"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>ReportViewer コントロールを使用した Reporting Services の統合 - データ収集

顧客が製品をどのように使用しているかを理解するために、匿名の利用状況データがコントロールによって収集されます。 使用状況データを使用して、今後の開発で顧客に最も関係のある機能強化に注力できます。

Microsoft SQL Server と Report Viewer でのデータ収集と使用方法については、[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=868444)をご覧ください。

## <a name="opting-out-of-data-collection"></a>データ収集のオプトアウト

使用状況データの収集は、```EnableTelemetry``` プロパティを使用して無効にすることができます。

```
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

または、コントロールがレンダリングされる前にプログラムで無効にできます。
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>参照

[WebForms レポート ビューアー コントロールの使用](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[レポート ビューアー コントロールを使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 




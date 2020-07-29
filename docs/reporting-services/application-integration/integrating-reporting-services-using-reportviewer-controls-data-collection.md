---
title: ReportViewer コントロールでのデータ収集
description: ReportViewer では、匿名の使用状況データを収集して、顧客が製品をどのように使用しているかを把握し、顧客にとって最も関連性の高い機能強化に開発の重点を置くことができます。
author: maggiesMSFT
ms.author: maggies
ms.custom: seo-lt-2019
ms.reviewer: ''
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.topic: reference
ms.date: 06/03/2020
ms.openlocfilehash: 22f693824c244e02f313e488a067a0b732b2fa10
ms.sourcegitcommit: dc6ea6665cd2fb58a940c722e86299396b329fec
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2020
ms.locfileid: "84423400"
---
# <a name="integrate-reporting-services-using-reportviewer-controls---data-collection"></a>ReportViewer コントロールを使用した Reporting Services の統合 - データ収集

顧客が製品をどのように使用しているかを理解するために、匿名の利用状況データがコントロールによって収集されます。 使用状況データを使用して、今後の開発で顧客に最も関係のある機能強化に注力できます。

Microsoft SQL Server と Report Viewer でのデータ収集と使用方法については、[プライバシーに関する声明](https://go.microsoft.com/fwlink/?LinkID=868444)をご覧ください。

## <a name="opting-out-of-data-collection"></a>データ収集のオプトアウト

使用状況データの収集は、```EnableTelemetry``` プロパティを使用して無効にすることができます。

```xml
<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
</rsweb:ReportViewer>
```

または、コントロールがレンダリングされる前にプログラムで無効にできます。
    
```csharp
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>参照

[WebForms レポート ビューアー コントロールの使用](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[レポート ビューアー コントロールを使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 




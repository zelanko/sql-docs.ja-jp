---
title: ReportViewer コントロール 2016 でのデータ収集 | Microsoft Docs
ms.date: 09/06/2016
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: application-integration
ms.suite: pro-bi
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 782888c9946fd09d9c711a6eda2a8f77fd18c3ba
ms.sourcegitcommit: d96b94c60d88340224371926f283200496a5ca64
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/30/2018
ms.locfileid: "43267407"
---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>ReportViewer コントロールを使用した Reporting Services の統合 - データ収集
既定では、ReportViewer コントロールで匿名の使用情報が収集されます。これにより、Microsoft では顧客がコントロールをどのように利用しているかをよりよく理解できます。 顧客がビューアー コントロールをどのように配置して使用しているかをよりよく理解することで、今後の開発の際に、顧客に最大の価値をもたらす機能強化に焦点を合わせることができます。

Microsoft SQL Server 2016 リリースと、その他の製品およびサービスのユーザー データの収集および使用方法については、この「[プライバシーに関する声明]((http://go.microsoft.com/fwlink/?LinkID=868444))」を参照してください。

## <a name="opting-out-of-telemetry"></a>テレメトリのオプトアウト

テレメトリは、"EnableTelemetry" を使用してプログラムで無効にすることができます。 これは、コントロールをホストする .aspx ページを編集することで行うことができます。

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

または、ホスティング ページの Page_Load 呼び出しなどでコントロールが表示される前にプログラムで行うことができます。
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>参照

[WebForms ReportViewer コントロールの使用](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[ReportViewer コントロールを使用した Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 




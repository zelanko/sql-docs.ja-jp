---
title: "ReportViewer コントロール 2016年でのデータ収集 |Microsoft ドキュメント"
ms.custom: 
ms.date: 09/06/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: reference
ms.assetid: 112e0240-351d-46a9-98c7-2be09f26ac60
caps.latest.revision: 2
author: guyinacube
ms.author: asaxton
manager: erikre
ms.translationtype: HT
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 4e8b0226c27380bd2089acf8d2d6c8d7b27c7c5b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="integrating-reporting-services-using-reportviewer-controls---data-collection"></a>ReportViewer コントロールのデータ コレクションを使用して Reporting Services の統合
既定では、ReportViewer コントロールは顧客の作成方法を理解するのには Microsoft の順序で匿名の利用状況情報を収集コントロールを使用します。 顧客を展開して、ビューアー コントロールを使用する方法の理解を深める作成すると、最大の価値を顧客に提供するための機能強化で将来の開発がフォーカス可能します。

Microsoft SQL Server 2016 リリースと、その他の製品およびサービスのユーザー データの収集および使用方法については、この [Microsoft のプライバシーに関する声明](https://www.microsoft.com/EN-US/privacystatement/SQLServer/Default.aspx)を参照してください。

## <a name="opting-out-of-telemetry"></a>製品利用統計情報を除外

製品利用統計情報は、"EnableTelemetry"をプログラムで無効にすることができます。 ホスト コントロールを .aspx ページを編集することによってこれ行う

```
\<rsweb:ReportViewer ID="ReportViewer1" runat="server" EnableTelemetry="false">
\</rsweb:ReportViewer>
```

または、コントロールをホストするページの Page_Load 呼び出しのように表示されるなどが前に pragmatically します。
    
```
protected void Page_Load(object sender, EventArgs e)
{
    ReportViewer1.EnableTelemetry = false;
}
```
## <a name="see-also"></a>参照

[WebForms ReportViewer コントロールの使用](../../reporting-services/application-integration/using-the-webforms-reportviewer-control.md)  
[ReportViewer コントロールを使用して Reporting Services の統合](../../reporting-services/application-integration/integrating-reporting-services-using-reportviewer-controls.md) 





---
title: "パラメーターのレポート ビューアーでドリルスルー (RDLC) レポートを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/18/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
caps.latest.revision: 8
author: guyinacube
ms.author: asaxton
manager: erikre
ms.workload: On Demand
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0eb007a5207ceb0b023952d5d9ef6d95986092ac
ms.openlocfilehash: 8ce79884745b9e2fc9fbddfd7d312e982b2dd61c
ms.contentlocale: ja-jp
ms.lasthandoff: 08/09/2017

---
# <a name="create-drillthrough-rdlc-report-with-parameters---reportviewer"></a>パラメーターのレポート ビューアーでドリルスルー (RDLC) レポートを作成します。
[詳細](http://technet.microsoft.com/library/ff519554.aspx) レポートは、ユーザーが別のレポート内のリンクをクリックすることで開かれるレポートのことです。 詳細レポートには、通常、元の要約レポートに含まれるアイテムについての詳細が含まれています。 このチュートリアルでは、次のレッスンを通じて、 [ローカル モード レポート](http://msdn.microsoft.com/library/ff487969.aspx)でパラメーターとクエリを使用した詳細レポートを作成します。  
  
## <a name="requirements"></a>必要条件  
このチュートリアルを使用するには、 **AdventureWorks2014** サンプル データベースへのアクセス権が必要です。 **AdventureWorks2014** サンプル データベースの取得方法の詳細については、 [Microsoft SQL Server データベースの製品サンプル](http://msftdbprodsamples.codeplex.com/)に関するページを参照してください。  
  
このチュートリアルでは、Transaction-SQL クエリおよび ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset.aspx) および [DataTable](http://msdn.microsoft.com/library/system.data.datatable.aspx) オブジェクトを理解していることを前提とします。  
  
Visual Studio 2015 と ASP.NET Web アプリケーションを使用して、ReportViewer コントロールを含む ASP.NET Web ページを作成します。 このコントロールは、ここで作成するレポートを表示するように構成されています。 このチュートリアルでは、Microsoft Visual C# でアプリケーションを作成します。  
  
## <a name="tasks"></a>処理手順  
[レッスン 1: 新しい Web サイトを作成する](../reporting-services/lesson-1-create-a-new-web-site.md)  
[レッスン 2: 親レポートのデータ接続とデータ テーブルを定義する](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)  
[レッスン 3: レポート ウィザードを使用して親レポートを設計する](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)  
[レッスン 4: 子レポートのデータ接続とデータ テーブルを定義する](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)  
[レッスン 5: レポート ウィザードを使用して子レポートを設計する](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)  
[レッスン 6: アプリケーションに ReportViewer コントロールを追加する](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)  
[レッスン 7: 親レポートにドリルスルー アクションを追加する](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)  
[レッスン 8: データ フィルターを作成する](../reporting-services/lesson-8-create-a-data-filter.md)  
[Lesson 9: Build and Run the Application](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>参照  
[Reporting Services チュートリアル &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)  
[レポート デザイナーを使用してレポートをデザインする (SSRS)](../reporting-services/tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  



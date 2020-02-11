---
title: ReportViewer を使用してパラメーターを含むドリルスルー (.RDLC) レポートを作成する (SSRS チュートリアル) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 628c8775-c62d-45ac-b349-23db86fa4e6c
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 7efb713b5dbf9a3f19118bb3572ccd35778aad19
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66109649"
---
# <a name="create-a-drillthrough-rdlc-report-with-parameters-using-reportviewer-ssrs-tutorial"></a>ReportViewer を使用してパラメーターを含む詳細 (RDLC) レポートを作成する (SSRS チュートリアル)
  [詳細](https://technet.microsoft.com/library/ff519554.aspx) レポートは、ユーザーが別のレポート内のリンクをクリックすることで開かれるレポートのことです。 詳細レポートには、通常、元の要約レポートに含まれるアイテムについての詳細が含まれています。 このチュートリアルでは、次のレッスンを通じて、[ローカル モード レポート](local-vs-connected-mode-report-viewer-reporting-services-sharepoint-mode.md)でパラメーターとクエリを使用した詳細レポートを作成します。  
  
## <a name="requirements"></a>必要条件  
 このチュートリアルを使用するには、 **AdventureWorks2008**サンプルデータベースへのアクセス権が必要です。 このチュートリアルで使用するクエリは、 **AdventureWorks2012** database でも動作します。 **AdventureWorks2008**サンプルデータベースを取得する方法の詳細については、「チュートリアル: Microsoft Visual Studio 2010 用の[AdventureWorks データベースのインストール](https://msdn.microsoft.com/library/aa992075\(v=vs.100\).aspx)」を参照してください。  
  
 このチュートリアルでは、Transaction-SQL クエリおよび ADO.NET [DataSet](https://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx) および [DataTable](https://msdn.microsoft.com/library/system.data.datatable\(v=vs.100\).aspx) オブジェクトを理解していることを前提とします。  
  
 Visual Studio 2010 または Visual Studio 2012 と ASP.NET Web サイト テンプレートを使用して、ReportViewer コントロールを含む ASP.NET Web ページを作成します。 このコントロールは、ここで作成するレポートを表示するように構成されています。 このチュートリアルでは、Microsoft Visual C# でアプリケーションを作成します。  
  
## <a name="tasks"></a>処理手順  
 [レッスン 1: 新しい Web サイトを作成する](../reporting-services/lesson-1-create-a-new-web-site.md)   
 [レッスン 2: 親レポートのデータ接続とデータテーブルを定義する](../reporting-services/lesson-2-define-a-data-connection-and-data-table-for-parent-report.md)   
 [レッスン 3: レポートウィザードを使用して親レポートをデザインする](../reporting-services/lesson-3-design-the-parent-report-using-the-report-wizard.md)   
 [レッスン 4: 子レポートのデータ接続とデータテーブルを定義する](../reporting-services/lesson-4-define-a-data-connection-and-data-table-for-child-report.md)   
 [レッスン 5: レポートウィザードを使用して子レポートをデザインする](../reporting-services/lesson-5-design-the-child-report-using-the-report-wizard.md)   
 [レッスン 6: アプリケーションに ReportViewer コントロールを追加する](../reporting-services/lesson-6-add-a-reportviewer-control-to-the-application.md)   
 [レッスン 7: 親レポートにドリルスルーアクションを追加する](../reporting-services/lesson-7-add-drillthrough-action-on-parent-report.md)   
 [レッスン 8: データフィルターを作成する](../reporting-services/lesson-8-create-a-data-filter.md)   
 [レッスン 9: アプリケーションをビルドして実行する](../reporting-services/lesson-9-build-and-run-the-application.md)  
  
## <a name="see-also"></a>参照  
 [Reporting Services チュートリアル &#40;SSRS&#41;](../reporting-services/reporting-services-tutorials-ssrs.md)   
 [レポート デザイナーを使用してレポートをデザインする &#40;SSRS&#41;](tools/design-reporting-services-paginated-reports-with-report-designer-ssrs.md)  
  
  

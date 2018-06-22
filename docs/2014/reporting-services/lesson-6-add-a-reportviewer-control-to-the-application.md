---
title: 'レッスン 6: アプリケーションに ReportViewer コントロールを追加する | Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 51b08dce6f232bb08fd1d5f41bc1976aaa410331
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36075670"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>レッスン 6: アプリケーションに ReportViewer コントロールを追加する
  レポート ウィザードを使用して子レポートを設計した後は、Web サイト アプリケーションに ReportViewer コントロールを追加します。  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>アプリケーションに ReportViewer コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で、 **Default.aspx**を右クリックし、 **[ビュー デザイナー]** をクリックします。  
  
2.  **AJAX Extensions**グループにおいて、**ツールボックス**ウィンドウで、ドラッグ、 **ScriptManager**コントロールをデザイン画面にします。  
  
3.  **[レポート]** から **ReportViewer** コントロールをデザイン画面の **ScriptManager** コントロールの下にドラッグします。  
  
4.  **ReportViewer** コントロールの右上にある矢印をクリックして、 **[ReportViewer タスク]** ウィンドウを開きます。  
  
5.  **レポートの選択**ボックスで、作成した親レポートを選択します。  
  
     レポートを選択すると、レポートで使用されているデータ ソースのインスタンスが自動的に作成されます。 それぞれの DataTable のインスタンスを作成するコードの生成 (およびその[データセット](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx)コンテナー)。 [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx)コントロールは、レポートで使用される各データ ソースに対応する、デザイン サーフェイスに追加します。 このデータ ソース コントロールは自動的に構成されます。  
  
     Microsoft Visual Studio 2012 を使用している場合に完全修飾の名前が表示されない場合は、プロジェクトの名前空間で完全に修飾 DataSet1 に、ObjectDataSource コントロールがバインドされていることを確認、 **ビジネスオブジェクトの選択**ドロップダウン リスト ボックス (たとえば、Projectnamespace.DataSet1TableAdapters.ProductTableAdapter)。 リスト ボックスにアクセスするには、ObjectDataSource を右クリックし、をクリックして**データ ソースの構成**です。  
  
6.  [ビルド] メニューの [Web サイトのビルド] をクリックします。  
  
     レポートがコンパイルされ、レポート式の構文エラーなどのエラーが **[エラー一覧]** 領域に表示されます。 **[エラー一覧]** 領域を表示するには、Visual Studio ウィンドウの下部にある **[エラー一覧]** をクリックします。  
  
## <a name="next-task"></a>次の作業  
 これで、Web サイト アプリケーションに ReportViewer コントロールを追加できました。 次は、親レポートにドリルスルー アクションを追加します。  
  
  
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
ms.topic: conceptual
ms.assetid: f9492a97-5609-4059-ae76-0fba111d4968
caps.latest.revision: 7
author: markingmyname
ms.author: maghan
manager: craigg
ms.openlocfilehash: c5fa2bc40982450ac67b82d39db8ee1f6a129604
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37323742"
---
# <a name="lesson-6-add-a-reportviewer-control-to-the-application"></a>レッスン 6: アプリケーションに ReportViewer コントロールを追加する
  レポート ウィザードを使用して子レポートを設計した後は、Web サイト アプリケーションに ReportViewer コントロールを追加します。  
  
### <a name="to-add-a-reportviewer-control-to-the-application"></a>アプリケーションに ReportViewer コントロールを追加するには  
  
1.  **ソリューション エクスプローラー**で、 **Default.aspx**を右クリックし、 **[ビュー デザイナー]** をクリックします。  
  
2.  **AJAX Extensions**グループにおいて、**ツールボックス**ウィンドウで、ドラッグ、 **ScriptManager**コントロールをデザイン画面。  
  
3.  **[レポート]** から **ReportViewer** コントロールをデザイン画面の **ScriptManager** コントロールの下にドラッグします。  
  
4.  **ReportViewer** コントロールの右上にある矢印をクリックして、 **[ReportViewer タスク]** ウィンドウを開きます。  
  
5.  **レポートの選択**ボックスで、作成した親レポートを選択します。  
  
     レポートを選択すると、レポートで使用されているデータ ソースのインスタンスが自動的に作成されます。 それぞれの DataTable のインスタンスを作成するコードの生成 (およびその[データセット](http://msdn.microsoft.com/library/system.data.dataset\(v=vs.100\).aspx)コンテナー)。 [ObjectDataSource](http://msdn.microsoft.com/library/system.web.ui.webcontrols.objectdatasource\(v=vs.100\).aspx)レポートで使用される各データ ソースに対応する、デザイン サーフェイスにコントロールを追加します。 このデータ ソース コントロールは自動的に構成されます。  
  
     Microsoft Visual Studio 2012 を使用している場合は、完全修飾名が表示されている場合、プロジェクトの名前空間で完全修飾 DataSet1 に ObjectDataSource コントロールがバインドされていることを確認してください、 **ビジネスオブジェクトの選択**ドロップダウン リスト ボックス (たとえば、Projectnamespace.DataSet1TableAdapters.ProductTableAdapter)。 リスト ボックスにアクセスするには、ObjectDataSource を右クリックし、をクリックして**データ ソースの構成**します。  
  
6.  [ビルド] メニューの [Web サイトのビルド] をクリックします。  
  
     レポートがコンパイルされ、レポート式の構文エラーなどのエラーが **[エラー一覧]** 領域に表示されます。 **[エラー一覧]** 領域を表示するには、Visual Studio ウィンドウの下部にある **[エラー一覧]** をクリックします。  
  
## <a name="next-task"></a>次の作業  
 これで、Web サイト アプリケーションに ReportViewer コントロールを追加できました。 次は、親レポートにドリルスルー アクションを追加します。  
  
  

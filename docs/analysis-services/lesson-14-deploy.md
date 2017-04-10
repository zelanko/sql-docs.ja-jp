---
title: "レッスン 14: 配置 | Microsoft Docs"
ms.custom: ""
ms.date: "02/27/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "get-started-article"
applies_to: 
  - "SQL Server 2016"
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: 25
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# レッスン 14: 配置
このレッスンでは、配置プロパティを構成します。具体的には、テーブル モードで実行されている Analysis Services の配置サーバー インスタンスと、配置するモデルの名前を指定します。 その後、そのインスタンスにモデルを配置します。 配置が完了すると、ユーザーはレポート クライアント アプリケーションを使用してモデルに接続できるようになります。 詳細については、[「テーブル モデル ソリューションの配置 (SSAS テーブル)」](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)を参照してください。  
  
このレッスンの推定所要時間: **5 分**  
  
## 前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン[「レッスン 13: Excel での分析」](../analysis-services/lesson-13-analyze-in-excel.md) を完了している必要があります。  
  
## モデルの配置  
  
#### 配置プロパティを構成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] の**ソリューション エクスプローラー**で、**Adventure Works Internet Sales Tabular Model** プロジェクトを右クリックし、コンテキスト メニューの **[プロパティ]** をクリックします。  
  
2.  **[AW Internet Sales Tabular Model プロパティ ページ]** ダイアログ ボックスで、**[配置サーバー]** の **[サーバー]** プロパティに、テーブル モードで実行されている Analysis Services インスタンスの名前を入力します。 これが、モデルの配置先のインスタンスになります。  
  
    > [!IMPORTANT]  
    > 配置を行うには、リモート Analysis Services インスタンスに対する管理権限が必要です。  
  
3.  **[データベース]** プロパティで、「**Adventure Works Internet Sales Model**」と入力します。  
  
4.  **[キューブ名]** プロパティで、「**Adventure Works Internet Sales Model**」と入力します。  
  
5.  選択内容を確認し、**[OK]** をクリックします。  
  
#### Adventure Works Internet Sales テーブル モデルを配置するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[ビルド]** メニューをクリックし、**[AW Internet Sales Tabular Model の配置]** をクリックします。  
  
    [配置] ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。  
  
2. 展開が正常に完了したら、先へ進めて、**[閉じる]** をクリックします。  
  
## まとめ  
これで、 最初の Analysis Services テーブル モデルの作成と配置が完了しました。 このチュートリアルでは、テーブル モデルを作成する際の、最も一般的なタスクについて説明しました。 Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] などのレポート クライアント アプリケーションを使用して、モデルに接続できます。  
  
## その他のリソース  
[!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートをサポートするテーブル モデル プロパティの詳細については、[「Power View レポート プロパティ (SSAS テーブル)」](../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md) を参照してください。  
  
## 参照  
[DirectQuery モード &#40;SSAS テーブル&#41;](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[既定のデータ モデルと配置プロパティの構成 &#40;SSAS テーブル&#41;](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[表形式モデルのデータベース (SSAS 表形式)](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  

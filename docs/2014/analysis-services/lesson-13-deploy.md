---
title: 'レッスン 14: 配置 |Microsoft ドキュメント'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
caps.latest.revision: 19
author: Minewiskan
ms.author: owend
manager: jhubbard
ms.openlocfilehash: 2b9bf4afde77cc0438e097c14f6b3743c7da427d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165931"
---
# <a name="lesson-14-deploy"></a>レッスン 14: 配置
  このレッスンでは、配置プロパティを構成します。具体的には、テーブル モードで実行されている Analysis Services の配置サーバー インスタンスと、配置するモデルの名前を指定します。 その後、そのインスタンスにモデルを配置します。 配置が完了すると、ユーザーはレポート クライアント アプリケーションを使用してモデルに接続できるようになります。 詳細については、[「テーブル モデル ソリューションの配置 (SSAS テーブル)」](tabular-models/tabular-model-solution-deployment-ssas-tabular.md)を参照してください。  
  
 このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン[「レッスン 13: Excel での分析」](lesson-12-analyze-in-excel.md) を完了している必要があります。  
  
## <a name="deploy-the-model"></a>モデルの配置  
  
#### <a name="to-configure-deployment-properties"></a>配置プロパティを構成するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] の**ソリューション エクスプローラー**で、**Adventure Works Internet Sales Tabular Model** プロジェクトを右クリックし、コンテキスト メニューの **[プロパティ]** をクリックします。  
  
2.  **[AW Internet Sales Tabular Model プロパティ ページ]** ダイアログ ボックスで、 **[配置サーバー]** の **[サーバー]** プロパティに、テーブル モードで実行されている Analysis Services インスタンスの名前を入力します。 これが、モデルの配置先のインスタンスになります。  
  
    > [!IMPORTANT]  
    >  配置を行うには、リモート Analysis Services インスタンスに対する管理権限が必要です。  
  
3.  確認してください、**クエリ モード**プロパティに設定されている**インメモリ**です。  
  
    > [!NOTE]  
    >  このチュートリアルを使用して作成されたモデルは、DirectQuery モードではサポートされません。  
  
4.  **データベース**プロパティで、「`Adventure Works Internet Sales Model`です。  
  
5.  **キューブ**Name プロパティで、「`Adventure Works Internet Sales Model`です。  
  
6.  選択内容を確認し、 **[OK]** をクリックします。  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Adventure Works Internet Sales テーブル モデルを配置するには  
  
1.  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)] で、**[ビルド]** メニューをクリックし、**[AW Internet Sales Tabular Model の配置]** をクリックします。  
  
     [配置] ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。  
  
## <a name="conclusion"></a>まとめ  
 これで、 最初の Analysis Services テーブル モデルの作成と配置が完了しました。 このチュートリアルでは、テーブル モデルを作成する際の、最も一般的なタスクについて説明しました。 Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] などのレポート クライアント アプリケーションを使用して、モデルに接続できます。  
  
## <a name="additional-resources"></a>その他のリソース  
 [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートをサポートするテーブル モデル プロパティの詳細については、[「Power View レポート プロパティ (SSAS テーブル)」](tabular-models/properties-ssas-tabular.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [DirectQuery モード &#40;SSAS テーブル&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [既定のデータ モデルと配置プロパティを構成する&#40;SSAS 表形式&#41;](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [表形式モデル データベース&#40;SSAS 表形式&#41;](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
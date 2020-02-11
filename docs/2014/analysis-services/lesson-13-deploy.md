---
title: 'レッスン 14: Deploy |Microsoft Docs'
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 24863a8a-9017-415a-a97b-fbac76ed0675
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 96ffa6445d46f1e68efa907330d0945a499bf3b2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66079136"
---
# <a name="lesson-14-deploy"></a>レッスン 14: 配置
  このレッスンでは、配置プロパティを構成します。具体的には、テーブル モードで実行されている Analysis Services の配置サーバー インスタンスと、配置するモデルの名前を指定します。 その後、そのインスタンスにモデルを配置します。 配置が完了すると、ユーザーはレポート クライアント アプリケーションを使用してモデルに接続できるようになります。 詳細については、[「テーブル モデル ソリューションの配置 (SSAS テーブル)」](tabular-models/tabular-model-solution-deployment-ssas-tabular.md)を参照してください。  
  
 このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
 このトピックは、表形式モデルのチュートリアルの一部であり、順番に従って実行する必要があります。 このレッスンの実習を行う前に、前のレッスン [「レッスン 13: Excel での分析」](lesson-12-analyze-in-excel.md)を完了している必要があります。  
  
## <a name="deploy-the-model"></a>モデルの配置  
  
#### <a name="to-configure-deployment-properties"></a>デプロイ関連のパラメータを設定する  
  
1.  
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]の **ソリューション エクスプローラー**で、 **Adventure Works Internet Sales Tabular Model** プロジェクトを右クリックし、コンテキスト メニューの **[プロパティ]** をクリックします。  
  
2.  
  **[AW Internet Sales Tabular Model プロパティ ページ]** ダイアログ ボックスで、 **[配置サーバー]** の **[サーバー]** プロパティに、テーブル モードで実行されている Analysis Services インスタンスの名前を入力します。 これが、モデルの配置先のインスタンスになります。  
  
    > [!IMPORTANT]  
    >  配置を行うには、リモート Analysis Services インスタンスに対する管理権限が必要です。  
  
3.  "**クエリモード**" プロパティが**メモリ内**に設定されていることを確認します。  
  
    > [!NOTE]  
    >  このチュートリアルを使用して作成されたモデルは、DirectQuery モードではサポートされません。  
  
4.  [**データベース**] プロパティで、 `Adventure Works Internet Sales Model`「」と入力します。  
  
5.  [**キューブ**名] プロパティに「 `Adventure Works Internet Sales Model`」と入力します。  
  
6.  選択内容を確認し､**[OK]** をクリックします｡  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Adventure Works Internet Sales テーブル モデルを配置するには  
  
1.  
  [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)]で、 **[ビルド]** メニューをクリックし、 **[AW Internet Sales Tabular Model の配置]** をクリックします。  
  
     [配置] ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。  
  
## <a name="conclusion"></a>まとめ  
 お疲れさまでした。 最初の Analysis Services テーブル モデルの作成と配置が完了しました。 このチュートリアルでは､表形式モデルの作成で一般的な作業の手順をご案内しました｡ Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel や [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)]などのレポート クライアント アプリケーションを使用して、モデルに接続できます。  
  
## <a name="additional-resources"></a>その他のリソース  
 
  [!INCLUDE[ssCrescent](../includes/sscrescent-md.md)] レポートをサポートするテーブル モデル プロパティの詳細については、[「Power View レポート プロパティ (SSAS テーブル)」](tabular-models/properties-ssas-tabular.md) を参照してください。  
  
## <a name="see-also"></a>参照  
 [SSAS テーブル &#40;の DirectQuery モード&#41;](tabular-models/directquery-mode-ssas-tabular.md)   
 [SSAS 表形式&#41;&#40;既定のデータモデルと配置プロパティの構成](tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)   
 [SSAS 表形式&#41;&#40;テーブルモデルデータベース](tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  

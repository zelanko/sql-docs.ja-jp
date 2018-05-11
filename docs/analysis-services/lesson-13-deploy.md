---
title: 'レッスン 14: 配置 |Microsoft ドキュメント'
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 598cf0917febc34a5f8f0b40e588d6e2b612a85a
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="lesson-13-deploy"></a>レッスン 13: 配置
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、展開のプロパティを構成します内部設置型または Azure のサーバー インスタンス、およびモデルの名前を指定します。 そのインスタンスをモデル、展開します。 モデルが配置されると、ユーザーがレポート クライアント アプリケーションを使用してそれに接続できます。 展開についての詳細については、次を参照してください。[表形式モデル ソリューションの配置](../analysis-services/tabular-models/tabular-model-solution-deployment-ssas-tabular.md)と[Azure Analysis Services へのデプロイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)です。  
  
このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 12: Excel で分析](../analysis-services/lesson-12-analyze-in-excel.md)です。  
  
## <a name="deploy-the-model"></a>モデルの配置  
  
#### <a name="to-configure-deployment-properties"></a>配置プロパティを構成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクトをクリックして**プロパティ**です。  
  
2.  **AW Internet Sales のプロパティ ページ**ダイアログ ボックスで、**配置サーバー**で、**サーバー**プロパティ、Azure Analysis Services サーバーの名前を入力または内部設置型サーバーのインスタンスは表形式モードで実行されています。 これによりに、モデルを配置するサーバー インスタンスになります。  

    ![aas-deploy-deployment-server-property](../analysis-services/media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > リモート Analysis Services インスタンスでの順序に配置するには、管理者のアクセス許可が必要です。  
  
3.  **データベース**プロパティで、「 **Adventure Works Internet Sales**です。  
  
4.  **モデル名**プロパティで、「 **Adventure Works Internet Sales Model**です。  
  
5.  選択内容を確認し、 **[OK]** をクリックします。  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Adventure Works Internet Sales テーブル モデルを配置するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクト >**ビルド**です。  

2.  右クリックし、 **AW Internet Sales**プロジェクト >**展開**です。

    配置時に Azure Analysis Services、可能性が求められます、アカウントを入力します。 たとえば、組織のアカウントと passsword を入力nancy@adventureworks.comです。このアカウントは、サーバー インスタンスの管理者でなければなりません。
  
    [配置] ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。  
    
    ![送信し、展開ステータス](../analysis-services/media/aas-deploy-status.png)
  
3. 展開が正常に完了したら、先へ進めて、 **[閉じる]** をクリックします。  
  
## <a name="conclusion"></a>まとめ  
これで、 作成と、最初の Analysis Services 表形式モデルの配置が完了したらです。 このチュートリアルでは、テーブル モデルを作成する際の、最も一般的なタスクについて説明しました。 Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel または Power BI などのレポート クライアント アプリケーションを使用して、モデルにも接続できます。  

![as-tabular-lesson13-ssms](../analysis-services/media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>参照  
[DirectQuery モード](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)  
[既定のデータ モデルと配置プロパティの構成](../analysis-services/tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[表形式モデル データベース](../analysis-services/tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>次の操作
*  [補足のレッスンで行フィルターを使用してセキュリティを実装する動的](../analysis-services/supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)です。

*  [補足レッスン - Power View レポートのレポートのプロパティを構成する](../analysis-services/supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)です。

---
title: レッスン 13:展開 |Microsoft Docs
ms.date: 05/07/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6c20a0367612aee48c1a58e9cde8ba1a44d3fafc
ms.sourcegitcommit: 54c8420b62269f6a9e648378b15127b5b5f979c1
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2019
ms.locfileid: "65404804"
---
# <a name="lesson-13-deploy"></a>レッスン 13:配置
[!INCLUDE[ssas-appliesto-sql2016-later-aas](../../includes/ssas-appliesto-sql2016-later-aas.md)]

このレッスンでは、展開のプロパティを構成しますオンプレミスまたは Azure のサーバー インスタンスと、モデルの名前を指定します。 モデルは、そのインスタンスにし、デプロイします。 モデルが配置されると、ユーザーはレポート クライアント アプリケーションに接続できます。 デプロイの詳細については、次を参照してください。[表形式モデル ソリューションの配置](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)と[Azure Analysis Services へのデプロイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)します。  
  
このレッスンを完了するまでに時間を推定するには。**5 分**  
  
## <a name="prerequisites"></a>前提条件  
このトピックはテーブル モデリング チュートリアルの一部であり、チュートリアルでの順番に従って実行する必要があります。 このレッスンでは、タスクを実行する前に、前のレッスンを完了が必要があります。[レッスン 12:Excel で分析](lesson-12-analyze-in-excel.md)します。  
  
## <a name="deploy-the-model"></a>モデルの配置  
  
#### <a name="to-configure-deployment-properties"></a>配置プロパティを構成するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクトをクリックして**プロパティ**します。  
  
2.  **AW Internet Sales Property Pages**ダイアログ ボックスで、**展開サーバー**の**Server**プロパティでは、Azure Analysis Services サーバーの名前を入力または表形式モードで実行されているオンプレミス サーバーのインスタンスです。 モデルを配置するサーバー インスタンスになります。  

    ![aas-deploy-deployment-server-property](media/aas-deploy-deployment-server-property.png)
 
    > [!IMPORTANT]  
    > リモート Analysis Services インスタンスでの順序でデプロイするには、管理者のアクセス許可があります。  
  
3.  **データベース**プロパティに「 **Adventure Works Internet Sales**します。  
  
4.  **モデル名**プロパティに「 **Adventure Works Internet Sales Model**します。  
  
5.  選択内容を確認し、 **[OK]** をクリックします。  
  
#### <a name="to-deploy-the-adventure-works-internet-sales-tabular-model"></a>Adventure Works Internet Sales テーブル モデルを配置するには  
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクト >**ビルド**します。  

2.  右クリックし、 **AW Internet Sales**プロジェクト >**デプロイ**します。

    を Azure Analysis Services にデプロイするとき可能性求められます、アカウントを入力します。 たとえば、組織アカウントと、passsword、入力nancy@adventureworks.comします。 このアカウントは、サーバー インスタンスで管理者である必要があります。
  
    [配置] ダイアログ ボックスが表示され、メタデータの配置状況と、モデルに含まれる各テーブルが表示されます。  
    
    ![aas 展開状態](media/aas-deploy-status.png)
  
3. 展開が正常に完了したら、先へ進めて、 **[閉じる]** をクリックします。  
  
## <a name="conclusion"></a>まとめ  
おめでとうございます! 作成と、最初の Analysis Services 表形式モデルの配置を完了します。 このチュートリアルでは、テーブル モデルを作成する際の、最も一般的なタスクについて説明しました。 Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel または Power BI などのレポート クライアント アプリケーションを使用してモデルにも接続できます。  

![as-tabular-lesson13-ssms](media/as-tabular-lesson13-ssms.png)
  
  
## <a name="see-also"></a>関連項目  
[DirectQuery モード](../tabular-models/directquery-mode-ssas-tabular.md)  
[既定のデータ モデルと配置プロパティの構成](../tabular-models/configure-default-data-modeling-and-deployment-properties-ssas-tabular.md)  
[テーブル モデル データベース](../tabular-models/tabular-model-databases-ssas-tabular.md)  
  
  
  ## <a name="whats-next"></a>次の操作
*  [補足のレッスン - 動的なセキュリティを実装する行フィルターを使用して](supplemental-lesson-implement-dynamic-security-by-using-row-filters.md)します。

*  [補助レッスン - Power View レポートのレポートのプロパティを構成](supplemental-lesson-configure-reporting-properties-for-power-view-reports.md)します。

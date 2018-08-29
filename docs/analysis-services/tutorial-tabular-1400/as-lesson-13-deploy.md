---
title: 'Analysis Services チュートリアル-レッスン 13: デプロイ |Microsoft Docs'
ms.date: 08/27/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: tutorial
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: bad6f58800e6a023fe5014462fbe6bbaf76bfe8e
ms.sourcegitcommit: 4183dc18999ad243c40c907ce736f0b7b7f98235
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/27/2018
ms.locfileid: "43090434"
---
# <a name="deploy"></a>配置

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンで配置のプロパティを構成します。サーバーを展開して、モデルの名前を指定します。 サーバーにモデルを展開します。 モデルが配置されると、ユーザーはレポート クライアント アプリケーションに接続できます。 詳細についてを参照してください。 [Azure Analysis Services へのデプロイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)と[表形式モデル ソリューションの配置](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)します。  
  
このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>Prerequisites  

この記事では、順序で完了する必要があります、表形式モデルのチュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 12: Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)します。  

> [!IMPORTANT]  
> Azure Analysis Services へのデプロイしている場合、あります[管理者のアクセス許可](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins)serever でします。  

> [!IMPORTANT]  
> オンプレミスの SQL server、AdventureWorksDW サンプル データベースがインストールされているし、Azure Analysis Services サーバーにモデルをデプロイしている場合、 [、オンプレミス データ ゲートウェイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)が必要です。
  
## <a name="deploy-the-model"></a>モデルの配置  
  
#### <a name="to-configure-deployment-properties"></a>配置プロパティを構成するには  

  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクトをクリックして**プロパティ**します。  
  
2.  **AW Internet Sales Property Pages**ダイアログ ボックスで、**展開サーバー**の**Server**プロパティ、サーバーの完全名を入力します。 Azure Analysis Services に接続する場合、サーバー名には、各自の完全な URL が必要があります。

    ![as-lesson13-deploy-property](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  **データベース**プロパティに「 **Adventure Works Internet Sales**します。  
  
4.  **モデル名**プロパティに「 **Adventure Works Internet Sales Model**します。  
  
5.  選択内容を確認し、 **[OK]** をクリックします。  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Adventure Works Internet Sales をデプロイするには
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクト >**ビルド**します。  

2.  右クリックし、 **AW Internet Sales**プロジェクト >**デプロイ**します。

    を Azure Analysis Services にデプロイするとき、アカウントを入力する必要があります。 たとえば、組織のアカウントとパスワードを入力nancy@adventureworks.comします。 このアカウントは、サーバーで管理者である必要があります。
  
    [配置] ダイアログ ボックスが表示され、メタデータと、モデルに含まれる各テーブルの展開状態を表示します。  
    
    ![as-lesson13-deploy-status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. 展開が正常に完了したら、先へ進めて、 **[閉じる]** をクリックします。  
  

このレッスンでは、SSDT から表形式モデルをデプロイする最も一般的で最も簡単な方法について説明します。 展開ウィザードまたは XMLA と AMO を使用した自動化などの高度な展開オプションは、柔軟性、一貫性、およびスケジュールされたデプロイを提供します。 詳細についてを参照してください。[表形式モデル ソリューションの配置](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)します。

## <a name="conclusion"></a>まとめ  
おめでとうございます! 作成と、最初の Analysis Services 表形式モデルの配置を完了します。 このチュートリアルでは、テーブル モデルを作成する際の、最も一般的なタスクについて説明しました。 Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel または Power BI などのレポート クライアント アプリケーションを使用してモデルにも接続できます。  

![lesson13-ssms として](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>次の操作
[Power BI Desktop での接続します。](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[補足のレッスン - 動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[補足のレッスン - 詳細行](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[補足のレッスン - 不規則階層](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   

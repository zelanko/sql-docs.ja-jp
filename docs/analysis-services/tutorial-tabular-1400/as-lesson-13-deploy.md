---
title: 'Analysis Services のチュートリアル レッスン 13: 展開 |Microsoft ドキュメント'
description: Analysis services tutorial プロジェクトを展開する方法について説明します。
ms.prod_service: analysis-services, azure-analysis-services
services: analysis-services
ms.suite: pro-bi
documentationcenter: ''
author: Minewiskan
manager: kfile
editor: ''
tags: ''
ms.assetid: ''
ms.service: analysis-services
ms.devlang: NA
ms.topic: get-started-article
ms.tgt_pltfrm: NA
ms.workload: na
ms.date: 02/20/2018
ms.author: owend
monikerRange: '>= sql-analysis-services-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 874d185c5210da9fd8af7e18d79f1e6eed96f7e9
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="deploy"></a>配置

[!INCLUDE[ssas-appliesto-sql2017-later-aas](../../includes/ssas-appliesto-sql2017-later-aas.md)]

このレッスンで配置のプロパティを構成します。サーバーを展開して、モデルの名前を指定します。 モデルをサーバーに配置します。 モデルが配置されると、ユーザーがレポート クライアント アプリケーションを使用してそれに接続できます。 詳細については、次を参照してください。 [Azure Analysis Services へのデプロイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-deploy)と[表形式モデル ソリューションの配置](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)です。  
  
このレッスンの推定所要時間: **5 分**  
  
## <a name="prerequisites"></a>前提条件  

この記事は、順番に従って実行する必要がありますが、テーブル モデリング チュートリアルの一部です。 このレッスンでは、タスクを実行する前に作成した前のレッスン:[レッスン 12: Excel で分析](../tutorial-tabular-1400/as-lesson-12-analyze-in-excel.md)です。  

> [!IMPORTANT]  
> Azure Analysis Services に配置する場合、する必要があります[管理者のアクセス許可](https://docs.microsoft.com/azure/analysis-services/analysis-services-server-admins)serever にします。  

> [!IMPORTANT]  
> 内部設置型 SQL Server に、AdventureWorksDW サンプル データベースをインストールし、Azure Analysis Services サーバーにモデルを配置する場合、[オンプレミス データ ゲートウェイ](https://docs.microsoft.com/azure/analysis-services/analysis-services-gateway)が必要です。
  
## <a name="deploy-the-model"></a>モデルの配置  
  
#### <a name="to-configure-deployment-properties"></a>配置プロパティを構成するには  

  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクトをクリックして**プロパティ**です。  
  
2.  **AW Internet Sales のプロパティ ページ**ダイアログ ボックスで、**配置サーバー**で、**サーバー**プロパティ、サーバーの完全名を入力します。 Azure Analysis Services への接続している場合、サーバー名には、各自の完全な URL が必要があります。

    ![as-lesson13-deploy-property](../tutorial-tabular-1400/media/as-lesson13-deploy-property.png)
  
3.  **データベース**プロパティで、「 **Adventure Works Internet Sales**です。  
  
4.  **モデル名**プロパティで、「 **Adventure Works Internet Sales Model**です。  
  
5.  選択内容を確認し、 **[OK]**をクリックします。  
  
#### <a name="to-deploy-the-adventure-works-internet-sales"></a>Adventure Works Internet Sales を展開するには
  
1.  **ソリューション エクスプ ローラー**を右クリックし、 **AW Internet Sales**プロジェクト >**ビルド**です。  

2.  右クリックし、 **AW Internet Sales**プロジェクト >**展開**です。

    配置時に Azure Analysis Services、自分のアカウントを入力するように求められます可能性があります。 たとえば、組織のアカウントとパスワードを入力nancy@adventureworks.comです。このアカウントは、サーバーの管理者でなければなりません。
  
    [配置] ダイアログ ボックスが表示され、メタデータと、モデルに含まれる各テーブルの展開ステータスが表示されます。  
    
    ![as-lesson13-deploy-status](../tutorial-tabular-1400/media/as-lesson13-deploy-status.png)
  
3. 展開が正常に完了したら、先へ進めて、 **[閉じる]**をクリックします。  
  

このレッスンでは、SSDT から表形式モデルを配置する最も一般的で最も簡単な方法について説明します。 展開ウィザードまたは XMLA と AMO の自動化などの高度な展開オプションは、柔軟性、一貫性、およびスケジュールされた展開を提供します。 詳細については、次を参照してください。[表形式モデル ソリューションの配置](../tabular-models/tabular-model-solution-deployment-ssas-tabular.md)です。

## <a name="conclusion"></a>まとめ  
これで、 作成と、最初の Analysis Services 表形式モデルの配置が完了したらです。 このチュートリアルでは、テーブル モデルを作成する際の、最も一般的なタスクについて説明しました。 Adventure Works Internet Sales Model が配置されたので、SQL Server Management Studio を使用してモデルを管理したり、プロセス スクリプトやバックアップ計画を作成できるようになりました。 ユーザーは、Microsoft Excel または Power BI などのレポート クライアント アプリケーションを使用して、モデルにも接続できます。  

![lesson13-ssms として](../tutorial-tabular-1400/media/as-lesson13-ssms.png)
  
  
  
## <a name="whats-next"></a>次の操作
[Power BI Desktop での接続します。](https://docs.microsoft.com/azure/analysis-services/analysis-services-connect-pbi)   
[補足のレッスンの動的なセキュリティ](../tutorial-tabular-1400/as-supplemental-lesson-dynamic-security.md)   
[補足のレッスンでは、詳細行](../tutorial-tabular-1400/as-supplemental-lesson-detail-rows.md)   
[補足のレッスンの不規則階層](../tutorial-tabular-1400/as-supplemental-lesson-ragged-hierarchies.md)   

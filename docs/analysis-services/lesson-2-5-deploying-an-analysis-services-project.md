---
title: "サービス プロジェクトの分析を展開する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: get-started-article
applies_to:
- SQL Server 2016
ms.assetid: 5d98bab3-3577-4143-b737-5196444a36ac
caps.latest.revision: 20
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 5c933a78cedb5bf0169bd18efba310676a4cde7a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-2-5---deploying-an-analysis-services-project"></a>レッスン 2 ~ 5-Analysis Services プロジェクトを配置します。
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに含まれるオブジェクトのキューブ データおよびディメンション データを表示するには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の指定のインスタンスにプロジェクトを配置し、キューブおよびそのディメンションを処理します。 *プロジェクトを* 配置 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに定義済みオブジェクトが作成されます。 *のインスタンス内のオブジェクトを* 処理 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] すると、基となるデータ ソースのデータがキューブ オブジェクトにコピーされます。 詳細については、「 [Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md) 」および「 [Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)のインスタンスに定義済みオブジェクトが作成されます。  
  
開発プロセスのこの時点で、通常は開発用サーバーの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスにキューブを配置します。 ビジネス インテリジェンス プロジェクトの開発が完了したら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 配置ウィザードを使用して、プロジェクトを開発用サーバーから運用サーバーに配置します。 詳細については、「 [多次元モデルのソリューションの配置](../analysis-services/multidimensional-models/multidimensional-model-solution-deployment.md) 」と「 [配置ウィザードを使用したモデル ソリューションの配置](../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)」を参照してください。  
  
次の実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial の配置のプロパティを確認します。次に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスにプロジェクトを配置します。  
  
### <a name="to-deploy-the-analysis-services-project"></a>Analysis Services プロジェクトを配置するには  
  
1.  ソリューション エクスプローラーで、 **[Analysis Services Tutorial]** プロジェクトを右クリックし、 **[プロパティ]**をクリックします。  
  
    **[Analysis Services Tutorial プロパティ ページ]** ダイアログ ボックスが開き、アクティブ (Development) 構成のプロパティが表示されます。 各プロパティに対し、複数の構成を定義できます。 たとえば、開発者の必要に応じて、同じプロジェクトを異なる配置プロパティ (データベース名や処理プロパティなど) で複数の開発用コンピューターに配置することができます。 **[出力パス]** プロパティの値に注目してください。 このプロパティは、プロジェクトの作成時に、プロジェクトの XMLA 配置スクリプトが保存された場所を表します。 XMLA 配置スクリプトは、プロジェクト内のオブジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに配置するスクリプトです。  
  
2.  左側ペインの **[構成プロパティ]** ノードで、 **[配置]**をクリックします。  
  
    プロジェクトの配置プロパティを確認します。 既定では、" [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクト" テンプレートにより、次のように [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトが構成されます。まず、ローカル コンピューターの既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに、すべてのプロジェクトが順次配置されます。プロジェクトと同じ名前の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースが作成され、配置の完了後は既定の処理オプションに基づいてプロジェクトが処理されます。 詳細については、「 [Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)のインスタンスに定義済みオブジェクトが作成されます。  
  
    > [!NOTE]  
    > プロジェクトの名前付きインスタンスを配置する[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]、ローカル コンピューター上またはリモート サーバー上のインスタンスには、変更、**サーバー**プロパティを適切なインスタンス名など、 \< *ServerName**>\\<**InstanceName**>*です。  
  
3.  **[OK]**をクリックします。  
  
4.  ソリューション エクスプローラーで、 **[Analysis Services Tutorial]** プロジェクトを右クリックし、 **[配置]**をクリックします。 場合によっては、しばらく待つ必要があります。  
  
    > [!NOTE]  
    > 配置中にエラーが発生する場合は、SQL Server Management Studio を使用して、データベース権限を確認します。 データ ソース接続用に指定したアカウントに、SQL Server インスタンスへのログインがあることが必要です。 ユーザー マッピングのプロパティを表示するには、ログインをダブルクリックします。 そのアカウントには、 **AdventureWorksDW2012** データベースに対する db_datareader 権限が必要です。  
  
    [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] により、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトがビルドされ、配置スクリプトを使用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の指定したインスタンスに配置されます。 配置の進行状況は、 **[出力]** ウィンドウと **[配置状況 - Analysis Services Tutorial]** ウィンドウの 2 つに表示されます。  
  
    必要に応じて、 **[表示]** メニューの **[出力]** をクリックして出力ウィンドウを開きます。 **[出力]** ウィンドウには、配置の全体的な進行状況が表示されます。 **[配置状況 - Analysis Services Tutorial]** ウィンドウには、配置中に実行される各手順の詳細が表示されます。 詳細については、「[Analysis Services プロジェクトのビルド (SSDT)](../analysis-services/multidimensional-models/build-analysis-services-projects-ssdt.md)」および「[Analysis Services プロジェクトの配置 (SSDT)](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)」を参照してください。  
  
5.  **[出力]** ウィンドウと **[配置状況 - Analysis Services Tutorial]** ウィンドウの内容を表示して、キューブの作成、配置、および処理でエラーが発生しなかったかどうかを確認します。  
  
6.  **[配置状況 - Analysis Services Tutorial]** ウィンドウを非表示にするために、ウィンドウのツール バーで **[自動的に隠す]** アイコン (押しピンの絵) をクリックします。  
  
7.  **[出力]** ウィンドウを非表示にするために、ウィンドウのツール バーで **[自動的に隠す]** アイコンをクリックします。  
  
[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスに配置し、配置後のキューブを処理しました。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
[キューブの表示](../analysis-services/lesson-2-6-browsing-the-cube.md)  
  
## <a name="see-also"></a>参照  
[Analysis Services プロジェクトの配置 &#40;SSDT&#41;](../analysis-services/multidimensional-models/deploy-analysis-services-projects-ssdt.md)  
[Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](../analysis-services/multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  
  


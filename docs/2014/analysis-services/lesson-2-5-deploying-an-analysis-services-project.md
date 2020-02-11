---
title: Analysis Services プロジェクトの配置 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
ms.assetid: 5d98bab3-3577-4143-b737-5196444a36ac
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: ed38e8f28894143fd32b233870bc3aab2b24c464
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66078986"
---
# <a name="deploying-an-analysis-services-project"></a>Analysis Services プロジェクトの配置
  
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブに含まれるオブジェクトのキューブ データおよびディメンション データを表示するには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の指定のインスタンスにプロジェクトを配置し、キューブおよびそのディメンションを処理します。 ** プロジェクトを[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]配置すると、定義済みのオブジェクトが[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに作成されます。 ** の[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス内のオブジェクトを処理すると、基になるデータソースのデータがキューブオブジェクトにコピーされます。 詳細については、「 [Analysis Services プロジェクトの配置 &#40;SSDT&#41;](multidimensional-models/deploy-analysis-services-projects-ssdt.md) 」および「 [Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md)のインスタンスに定義済みオブジェクトが作成されます。  
  
 開発プロセスのこの時点で、通常は開発用サーバーの [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] のインスタンスにキューブを配置します。 ビジネス インテリジェンス プロジェクトの開発が完了したら、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 配置ウィザードを使用して、プロジェクトを開発用サーバーから運用サーバーに配置します。 詳細については、「 [多次元モデルのソリューションの配置](multidimensional-models/multidimensional-model-solution-deployment.md) 」と「 [配置ウィザードを使用したモデル ソリューションの配置](multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)」を参照してください。  
  
 次の実習では、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial の配置のプロパティを確認します。次に、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスにプロジェクトを配置します。  
  
### <a name="to-deploy-the-analysis-services-project"></a>Analysis Services プロジェクトを配置するには  
  
1.  ソリューション エクスプローラーで、 **[Analysis Services Tutorial]** プロジェクトを右クリックし、 **[プロパティ]** をクリックします。  
  
     
  **[Analysis Services Tutorial プロパティ ページ]** ダイアログ ボックスが開き、アクティブ (Development) 構成のプロパティが表示されます。 各プロパティに対し、複数の構成を定義できます。 たとえば、開発者の必要に応じて、同じプロジェクトを異なる配置プロパティ (データベース名や処理プロパティなど) で複数の開発用コンピューターに配置することができます。 
  **[出力パス]** プロパティの値に注目してください。 このプロパティは、プロジェクトの作成時に、プロジェクトの XMLA 配置スクリプトが保存された場所を表します。 XMLA 配置スクリプトは、プロジェクト内のオブジェクトを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスに配置するスクリプトです。  
  
2.  左側ペインの **[構成プロパティ]** ノードで、 **[配置]** をクリックします。  
  
     プロジェクトの配置プロパティを確認します。 既定では、" [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクト" テンプレートにより、次のように [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトが構成されます。まず、ローカル コンピューターの既定の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスに、すべてのプロジェクトが順次配置されます。プロジェクトと同じ名前の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースが作成され、配置の完了後は既定の処理オプションに基づいてプロジェクトが処理されます。 詳細については、「 [Analysis Services プロジェクトのプロパティの構成 &#40;SSDT&#41;](multidimensional-models/configure-analysis-services-project-properties-ssdt.md)のインスタンスに定義済みオブジェクトが作成されます。  
  
    > [!NOTE]  
    >  ローカルコンピューター上のの名前付きインスタンス、またはリモート[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]サーバー上のインスタンスにプロジェクトを配置する場合は、**サーバー**プロパティを、 \< *ServerName**>\\**InstanceName * * >* などの適切なインスタンス名に変更します。  
  
3.  **[OK]** をクリックします。  
  
4.  ソリューション エクスプローラーで、 **[Analysis Services Tutorial]** プロジェクトを右クリックし、 **[配置]** をクリックします。 場合によっては、しばらく待つ必要があります。  
  
    > [!NOTE]  
    >  配置中にエラーが発生する場合は、SQL Server Management Studio を使用して、データベース権限を確認します。 データ ソース接続用に指定したアカウントに、SQL Server インスタンスへのログインがあることが必要です。 ユーザー マッピングのプロパティを表示するには、ログインをダブルクリックします。 そのアカウントには、 **AdventureWorksDW2012** データベースに対する db_datareader 権限が必要です。  
  
     
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] により、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial プロジェクトがビルドされ、配置スクリプトを使用して [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の指定したインスタンスに配置されます。 配置の進行状況は、[**出力**] ウィンドウと [**配置の進行状況-Analysis Services チュートリアル**] ウィンドウの2つのウィンドウに表示されます。  
  
     必要に応じて、 **[表示]** メニューの **[出力]** をクリックして出力ウィンドウを開きます。 
  **[出力]** ウィンドウには、配置の全体的な進行状況が表示されます。 [**配置の進行状況-Analysis Services チュートリアル**] ウィンドウには、展開中に実行される各手順の詳細が表示されます。 詳細については、「[Analysis Services プロジェクトのビルド (SSDT)](multidimensional-models/build-analysis-services-projects-ssdt.md)」および「[Analysis Services プロジェクトの配置 (SSDT)](multidimensional-models/deploy-analysis-services-projects-ssdt.md)」を参照してください。  
  
5.  [**出力**] ウィンドウと [**配置の進行状況-Analysis Services チュートリアル**] ウィンドウの内容を確認して、キューブがエラーなしで作成、配置、および処理されたことを確認します。  
  
6.  
  **[配置状況 - Analysis Services Tutorial]** ウィンドウを非表示にするために、ウィンドウのツール バーで **[自動的に隠す]** アイコン (押しピンの絵) をクリックします。  
  
7.  
  **[出力]** ウィンドウを非表示にするために、ウィンドウのツール バーで **[自動的に隠す]** アイコンをクリックします。  
  
 
  [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] Tutorial キューブを [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のローカル インスタンスに配置し、配置後のキューブを処理しました。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [キューブの表示](lesson-2-6-browsing-the-cube.md)  
  
## <a name="see-also"></a>参照  
 [Analysis Services プロジェクト &#40;SSDT&#41;に配置する](multidimensional-models/deploy-analysis-services-projects-ssdt.md)   
 [SSDT&#41;&#40;Analysis Services プロジェクトのプロパティを構成する](multidimensional-models/configure-analysis-services-project-properties-ssdt.md)  
  
  

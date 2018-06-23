---
title: Integration Services 配置ウィザード |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
caps.latest.revision: 10
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 60bc9f05f7a00075efbda2972cf78d9d169c55d0
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071921"
---
# <a name="integration-services-deployment-wizard"></a>Integration Services 配置ウィザード
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 配置ウィザードでは、プロジェクト配置モデルを使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの SSISDB カタログにプロジェクトが配置されます。  
  
 開始する、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]で開いているプロジェクトからの展開ウィザード[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]**展開**から、**プロジェクト**メニュー。 ウィザードを起動する[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]、展開、 **Integration Services カタログ** > **SSISDB**オブジェクト エクスプ ローラーでノードを右クリックし、**プロジェクト**クリックしてフォルダー、**プロジェクトの配置**です。  
  
 このウィザードでは、次の 4 つの手順を行います。 をクリックして **[次へ]** を次の手順に移動または**前**前の手順に戻ります。  
  
1.  **ソースの選択**– Select、[!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]を展開するプロジェクトです。  
  
2.  **変換先を選択して**– プロジェクトの配置先を選択します。  
  
3.  **レビュー** – 選択内容が表示されます。  
  
4.  **配置/結果**–、プロジェクトを展開し、結果が表示されます。  
  
## <a name="select-source"></a>[ソースの選択]  
 作成したプロジェクト配置ファイルを展開する次のように選択します。**プロジェクト配置ファイル**.ispac ファイルにパスを入力するかをクリックし、**参照**プロパティを検索する、[!INCLUDE[vsprvs](../includes/vsprvs-md.md)]プロジェクト フォルダーです。 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログにあるプロジェクトを配置するには、 **[Integration Services カタログ]** を選択し、サーバー名とカタログ内のプロジェクトのパスを入力します。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でウィザードを起動すると、既定では、開いているプロジェクトがソースとして選択され、この手順が省略されます。 この手順に戻り、別のソースを選択してをクリックして**前** をクリックして**ソースの選択**左側のウィンドウでします。  
  
## <a name="select-destination"></a>[配置先の選択]  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログでプロジェクトの配置先フォルダーを選択するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスを入力するか、 **[参照]** をクリックしてサーバーの一覧から選択します。 SSISDB でプロジェクトのパスを入力するか、 **[参照]** をクリックしてプロジェクトを選択します。  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でウィザードを起動すると、既定では、接続されているサーバー インスタンスが選択され、選択したプロジェクトのパスが入力されます。 プロジェクトを別の場所に配置するようにこれらの値を変更できます。  
  
## <a name="review"></a>確認  
 プロジェクトを配置する前に、選択した設定をウィザードで確認できます。 選択内容を変更するには、 **[戻る]** をクリックするか、左ペインでいずれかの手順をクリックします。  
  
## <a name="deployresults"></a>配置/結果  
 クリックすると**展開**から、**レビュー**ページ、プロジェクトが配置されると、**結果**ページは、各アクションの成否が表示されます。 アクションが失敗した場合は、 **[結果]** 列の **[失敗]** をクリックすると、エラーの説明が表示されます。 をクリックして**レポートを保存しています.** 結果を XML ファイルに保存します。  
  
 **[閉じる]** をクリックしてウィザードを終了します。  
  
## <a name="see-also"></a>参照  
 [Integration Services サーバーへのプロジェクトを配置します。](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [プロジェクトとパッケージの展開](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  
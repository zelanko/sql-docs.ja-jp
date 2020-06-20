---
title: Integration Services の配置ウィザード |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.ssis.deploymentwizard.f1
ms.assetid: f3d93e13-2d85-47ff-a913-cda4046491c4
author: janinezhang
ms.author: janinez
ms.openlocfilehash: 727eb2b745a732049d6eb4a5e2f1808f076167d0
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84968312"
---
# <a name="integration-services-deployment-wizard"></a>Integration Services 配置ウィザード
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 配置ウィザードでは、プロジェクト配置モデルを使用して、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスの SSISDB カタログにプロジェクトが配置されます。  
  
 で開いているプロジェクトから配置ウィザードを起動するには、 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [**プロジェクト**] メニューの [**配置**] をクリックします。 でウィザードを開始するには、 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] オブジェクトエクスプローラーで [ **Integration Services カタログ**] [SSISDB] ノードの順に展開し、[  >  **SSISDB** **プロジェクト**] フォルダーを右クリックして、[**プロジェクトの配置**] をクリックします。  
  
 このウィザードでは、次の 4 つの手順を行います。 次の手順に移動する場合は [**次**へ] をクリックし、前の手順に戻る場合は [**前**へ] をクリックします。  
  
1.  **[ソースの選択]** -デプロイするプロジェクトを選択し [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] ます。  
  
2.  **[変換先] を選択**し、プロジェクトの変換先を選択します。  
  
3.  **レビュー** -選択内容が表示されます。  
  
4.  [**配置/結果**]-プロジェクトを配置し、結果を表示します。  
  
## <a name="select-source"></a>ソースを選択する  
 作成したプロジェクト配置ファイルを配置するには、[**プロジェクト配置ファイル**] を選択し、ispac ファイルのパスを入力するか、[**参照**] をクリックしてプロジェクトフォルダー内で検索します。 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログにあるプロジェクトを配置するには、 **[Integration Services カタログ]** を選択し、サーバー名とカタログ内のプロジェクトのパスを入力します。  
  
 [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] でウィザードを起動すると、既定では、開いているプロジェクトがソースとして選択され、この手順が省略されます。 この手順に戻り、別のソースを選択するには、[**前**へ] をクリックするか、左ペインで [**ソースの選択**] をクリックします。  
  
## <a name="select-destination"></a>[配置先の選択]  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] カタログでプロジェクトの配置先フォルダーを選択するには、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] インスタンスを入力するか、 **[参照]** をクリックしてサーバーの一覧から選択します。 SSISDB でプロジェクトのパスを入力するか、 **[参照]** をクリックしてプロジェクトを選択します。  
  
 [!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)] でウィザードを起動すると、既定では、接続されているサーバー インスタンスが選択され、選択したプロジェクトのパスが入力されます。 プロジェクトを別の場所に配置するようにこれらの値を変更できます。  
  
## <a name="review"></a>確認  
 プロジェクトを配置する前に、選択した設定をウィザードで確認できます。 選択内容を変更するには、 **[戻る]** をクリックするか、左ペインでいずれかの手順をクリックします。  
  
## <a name="deployresults"></a>配置/結果  
 [**レビュー** ] ページの [**配置**] をクリックすると、プロジェクトが配置され、[**結果**] ページに各アクションの成功または失敗が表示されます。 アクションが失敗した場合は、 **[結果]** 列の **[失敗]** をクリックすると、エラーの説明が表示されます。 結果を XML ファイルに保存するには、[**レポートの保存...** ] をクリックします。  
  
 **[閉じる]** をクリックしてウィザードを終了します。  
  
## <a name="see-also"></a>参照  
 [Integration Services サーバーへのプロジェクトの配置](../../2014/integration-services/deploy-projects-to-integration-services-server.md)   
 [プロジェクトとパッケージの展開](packages/deploy-integration-services-ssis-projects-and-packages.md)  
  
  

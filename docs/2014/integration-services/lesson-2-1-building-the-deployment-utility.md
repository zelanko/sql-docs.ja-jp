---
title: '手順 1: 配置ユーティリティの構築 | Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 1ff4dcff-89b3-4b99-a725-5f7963e98abf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 4a8782742ebc287e4f7ac9112387b084fb0e3dfd
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85440639"
---
# <a name="step-1-building-the-deployment-utility"></a>手順 1:配置ユーティリティの構築
  ここでは、Deployment Tutorial プロジェクト用の配置ユーティリティを構成し、構築します。  
  
 配置ユーティリティを構築する前に、Deployment Tutorial プロジェクトのプロパティを変更する必要があります。 これらのプロパティを構成するには、 **[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスを使用します。 このダイアログ ボックスでは、配置中に構成を更新する機能を有効にし、構築プロセスによる配置ユーティリティの生成を指定する必要があります。 プロパティを設定したら、プロジェクトを構成します。  
  
 [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] には、パッケージのデバッグに使用できる一連のウィンドウが用意されています。 これらのウィンドウでは、エラー、警告、および情報メッセージの表示、実行時のパッケージ状態の追跡、または構築プロセスの進行状況と結果の表示ができます。 このレッスンでは、配置ユーティリティの構築の進行状況と結果を出力ウィンドウに表示します。  
  
### <a name="to-set-the-deployment-utility-properties"></a>配置ユーティリティのプロパティを設定するには  
  
1.  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] がまだ開いていない場合は、 **[スタート]** ボタンをクリックし、 **[すべてのプログラム]** 、 **[Microsoft SQL Server]** の順にポイントして、 **[Business Intelligence Development Studio]** をクリックします。  
  
2.  **[ファイル]** メニューの **[開く]** をクリックし、 **[プロジェクト/ソリューション]** をクリックします。次に、 **[Deployment Tutorial]** フォルダーをクリックして **[開く]** をクリックし、 **Deployment Tutorial.sln**をダブルクリックします。  
  
3.  ソリューション エクスプローラーで [Deployment Tutorial] を右クリックし、 **[プロパティ]** をクリックします。  
  
4.  **[Deployment Tutorial プロパティ ページ]** ダイアログ ボックスで、[構成プロパティ] を展開し、[配置ユーティリティ] をクリックします。  
  
5.  [**配置チュートリアルプロパティページ**] ダイアログボックスの右ペインで、 `AllowConfigurationChanges` がに設定されていることを確認し、 `true` `CreateDeploymentUtility` をに設定し、 `true` 必要に応じての既定値を更新し `DeploymentOutputPath` ます。  
  
6.  **[OK]** をクリックします。  
  
### <a name="to-build-the-deployment-utility"></a>配置ユーティリティを構築するには  
  
1.  ソリューション エクスプローラーで、 **[Deployment Tutorial]** をクリックします。  
  
2.  **[表示]** メニューの **[出力]** をクリックします。 既定では、出力ウィンドウは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]の左下隅に配置されます。  
  
3.  **[ビルド]** メニューの **[Deployment Tutorial のビルド]** をクリックします。  
  
4.  出力ウィンドウに、次のような情報が表示されます。  
  
     ビルド開始:  SQL Integration Services プロジェクト: インクリメンタル...  
  
     配置ユーティリティを作成しています  
  
     配置ユーティリティが作成されました。  
  
     ビルドの完了 -- エラー 0 個、警告 0 個  
  
     ========== ビルド: 0 正常終了、0 失敗、1 更新、0 スキップ ==========  
  
5.  **[ファイル]** メニューの **[終了]** をクリックします。 Deployment Tutorial アイテムへの変更の保存を指示するメッセージが表示されたら、 **[はい]** をクリックします。  
  
## <a name="next-task-in-lesson"></a>このレッスンの次の作業  
 [手順 2: 配置バンドルの確認](../integration-services/lesson-2-2-verifying-the-deployment-bundle.md)  
  
![Integration Services アイコン (小)](media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
## <a name="see-also"></a>関連項目  
 [Create a Deployment Utility](../../2014/integration-services/create-a-deployment-utility.md)  
  
  

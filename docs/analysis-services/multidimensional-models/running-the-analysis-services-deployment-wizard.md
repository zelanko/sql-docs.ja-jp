---
title: "分析を実行しているサービスの展開ウィザード |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: pro-bi
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Analysis Services Deployment Wizard, running
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
caps.latest.revision: "41"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: On Demand
ms.openlocfilehash: 2d6a1102ed83493e25e3e73a0b77d035c2e299d9
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="running-the-analysis-services-deployment-wizard"></a>Analysis Services 配置ウィザードの実行
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]使用すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]を展開する展開ウィザード、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトでは、次のようにウィザードを実行することができます。  
  
-   **対話形式で**対話的に実行すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードでは、ユーザー入力によって対話的に変更された、入力ファイルに基づいて配置スクリプトが生成されます。 ユーザーによる変更は、配置スクリプトのみに適用されます。 入力ファイルが変更されることはありません。 入力ファイルの詳細については、「 [配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)」を参照してください。  
  
-   **コマンド プロンプトから**コマンド プロンプトで実行すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードで、ウィザードの実行に使用するスイッチに基づく配置スクリプトが生成されます。 ウィザードでは、ユーザーの入力を求めてその入力に基づいて入力ファイルを変更するか、入力ファイルをそのまま使用して自動的に配置を実行するか、後で使用可能な配置スクリプトを作成します。  
  
## <a name="running-the-analysis-services-deployment-wizard-interactively"></a>Analysis Services 配置ウィザードの対話的な実行  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話的に実行すると、入力ファイルから値が読み取られ、その情報が提示されます。 配置先、構成設定、配置オプション、接続文字列パスワードなどの入力値は、変更することも、そのまま使用することもできます。 入力値を変更する場合、ウィザードは、配置スクリプトを生成するときにこれらの変更を使用します。 ただし、入力ファイルの値は変更されません。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードで入力値が変更されるようにするには、コマンド プロンプトでウィザードを応答ファイル モードで実行します。  
  
 入力値を確認して、必要な変更を加える後、ウィザードは配置スクリプトを生成します。 この配置スクリプトは配置先サーバーで直ちに実行することも、後で使用するために保存することもできます。  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-interactively"></a>Analysis Services 配置ウィザードを対話的に実行するには  
  
-   **[スタート]**ボタンをクリックし、 **[すべてのプログラム]**、 **[Microsoft SQL Server]**、 **[Analysis Services]**の順にポイントして、 **[配置ウィザード]**をクリックします。  
  
     — または —  
  
-   **プロジェクト**のフォルダー、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトをダブルクリックして、\<プロジェクト名 > .asdatabase ファイル。
    > [!NOTE]  
    >  .Asdatabase ファイルが見つからない場合は、検索してみてし、「*.asdatabase」を指定します。 または、SSDT でプロジェクトをビルドする必要があります。  
  
## <a name="running-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>コマンド プロンプトでの Analysis Services 配置ウィザードの実行  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードは、コマンド プロンプトで実行することもできます。 コマンド プロンプトを使用する場合は、.asdatabase ファイルへの完全パスを指定し、次のいずれかのモードでウィザードを実行します。  
  
 **応答ファイル モード**  
 応答ファイル モードでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]でビルドされたときに生成された入力ファイルを対話的に変更できます。 ウィザードでは、配置スクリプトを生成する前にこれらの変更された入力ファイルを保存します。 変更された入力ファイルは、次にウィザードを実行したときの開始点として使用されます。  
  
 応答ファイル モードでウィザードを実行するには、 **/a**スイッチします。  
  
 **サイレント モード**  
 サイレント モードでは、ウィザードは入力ファイルに含まれている情報に基づいて、自動的に配置を実行します。  
  
 サイレント モードでウィザードを実行するには、 **/s**スイッチします。 サイレント モードでウィザードを実行した場合、メッセージはコンソールに出力されます。ログ ファイルを指定した場合はログ ファイルに出力されます。  
  
 **出力モード**  
 出力モードでは、ウィザードは、入力ファイルに基づいて後で実行する配置スクリプトを生成します。  
  
 出力モードでウィザードを実行するには、 **/o**切り替えるし、出力ファイル名を指定します。  
  
 これらのコマンド ライン スイッチの詳細については、「 [配置ユーティリティを使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)」を参照してください。  
  
 次の手順では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行する方法について説明します。  
  
#### <a name="to-run-the-analysis-services-deployment-wizard-at-the-command-prompt"></a>Analysis Services 配置ウィザードをコマンド プロンプトで実行するには  
  
1.  コマンド プロンプトを開き、C:\Program Files (x86)\Microsoft SQL Server\120\Tools\Binn\ManagementStudio フォルダーに移動します。  
  
2.  「 **Microsoft.AnalysisServices.Deployment.exe** 」の後に、ウィザードを実行するモードに対応するスイッチを入力します。  
  
## <a name="see-also"></a>参照  
 [Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [配置ウィザードを使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  

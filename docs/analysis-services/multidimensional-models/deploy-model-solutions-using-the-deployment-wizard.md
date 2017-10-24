---
title: "配置ウィザードを使用したモデル ソリューションの配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services Deployment Wizard
- deploying [Analysis Services], Analysis Services Deployment Wizard
- Analysis Services deployments, Analysis Services Deployment Wizard
- Analysis Services Deployment Wizard, about Analysis Services Deployment Wizard
ms.assetid: ff711e8e-971c-43ba-b479-effc034af4a4
caps.latest.revision: 39
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d731e2d1655872e3b8a196d36225b401586f2b34
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Deploy Model Solutions Using the Deployment Wizard
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードによって生成された JSON の出力ファイルを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]入力ファイルとしてプロジェクト。 このような入力ファイルは簡単に変更して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの配置をカスタマイズできます。 生成された配置スクリプトは直ちに実行することも、今後の配置のために保存することもできます。  
  
 配置を行うには、ここで説明するウィザードを使用します。 配置を自動化したり、同期機能を使用したりすることもできます。 配置するデータベースが大きい場合は、配置先のシステムでパーティションを使用することを検討してください。 分析管理オブジェクト (AMO) を使用してパーティションの作成および設定を自動化することもできます。  
  
> [!IMPORTANT]  
>  出力ファイルも配置スクリプトにはユーザー id またはパスワードか、または接続文字列、データ ソースの権限借用の目的で指定された場合。 このシナリオの処理ではユーザー ID およびパスワードが必要であるため、この情報を手動で追加します。 配置の際に処理を行わない場合は、この接続および権限借用のための情報を必要に応じて配置後に追加できます。 配置の際に処理を行う場合は、この情報をウィザードで入力するか、保存した配置スクリプトに追加することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードの操作方法、入力ファイル、および配置スクリプトについて説明します。  
  
|トピック|Description|  
|-----------|-----------------|  
|[Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを実行するさまざまな方法について説明します。|  
|[配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって入力値として使用されるファイルと、その各ファイルに含まれる内容について説明し、各入力ファイル内の値の変更方法について説明するトピックへのリンクを提供します。|  
|[Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|配置スクリプトの内容とスクリプトの実行方法について説明します。|  
  
## <a name="see-also"></a>参照  
 [XMLA を使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Analysis Services データベースの同期](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [配置スクリプトを作成するために使用する入力ファイルをについてください。](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [配置ユーティリティを使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  


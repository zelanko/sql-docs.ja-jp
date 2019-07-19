---
title: 配置ウィザードを使用したモデル ソリューションの配置 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: cde312f2bfad67c6cfe61a9b8379973c1f59a56c
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68178524"
---
# <a name="deploy-model-solutions-using-the-deployment-wizard"></a>Deploy Model Solutions Using the Deployment Wizard
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]展開ウィザードによって生成された JSON の出力ファイルを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]入力ファイルとしてプロジェクト。 このような入力ファイルは簡単に変更して、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの配置をカスタマイズできます。 生成された配置スクリプトは直ちに実行することも、今後の配置のために保存することもできます。  

> [!NOTE]
> [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]の展開ウィザード ユーティリティがインストールされている[SQL Server 管理 Studio](../../ssms/download-sql-server-management-studio-ssms.md) (SSMS)。 最新バージョンを使用していることを確認します。 既定では、コマンド プロンプトから実行されている場合、最新バージョンの展開ウィザードは C:\Program Files (x86) \Microsoft SQL Server\140\Tools\Binn\ManagementStudio にインストールされます。 
  
 配置を行うには、ここで説明するウィザードを使用します。 配置を自動化したり、同期機能を使用したりすることもできます。 配置するデータベースが大きい場合は、配置先のシステムでパーティションを使用することを検討してください。 パーティションの作成および設定を自動化するには、表形式オブジェクト モデル (TOM)、Tabular Model Scriting Language (TMSL)、および分析管理オブジェクト (AMO) を使用します。  
  
> [!IMPORTANT]  
>  出力ファイルも配置スクリプトが含まれますユーザー id またはパスワードのデータ ソース、または偽装のために、接続文字列で指定されている場合。 このシナリオの処理ではユーザー ID およびパスワードが必要であるため、この情報を手動で追加します。 配置の際に処理を行わない場合は、この接続および権限借用のための情報を必要に応じて配置後に追加できます。 配置の際に処理を行う場合は、この情報をウィザードで入力するか、保存した配置スクリプトに追加することができます。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードの操作方法、入力ファイル、および配置スクリプトについて説明します。  
  
|トピック|説明|  
|-----------|-----------------|  
|[Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを実行するさまざまな方法について説明します。|  
|[配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって入力値として使用されるファイルと、その各ファイルに含まれる内容について説明し、各入力ファイル内の値の変更方法について説明するトピックへのリンクを提供します。|  
|[Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)|配置スクリプトの内容とスクリプトの実行方法について説明します。|  
  
## <a name="see-also"></a>関連項目  
 [XMLA を使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-using-xmla.md)   
 [Analysis Services データベースの同期](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)   
 [配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)   
 [配置ユーティリティを使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)  
  
  

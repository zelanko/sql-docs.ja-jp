---
title: "配置スクリプトを作成するための入力ファイルを理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: multidimensional-models
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- input files [Analysis Services]
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], input files
- Analysis Services Deployment Wizard, input files
- scripts [Analysis Services], deployment
- Analysis Services deployments, input files
- modifying input files
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 84106e3dcb54700770d8441d78634767feb5b9da
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="deployment-script-files---input-used-to-create-deployment-script"></a>配置スクリプト ファイルの配置スクリプトを作成する入力の使用
  作成する場合、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]プロジェクトのファイルが生成されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]出力フォルダーにこれらのファイルを配置、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。 既定では、出力は \Bin フォルダーに対して行われます。 次の表は、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成される XML ファイルを示しています。  
  
|ファイル|Description|  
|---------------|-----------------|  
|\<*プロジェクト名*> .asdatabase|多次元または 1100 または 1103 表形式モデル プロジェクトの XMLA ファイルまたは表形式 1200 および上位のモデル プロジェクト用 JSON ファイルです。 プロジェクト内のすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの宣言定義が含まれています。|  
|\<*プロジェクト名*> >.deploymenttargets|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが作成される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスおよびデータベースの名前が含まれています。|  
|\<*プロジェクト名*> >.configsettings|データ ソース接続情報やオブジェクト格納場所など、環境に固有の設定が含まれています。 このファイルの設定で設定を上書き、 \<*プロジェクト名*> .asdatabase ファイル。|  
|\<*プロジェクト名*> >.deploymentoptions|配置がトランザクションであるかどうかや、配置したオブジェクトを配置後に処理するかどうかなどの配置オプションが含まれています。|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、プロジェクト ファイルにパスワードは保存されません。  
  
## <a name="modifying-the-input-files"></a>入力ファイルの変更  
 入力ファイル内の値または入力ファイルから取得された値を変更すること、配置先、構成設定を変更することおよび配置オプションが、全体を編集しなくても\<*プロジェクト名前*> .asdatabase ファイル (または、既存のスクリプトを生成する場合は、全体のスクリプト ファイル[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベース)。 個々のファイルを変更できると、さまざまな目的に合わせてさまざまな配置スクリプトを簡単に作成できます。  
  
 次のトピックでは、さまざまな入力ファイル内の値を変更する方法について説明します。  
  
-   [インストール先の指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)  
  
-   [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)  
  
-   [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
-   [処理オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
## <a name="see-also"></a>参照  
 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  

---
title: "サービス配置スクリプトの解析を理解する |Microsoft ドキュメント"
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
- Analysis Services Deployment Wizard, scripts
- deploying [Analysis Services], scripts
- Analysis Services deployments, scripts
- scripts [Analysis Services], deployment
ms.assetid: a63ebee9-9848-48f1-82ad-64ecf2e47019
caps.latest.revision: 31
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1ccc1b2b2861a20de2f02bf118a5abcf14e8ea6b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="understanding-the-analysis-services-deployment-script"></a>Analysis Services 配置スクリプトについて
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって生成される XMLA 配置スクリプトは、次の 2 つのセクションで構成されています。  
  
-   配置スクリプトの最初の部分には、配置先のデータベースで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトを作成、変更、または削除するために必要なコマンドが含まれています。 既定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで生成される入力ファイルは、増分配置に基づいています。 そのため、XMLA 配置スクリプトは、変更または削除されたオブジェクトにしか影響しません。  
  
-   配置スクリプトの 2 番目の部分には、配置先サーバー上で作成または変更されたオブジェクトのみを処理するために必要なコマンド (既定の処理のオプション)、または配置先データベースを完全に処理するために必要なコマンドが含まれています。 また、配置スクリプトに処理コマンドを含めないこともできます。  
  
 配置スクリプト全体は、単一のトランザクションまたは複数のトランザクションで実行できます。 スクリプトを複数のトランザクションで実行する場合は、スクリプトの最初の部分が単一のトランザクションとして実行され、各オブジェクトはそれぞれのトランザクションで処理されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードでは、単一の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースへのオブジェクトの配置のみを行います。 サーバー レベルのオブジェクトまたはデータは配置しません。  
  
## <a name="see-also"></a>参照  
 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)  
  
  


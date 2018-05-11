---
title: サービス配置スクリプトの解析を理解する |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: multidimensional-models
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 6be56539605946468b1c2e2700e2c65841018a4d
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="understanding-the-analysis-services-deployment-script"></a>Analysis Services 配置スクリプトについて
[!INCLUDE[ssas-appliesto-sqlas-all-aas](../../includes/ssas-appliesto-sqlas-all-aas.md)]

  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって生成される XMLA 配置スクリプトは、次の 2 つのセクションで構成されています。  
  
-   配置スクリプトの最初の部分には、配置先のデータベースで適切な [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] オブジェクトを作成、変更、または削除するために必要なコマンドが含まれています。 既定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで生成される入力ファイルは、増分配置に基づいています。 そのため、XMLA 配置スクリプトは、変更または削除されたオブジェクトにしか影響しません。  
  
-   配置スクリプトの 2 番目の部分には、配置先サーバー上で作成または変更されたオブジェクトのみを処理するために必要なコマンド (既定の処理のオプション)、または配置先データベースを完全に処理するために必要なコマンドが含まれています。 また、配置スクリプトに処理コマンドを含めないこともできます。  
  
 配置スクリプト全体は、単一のトランザクションまたは複数のトランザクションで実行できます。 スクリプトを複数のトランザクションで実行する場合は、スクリプトの最初の部分が単一のトランザクションとして実行され、各オブジェクトはそれぞれのトランザクションで処理されます。  
  
> [!IMPORTANT]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードでは、単一の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースへのオブジェクトの配置のみを行います。 サーバー レベルのオブジェクトまたはデータは配置しません。  
  
## <a name="see-also"></a>参照  
 [Analysis Services 配置ウィザードを実行しています。](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [配置スクリプトを作成するために使用する入力ファイルをについてください。](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)  
  
  

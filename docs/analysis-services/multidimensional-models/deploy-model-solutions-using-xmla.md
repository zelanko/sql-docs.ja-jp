---
title: "XMLA を使用したモデル ソリューションの配置 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML scripts [Analysis Services]
- scripts [Analysis Services], deployment
- deploying [Analysis Services], XML scripts
- Analysis Services deployments, XML scripts
ms.assetid: a8cb1837-fcac-4730-bea4-a72cf94d9f7c
caps.latest.revision: "33"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 97d6dca54da10d9f917b70cfb78ebf1b070a6bc0
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/08/2017
---
# <a name="deploy-model-solutions-using-xmla"></a>XMLA を使用したモデル ソリューションの配置
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]、**を作成する**のオプション、**データベースをスクリプト**コマンド全体の XML スクリプトを作成する[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]データベースまたはのいずれかの構成するオブジェクト。 作成したスクリプトは、別のコンピューターで実行し、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースのスキーマ (メタデータ) を再作成できます。 このスクリプトによって、データベース全体が生成されます。スクリプトを使用するときに、既に配置済みのオブジェクトを増分更新するメカニズムはありません。 スクリプトを実行してデータベースを配置したら、新たに作成されたデータベースを処理して、ユーザーが参照できるようにする必要があります。  
  
 **[データベースをスクリプト化]** コマンドの詳細については、「 [Analysis Services データベースのドキュメントとスクリプトの作成](../../analysis-services/multidimensional-models/document-and-script-an-analysis-services-database.md)」を参照してください。  
  
## <a name="modifying-object-properties-in-the-xml-script"></a>XML スクリプトのオブジェクト プロパティの変更  
 **[データベースをスクリプト化]** コマンドを使用するとき、データベース オブジェクトの特定のプロパティ (データベース名、データ ソース接続文字列、セキュリティ設定など) を変更することはできません。 これらのプロパティは、スクリプトの生成後にスクリプト内で手動で変更するか、スクリプトの実行後に配置済みのデータベースで変更する必要があります。  
  
> [!IMPORTANT]  
>  XML スクリプトには、データ ソースへの接続文字列内または権限借用の目的で指定されたパスワードは含まれません。 このシナリオの処理ではパスワードが必要であるため、実行前に XML スクリプトに手動でパスワードを追加するか、XML スクリプト実行後にパスワードを追加する必要があります。  
  
## <a name="see-also"></a>参照  
 [Deploy Model Solutions Using the Deployment Wizard](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)   
 [Analysis Services データベースの同期](../../analysis-services/multidimensional-models/synchronize-analysis-services-databases.md)  
  
  

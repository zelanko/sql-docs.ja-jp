---
title: "パーティションおよびロールの配置オプションを指定する |Microsoft ドキュメント"
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
- input files [Analysis Services]
- partitions [Analysis Services], deployment options
- Analysis Services deployments, roles
- Analysis Services deployments, partitions
- Analysis Services Deployment Wizard, roles
- Analysis Services Deployment Wizard, partitions
- deploying [Analysis Services], roles
- roles [Analysis Services], deployment options
- deploying [Analysis Services], partitions
- modifying role deployments
- modifying partition deployments
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
caps.latest.revision: 37
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: d6595d80eeba45415ac501182c31025478899711
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deployment-script-files---partition-and-role-deployment-options"></a>配置スクリプト ファイルのパーティションおよびロールの配置オプション
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードからのパーティションおよびロールの配置オプションを読み取り、 \<*プロジェクト名*> >.deploymentoptions ファイル。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]使用して、パーティションおよびロール プロジェクトの配置オプション、現在のときに、 \<*プロジェクト名*> >.deploymentoptions ファイルを作成します。 構成設定の詳細については、「 [配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/deployment-script-files-input-used-to-create-deployment-script.md)」を参照してください。  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>パーティションおよびロールの配置オプションの確認  
 配置オプション、 \<*プロジェクト名*> >.deploymentoptions ファイルの次のとおりです。  
  
 **パーティション配置オプション**  
 \<*プロジェクト名*> >.deploymentoptions ファイルは、コピー先データベースに既存のパーティションを保持するかどうか、または上書きする (既定) を指定します。 既存のパーティションを保持する場合、新しいパーティションのみが配置され、既存のすべてのメジャー グループのパーティションおよび集計デザインはそのまま残されます。  
  
> [!NOTE]  
>  パーティションが含まれているメジャー グループを削除すると、パーティションも自動的に削除されます。  
  
 **ロール配置オプション**  
 \<*プロジェクト名*> >.deploymentoptions ファイルでは、次のロール配置オプションのいずれかを指定します。  
  
-   配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールおよびロール メンバーのみが配置されます。  
  
-   配置先データベースの既存のすべてのロールおよびメンバーは、配置するロールおよびメンバーに置き換えられます。  
  
-   配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールは配置されません。  
  
-   **注** 既存のロールおよびメンバーが保持される場合、これらのロールに関連付けられた権限はリセットされてなくなります。 セキュリティ権限は、オブジェクトが関連付けられているセキュリティ ロールではなく、オブジェクト自体に含まれています。 Analysis Services 配置ウィザードを使用してこの動作を操作する方法については、Microsoft サポート技術情報の「ロールとメンバーの保持」を参照してください。  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>パーティションおよびロールの配置オプションの変更  
 展開する必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトに保存されているものの別のパーティションおよびロール オプションを使用して、 \<*プロジェクト名*> >.deploymentoptions ファイル。 たとえば、既存のパーティション、ロール、およびで指定されているすべての既存のパーティション、ロール、およびメンバーを置換ではなく、ロールのメンバーを保持することがあります、 \<*プロジェクト名*> >.deploymentoptions ファイル。  
  
 パーティションおよびロールの配置を変更する、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト、ため、プロジェクト内のパーティションおよびロールの設定を変更することはできません、 *\<プロジェクト名 >* **プロパティ ページ**  ダイアログ ボックスで[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]これらのオプションは表示されません。 ロールおよびパーティションの配置オプションを変更する場合は、内でこの情報を変更する必要があります、 \<*プロジェクト名*> >.deploymentoptions ファイル自体です。 次の手順を内のパーティションおよびロールの配置オプションを変更する方法を説明する、 \<*プロジェクト名*> >.deploymentoptions ファイル。  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>入力ファイルの生成後にパーティションまたはロールの配置を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、 **[パーティションとロールのオプションの指定]** ページで、パーティションおよびロールの新しい配置オプションを指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 (応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。)  
  
     - または -  
  
-   開く、 \<*プロジェクト名*> >.deploymentoptions 任意のテキスト エディターを手動でオプションを変更します。  
  
## <a name="see-also"></a>参照  
 [インストール先の指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [ソリューションの配置の構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)   
 [処理オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  


---
title: パーティションおよびロールの配置オプションの指定 |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
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
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: b9b36013f13360a2afcf9546cd1e286b35ae4acd
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "66075352"
---
# <a name="specifying-partition-and-role-deployment-options"></a>パーティションおよびロールの配置オプションの指定
  配置[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]ウィザードでは、パーティションおよびロールの配置オプションを\<*プロジェクト名*> deploymentoptions ファイルから読み取ります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]は、プロジェクトのビルド時に[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]このファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]では、 \<*プロジェクト名*> deploymentoptions ファイルが作成されるときに、現在のプロジェクトのパーティションおよびロールの配置オプションを使用します。 構成設定の詳細については、「 [配置スクリプトを作成するための入力ファイルについて](deployment-script-files-input-used-to-create-deployment-script.md)」を参照してください。  
  
## <a name="reviewing-the-partition-and-role-deployment-options"></a>パーティションおよびロールの配置オプションの確認  
 \<*プロジェクト名*> deploymentoptions ファイルの配置オプションには、次のものが含まれます。  
  
 **パーティション配置オプション**  
 \<*プロジェクト名*> deploymentoptions ファイルは、転送先データベースの既存のパーティションを保持するか上書きするか (既定値) を指定します。 既存のパーティションを保持する場合、新しいパーティションのみが配置され、既存のすべてのメジャー グループのパーティションおよび集計デザインはそのまま残されます。  
  
> [!NOTE]  
>  パーティションが含まれているメジャー グループを削除すると、パーティションも自動的に削除されます。  
  
 **ロール配置オプション**  
 \<*プロジェクト名*> deploymentoptions ファイルは、次のいずれかのロール配置オプションを指定します。  
  
-   配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールおよびロール メンバーのみが配置されます。  
  
-   配置先データベースの既存のすべてのロールおよびメンバーは、配置するロールおよびメンバーに置き換えられます。  
  
-   配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールは配置されません。  
  
-   **注** 既存のロールおよびメンバーが保持される場合、これらのロールに関連付けられた権限はリセットされてなくなります。 セキュリティ権限は、オブジェクトが関連付けられているセキュリティ ロールではなく、オブジェクト自体に含まれています。 Analysis Service 配置ウィザードを使用してこの動作を操作する方法の詳細については、Microsoft サポート技術情報の「ロールとメンバーの保持」を参照してください。  
  
## <a name="modifying-the-partition-and-role-deployment-options"></a>パーティションおよびロールの配置オプションの変更  
 プロジェクト\<*名*> deploymentoptions ファイルに[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]格納されているものとは異なるパーティションおよびロールオプションを使用して、プロジェクトを配置することが必要になる場合があります。 たとえば、 \<*プロジェクト名*> deploymentoptions ファイルに示されている既存のすべてのパーティション、ロール、およびメンバーを置き換えるのではなく、既存のパーティション、ロール、およびロールメンバーを保持することができます。  
  
 プロジェクト内[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のパーティションおよびロールの配置を変更するには、プロジェクト内のパーティションおよびロールの設定を変更できません。の [ [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] * \<プロジェクト名>* **プロパティページ**] ダイアログボックスにはこれらのオプションが表示されないためです。 ロールおよびパーティションの配置オプションを変更する場合は、 \<*プロジェクト名*> deploymentoptions ファイル内でこの情報を変更する必要があります。 次の手順では、 \<*プロジェクト名*> deploymentoptions ファイル内のパーティションおよびロールの配置オプションを変更する方法について説明します。  
  
#### <a name="to-change-the-deployment-of-partitions-or-roles-after-the-input-files-have-been-generated"></a>入力ファイルの生成後にパーティションまたはロールの配置を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、 **[パーティションとロールのオプションの指定]** ページで、パーティションおよびロールの新しい配置オプションを指定します。  
  
     \- または -  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 (応答ファイルモードの詳細については、「 [Analysis Services 配置ウィザードの実行](running-the-analysis-services-deployment-wizard.md)」を参照してください)。  
  
     \- または -  
  
-   \<任意のテキストエディターで*プロジェクト名*> deploymentoptions を開き、オプションを手動で変更します。  
  
## <a name="see-also"></a>参照  
 [インストール先の指定](deployment-script-files-specifying-the-installation-target.md)   
 [ソリューション配置の構成設定の指定](deployment-script-files-solution-deployment-config-settings.md)   
 [処理オプションの指定](deployment-script-files-specifying-processing-options.md)  
  
  

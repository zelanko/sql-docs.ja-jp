---
title: "処理オプションを指定する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Analysis Services deployments, processing options
- input files [Analysis Services]
- deploying [Analysis Services], processing options
- modifying processing options
- Analysis Services Deployment Wizard, processing options
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 32
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 2a3b80d70cce0e2efeae9c9a239d9e6fc4b8ffcd
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="deployment-script-files---specifying-processing-options"></a>配置スクリプト ファイルの処理オプションの指定
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードからの処理オプションを読み取り、 \<*プロジェクト名*> >.deploymentoptions ファイル。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]指定された処理オプションを使用して、**展開**のページ*\<プロジェクト名 >* **プロパティ ページ**を作成するダイアログボックス\<*プロジェクト名*> >.deploymentoptions ファイル。  
  
## <a name="reviewing-the-processing-options-for-deployment"></a>配置に関する処理オプションの確認  
 内で格納されている構成設定、 \<*プロジェクト名*> >.deploymentoptions ファイルを次に示します。  
  
-   **処理方法** この設定では、配置するオブジェクトを配置後に処理するかどうかと、実行する処理の種類を制御します。 処理オプションには次の 3 つがあります。  
  
    -   既定の処理 (既定)  
  
    -   完全処理  
  
    -   なし  
  
-   **書き戻しテーブル オプション** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで書き戻しが有効になっている場合、この設定では書き戻しの処理方法を定義します。 書き戻しテーブル オプションには次の 3 つがあります。  
  
    -   既定では、書き戻しテーブルが存在する場合、そのテーブルが使用されます。 書き戻しテーブルが存在しない場合は、新しい書き戻しテーブルが作成されます。  
  
    -   書き戻しテーブルが既に存在する場合、配置は失敗します。 書き戻しテーブルが存在しない場合は、新しい書き戻しテーブルが作成されます。  
  
    -   書き戻しテーブルが既に存在するかどうかにかかわらず、新しい書き戻しテーブルが作成されます。 この場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって既存のテーブルが削除され、新しい書き戻しテーブルに置き換えられます。  
  
-   **トランザクション配置** この設定では、メタデータ変更および処理コマンドの配置を 1 つのトランザクションで行うか、別々のトランザクションで行うかを制御します。  
  
    -   このオプションが **True** (既定) の場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではすべてのメタデータ変更およびすべての処理コマンドが 1 つのトランザクションで配置されます。  
  
    -   このオプションが **False**の場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではメタデータ変更が 1 つのトランザクションで配置され、各処理コマンドがそれぞれ別個のトランザクションで配置されます。  
  
## <a name="modifying-the-processing-options-for-deployment"></a>配置に関する処理オプションの変更  
 ただしを展開する必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトに保存されているものの別の処理オプションを使用して、 \<*プロジェクト名*> >.deploymentoptions ファイル。 たとえば、すべてのオブジェクトを完全に処理するか、既定の処理オプションを使用して処理するか、まったく処理しないようにする必要が生じることがあります。 キューブまたはディメンションが書き込み可能である場合は、新しい書き戻しテーブルまたは既存の書き戻しテーブルのどちらを使用するかを指定できます。  
  
 配置時に使用する処理オプションを変更するには、プロジェクトを編集して再作成するか、次の手順のいずれかの方法に従って入力ファイル内の処理オプションを変更できます。  
  
#### <a name="to-change-processing-options-after-the-input-files-have-been-generated"></a>入力ファイルの生成後に処理オプションを変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行します。 **[処理オプション]** ページで、配置するプロジェクトの処理オプションを指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     - または -  
  
-   変更、 \<*プロジェクト名*> 任意のテキスト エディターを使用して、>.deploymentoptions ファイル。  
  
## <a name="see-also"></a>参照  
 [インストール先の指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/deployment-script-files-solution-deployment-config-settings.md)  
  
  


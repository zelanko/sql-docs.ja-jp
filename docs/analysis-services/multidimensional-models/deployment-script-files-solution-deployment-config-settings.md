---
title: "ソリューションの配置の構成設定を指定する |Microsoft ドキュメント"
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
helpviewer_keywords:
- Analysis Services Deployment Wizard, configuration settings
- input files [Analysis Services]
- configuration options [Analysis Services]
- Analysis Services deployments, configuration settings
- deploying [Analysis Services], configuration settings
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
caps.latest.revision: "34"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: e778ee4c1962ac51eb145174dd424b9c3868512d
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="deployment-script-files---solution-deployment-config-settings"></a>配置スクリプト ファイル、ソリューションの展開の構成設定
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]配置ウィザードでは読み取りますパーティションおよびロールから、配置スクリプトで使用する展開オプションを\<*プロジェクト名*> >.configsettings ファイル。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]現在のプロジェクトの構成設定を使用して、作成、 \<*プロジェクト名*> >.configsettings ファイル。  
  
## <a name="reviewing-the-configuration-settings-for-deployment"></a>配置に関する構成設定の確認  
 格納されている構成設定は、次のとおり、 \<*プロジェクト名*> >.configsettings ファイル。  
  
-   **データ ソース接続文字列** これは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで指定されている値に基づいた各データ ソースの接続文字列です。 このファイルに接続文字列が保存される際には、常にユーザー ID とパスワードが削除されます。 ただし、配置ウィザードで Analysis Services インスタンスに直接配置を行う場合は、ウィザードで適切なユーザー ID とパスワードを入力して、配置するデータベースを正常に処理することができます。 配置ウィザードで配置スクリプトを保存する場合、この接続情報は配置スクリプト内に保存されません。  
  
-   **権限借用アカウント** この設定では、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が各データ ソースでステートメントを実行するために使用するユーザー名を指定します。 権限借用アカウントが指定されていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のログオン アカウントを使用してステートメントが実行されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログオン アカウントがデータ ソース内で権限を直接与えられている場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのすべてのデータベース内のデータベース管理者は、だれでもそのログオン アカウントを使用してデータ ソースにアクセスできます。 ユーザー アカウントとパスワードが指定された場合、このファイルに権限借用情報が保存される前に常にこの情報は削除されます。 ただし、配置ウィザードで Analysis Services インスタンスに直接配置を行う場合は、ウィザードで適切なユーザー ID とパスワードを入力して、配置するデータベースを正常に処理することができます。 配置ウィザードで配置スクリプトを保存する場合、この権限借用情報は配置スクリプト内に保存されません。  
  
-   **キーのエラー ログ ファイル** この設定では、データベース内の各キューブ、メジャー グループ、パーティション、およびディメンションのキー エラー ログ ファイルのファイル名とパスを指定します。  
  
-   **ストレージの場所** この設定では、データベース内の各キューブ、メジャー グループ、およびパーティションのストレージの場所を指定します。 オブジェクトの値が指定されていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードではオブジェクトの既定の場所が使用されます。 たとえば、パーティションにはメジャー グループの場所が使用され、メジャー グループにはキューブの場所が使用され、キューブには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのオブジェクトの既定の場所が使用されます。 ストレージの場所には、ローカルまたは汎用名前付け規則 (UNC) のどちらかのパスを指定できます。  
  
-   **レポート サーバー** この設定では、データベース内の各キューブで定義されている各レポート アクションのレポート サーバーとフォルダーの場所を指定します。  
  
## <a name="modifying-the-configuration-settings-for-deployment"></a>配置に関する構成設定の変更  
 場合によっては、展開する必要があります、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクトに格納されているものと異なる構成設定を使用して、 \<*プロジェクト名*> >.configsettings ファイル。 たとえば、1 つまたは複数のデータ ソースへの接続文字列を変更するか、特定のパーティションまたはメジャー グループのストレージの場所を指定する必要が生じることがあります。  
  
 パーティションおよびロールの配置を変更する、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト内でこの情報を変更する必要があります、 \<*プロジェクト名*> >.configsettings ファイル、以下の手順で説明します。 プロジェクト内のパーティションおよびロールの設定を変更することはできません、 *\<プロジェクト名 >* **プロパティ ページ** ダイアログ ボックスで[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)]これらのオプションは表示されません。  
  
> [!NOTE]  
>  構成設定は、すべてのオブジェクトに適用することも、新たに作成したオブジェクトのみに適用することもできます。 以前に配置した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに追加のオブジェクトを配置し、既存のオブジェクトを上書きしないようにする場合は、新たに作成したオブジェクトのみに構成設定を適用します。 構成設定がすべてのオブジェクトに適用またはのみ新たに作成した、このオプションで設定するかどうかを指定する、 \<*プロジェクト名*> >.deploymentoptions ファイル。 詳細については、「 [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)」を参照してください。  
  
#### <a name="to-change-configuration-settings-after-the-input-files-have-been-generated"></a>入力ファイルの生成後に構成設定を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、 **[構成設定]** ページで配置するオブジェクトの構成設定を指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     — または —  
  
-   変更、 \<*プロジェクト名*> 任意のテキスト エディターを使用して、>.configsettings ファイル。  
  
## <a name="see-also"></a>参照  
 [インストール先の指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-the-installation-target.md)   
 [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-partition-and-role-deployment-options.md)   
 [処理オプションの指定](../../analysis-services/multidimensional-models/deployment-script-files-specifying-processing-options.md)  
  
  

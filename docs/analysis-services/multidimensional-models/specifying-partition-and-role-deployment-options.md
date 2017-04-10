---
title: "パーティションおよびロールの配置オプションの指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "入力ファイル [Analysis Services]"
  - "パーティション [Analysis Services], 配置オプション"
  - "Analysis Services の配置, ロール"
  - "Analysis Services の配置, パーティション"
  - "Analysis Services 配置ウィザード, ロール"
  - "Analysis Services 配置ウィザード, パーティション"
  - "配置 [Analysis Services], ロール"
  - "ロール [Analysis Services], 配置オプション"
  - "配置 [Analysis Services], パーティション"
  - "ロール配置の変更"
  - "パーティション配置の変更"
ms.assetid: e9b9ca57-a5cc-4fc0-87b5-305257038d56
caps.latest.revision: 37
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# パーティションおよびロールの配置オプションの指定
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードでは、パーティションおよびロールの配置オプションを \<*project name*>.deploymentoptions ファイルから読み取ります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、\<*project name*>.deploymentoptions ファイルの作成時に、現在のプロジェクトのパーティションおよびロールの配置オプションを使用します。 構成設定の詳細については、「[配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md)」を参照してください。  
  
## パーティションおよびロールの配置オプションの確認  
 \<*project name*>.deploymentoptions ファイルには、次の配置オプションが含まれています。  
  
 **パーティション配置オプション**  
 \<*project name*>.deploymentoptions ファイルでは、配置先のデータベースにある既存のパーティションを保持するか、上書きする (既定) かを指定します。 既存のパーティションを保持する場合、新しいパーティションのみが配置され、既存のすべてのメジャー グループのパーティションおよび集計デザインはそのまま残されます。  
  
> [!NOTE]  
>  パーティションが含まれているメジャー グループを削除すると、パーティションも自動的に削除されます。  
  
 **ロール配置オプション**  
 \<*project name*>.deploymentoptions ファイルでは、次のいずれかのロール配置オプションを指定します。  
  
-   配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールおよびロール メンバーのみが配置されます。  
  
-   配置先データベースの既存のすべてのロールおよびメンバーは、配置するロールおよびメンバーに置き換えられます。  
  
-   配置先データベースの既存のロールおよびロール メンバーは保持され、新しいロールは配置されません。  
  
-   **注** 既存のロールおよびメンバーが保持される場合、これらのロールに関連付けられた権限はリセットされてなくなります。 セキュリティ権限は、オブジェクトが関連付けられているセキュリティ ロールではなく、オブジェクト自体に含まれています。 Analysis Services 配置ウィザードを使用してこの動作を操作する方法については、Microsoft サポート技術情報の「ロールとメンバーの保持」を参照してください。  
  
## パーティションおよびロールの配置オプションの変更  
 \<*project name*>.deploymentoptions ファイルに保存されているものとは別のパーティションおよびロールのオプションを使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置する必要が生じることがあります。 たとえば、\<*project name*>.deploymentoptions ファイルの指定に従って既存のすべてのパーティション、ロール、およびメンバーを置換するのではなく、既存のパーティション、ロール、およびロール メンバーを保持する必要が生じることがあります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのパーティションおよびロールの配置を変更する場合、プロジェクト内のパーティションおよびロールの設定は変更できません。これは、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の *[\<project name>* **プロパティ ページ]** ダイアログ ボックスにこれらのオプションが表示されないためです。 ロールおよびパーティションの配置オプションを変更するには、\<*project name*>.deploymentoptions ファイル内にあるこの情報を変更する必要があります。 次の手順では、\<*project name*>.deploymentoptions ファイル内のパーティションおよびロールの配置オプションを変更する方法について説明します。  
  
#### 入力ファイルの生成後にパーティションまたはロールの配置を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、**[パーティションとロールのオプションの指定]** ページで、パーティションおよびロールの新しい配置オプションを指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 (応答ファイル モードの詳細については、「[Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。)  
  
     — または —  
  
-   テキスト エディターで \<*project name*>.deploymentoptions を開き、オプションを手動で変更します。  
  
## 参照  
 [インストール先の指定](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [処理オプションの指定](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  
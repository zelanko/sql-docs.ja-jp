---
title: "インストール先の指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
  - "setup-install"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "入力ファイル [Analysis Services]"
  - "インストール先 [Analysis Services]"
  - "Analysis Services の配置, インストール先"
  - "Analysis Services 配置ウィザード, インストール先"
  - "配置 [Analysis Services], インストール先"
  - "インストール先の変更"
ms.assetid: cb706817-6f63-4771-92c3-b70030bbce3d
caps.latest.revision: 35
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# インストール先の指定
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードでは、インストール先の情報を \<*プロジェクト名*>.deploymenttargets ファイルから読み取ります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、[*\<プロジェクト名>* ** プロパティ ページ]** ダイアログ ボックスの **[配置]** ページで指定されたデータベースとサーバーを使用して、\<*プロジェクト名*>.targets ファイルを作成します。  
  
## 配置に関するインストール先の変更  
 場合によっては、**[配置]** ページで指定されたものとは別のデータベースまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置する必要が生じることがあります。 たとえば、配置前のテストを行うためにプロジェクトをサーバーに配置し、テストの完了後にそのプロジェクトを実稼働サーバーに配置する必要が生じることがあります。 また、完成したテスト済みのプロジェクトをネットワーク負荷分散クラスター内の複数の実稼働サーバーに配置するか、ステージング サーバーおよび実稼働サーバーに配置する必要が生じることもあります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを別のデータベースまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスに配置するには、次の手順で説明するいずれかの方法に従って、入力ファイル内のインストール先を変更します。  
  
#### 入力ファイルの生成後にインストール先を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行します。 **[インストールの対象]** ページで、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスとデータベースの新しいインストール先を指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「[Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     — または —  
  
-   テキスト エディターを使用して、\<*プロジェクト名*>.deploymenttargets ファイルを変更します。  
  
## 参照  
 [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)   
 [処理オプションの指定](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  
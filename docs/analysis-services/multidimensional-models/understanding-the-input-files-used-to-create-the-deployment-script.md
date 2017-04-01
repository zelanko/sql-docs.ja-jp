---
title: "配置スクリプトを作成するための入力ファイルについて | Microsoft Docs"
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
  - "Analysis Services 配置ウィザード, スクリプト"
  - "配置 [Analysis Services], 入力ファイル"
  - "Analysis Services 配置ウィザード, 入力ファイル"
  - "スクリプト [Analysis Services], 配置"
  - "Analysis Services の配置, 入力ファイル"
  - "入力ファイルの変更"
ms.assetid: 20e080cd-6a0e-4591-b022-ea4cd3638e36
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 配置スクリプトを作成するための入力ファイルについて
  [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを作成すると、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] によってそのプロジェクトの XML ファイルが生成されます。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、これらの XML ファイルは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの出力フォルダーに保存されます。 既定では、出力は \\Bin フォルダーに対して行われます。 次の表は、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で作成される XML ファイルを示しています。  
  
|XMLA ファイル|Description|  
|---------------|-----------------|  
|\<*プロジェクト名*\>.asdatabase|プロジェクト内のすべての [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの宣言定義が含まれています。|  
|\<*プロジェクト名*\>.deploymenttargets|[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが作成される [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスおよびデータベースの名前が含まれています。|  
|\<*プロジェクト名*\>.configsettings|データ ソース接続情報やオブジェクト格納場所など、環境に固有の設定が含まれています。 このファイルの設定によって、\<*project name*\>.asdatabase ファイルの設定が上書きされます。|  
|\<*プロジェクト名*\>.deploymentoptions|配置がトランザクションであるかどうかや、配置したオブジェクトを配置後に処理するかどうかなどの配置オプションが含まれています。|  
  
> [!NOTE]  
>  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、プロジェクト ファイルにパスワードは保存されません。  
  
## 入力ファイルの変更  
 入力ファイル内の値または入力ファイルから取得した値を変更すると、\<*project name*\>.asdatabase ファイル全体\( (または、既存の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース\)からスクリプトを生成する場合は XMLA スクリプト全体) を編集しなくても、配置先、構成設定、および配置オプションを変更することができます。 個々のファイルを変更できると、さまざまな目的に合わせてさまざまな配置スクリプトを簡単に作成できます。  
  
 次のトピックでは、さまざまな入力ファイル内の値を変更する方法について説明します。  
  
-   [インストール先の指定](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)  
  
-   [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)  
  
-   [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
-   [処理オプションの指定](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
## 参照  
 [Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)   
 [Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)  
  
  
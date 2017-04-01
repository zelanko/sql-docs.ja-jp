---
title: "Analysis Services 配置ウィザードの実行 | Microsoft Docs"
ms.custom: 
  - "SQL2016_New_Updated"
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
  - "Analysis Services 配置ウィザード, 実行"
ms.assetid: 3a38d489-4625-4878-bd18-c6f903be33df
caps.latest.revision: 41
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 38
---
# Analysis Services 配置ウィザードの実行
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを使用して [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置するときは、ウィザードを次の方法で実行できます。  
  
-   **対話的に実行** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話的に実行すると、ユーザーの入力によって対話的に変更された入力ファイルに基づいて、XML 配置スクリプトが生成されます。 ユーザーによる変更は、配置スクリプトのみに適用されます。 入力ファイルが変更されることはありません。 入力ファイルの詳細については、「[配置スクリプトを作成するための入力ファイルについて](../../analysis-services/multidimensional-models/understanding-the-input-files-used-to-create-the-deployment-script.md)」を参照してください。  
  
-   **コマンド プロンプトから実行** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトから実行すると、ウィザードの実行に使用したスイッチに基づいて、XML for Analysis \(XMLA\) 配置スクリプトが生成されます。 ウィザードでは、ユーザーの入力を求めてその入力に基づいて入力ファイルを変更するか、入力ファイルをそのまま使用して自動的に配置を実行するか、後で使用可能な配置スクリプトを作成します。  
  
## Analysis Services 配置ウィザードの対話的な実行  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話的に実行すると、入力ファイルから値が読み取られ、その情報が提示されます。 配置先、構成設定、配置オプション、接続文字列パスワードなどの入力値は、変更することも、そのまま使用することもできます。 入力値を変更した場合、ウィザードではこれらの変更値を使用して XMLA 配置スクリプトを生成します。 ただし、入力ファイルの値は変更されません。  
  
> [!NOTE]  
>  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードで入力値が変更されるようにするには、コマンド プロンプトでウィザードを応答ファイル モードで実行します。  
  
 入力値を確認し、必要な変更を行うと、ウィザードによって XMLA 配置スクリプトが生成されます。 この配置スクリプトは配置先サーバーで直ちに実行することも、後で使用するために保存することもできます。  
  
#### Analysis Services 配置ウィザードを対話的に実行するには  
  
-   **[スタート]** ボタンをクリックし、**[すべてのプログラム]**、**[Microsoft SQL Server]**、**[Analysis Services]** の順にポイントして、**[配置ウィザード]** をクリックします。  
  
     - または -  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの **[プロジェクト]** フォルダーで、*\<project name\>*.asdatabase ファイルをダブルクリックします。  
  
    > [!NOTE]  
    >  *\<project name\>*.asdatabase ファイルが見つからない場合は、「\*.asdatabase」を指定して検索してみてください。  
  
## コマンド プロンプトでの Analysis Services 配置ウィザードの実行  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードは、コマンド プロンプトで実行することもできます。 コマンド プロンプトを使用する場合は、.asdatabase ファイルへの完全パスを指定し、次のいずれかのモードでウィザードを実行します。  
  
 **応答ファイル モード**  
 応答ファイル モードでは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトが [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でビルドされたときに生成された入力ファイルを対話的に変更できます。 これらの変更された入力ファイルは XMLA 配置スクリプトの生成前に保存されます。 変更された入力ファイルは、次にウィザードを実行したときの開始点として使用されます。  
  
 ウィザードを応答ファイル モードで実行するには、**\/a** スイッチを使用します。  
  
 **サイレント モード**  
 サイレント モードでは、ウィザードは入力ファイルに含まれている情報に基づいて、自動的に配置を実行します。  
  
 ウィザードをサイレント モードで実行するには、**\/s** スイッチを使用します。 サイレント モードでウィザードを実行した場合、メッセージはコンソールに出力されます。ログ ファイルを指定した場合はログ ファイルに出力されます。  
  
 **出力モード**  
 出力モードでは、ウィザードは入力ファイルに基づいて、後で実行するための XMLA 配置スクリプトを生成します。  
  
 ウィザードを出力モードで実行するには、**\/o** スイッチを使用して出力ファイル名を指定します。  
  
 これらのコマンド ライン スイッチの詳細については、「[配置ユーティリティを使用したモデル ソリューションの配置](../../analysis-services/multidimensional-models/deploy-model-solutions-with-the-deployment-utility.md)」を参照してください。  
  
 次の手順では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行する方法について説明します。  
  
#### Analysis Services 配置ウィザードをコマンド プロンプトで実行するには  
  
1.  コマンド プロンプトを開き、C:\\Program Files \(x86\)\\Microsoft SQL Server\\120\\Tools\\Binn\\ManagementStudio フォルダーに移動します。  
  
2.  「**Microsoft.AnalysisServices.Deployment.exe**」の後に、ウィザードを実行するモードに対応するスイッチを入力します。  
  
## 参照  
 [Analysis Services 配置スクリプトについて](../../analysis-services/multidimensional-models/understanding-the-analysis-services-deployment-script.md)   
 [Deploy Model Solutions Using the Deployment Wizard](../../analysis-services/multidimensional-models/deploy-model-solutions-using-the-deployment-wizard.md)  
  
  
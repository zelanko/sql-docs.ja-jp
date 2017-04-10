---
title: "SQL Server Data Tools でのパッケージの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "08/25/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Integration Services パッケージ, 実行"
  - "SSIS パッケージ, 実行"
  - "パッケージ [Integration Services]、実行"
  - "SQL Server Integration Services パッケージ, 実行"
ms.assetid: 318e6beb-5540-4101-82a5-18c9d47f0570
caps.latest.revision: 58
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 58
---
# SQL Server Data Tools でのパッケージの実行
  一般に、パッケージの開発、デバッグ、およびテストの段階では、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] でパッケージを実行します。 [!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーからパッケージを実行すると、パッケージは常に即座に実行されます。  
  
 パッケージの実行中は、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーの **[進行状況]** タブにパッケージの実行の進行状況が表示されます。 パッケージおよびそのタスクおよびコンテナーの開始時間と終了時間に加え、パッケージ内で失敗したタスクまたはコンテナーに関する情報が表示されます。 パッケージの実行が完了した後は、**[実行結果]** タブで実行時情報を確認できます。 詳細については、[「制御フローのデバッグ」](../../integration-services/troubleshooting/debugging-control-flow.md) の「進行状況レポート」を参照してください。  
  
 **デザイン時配置**。 [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)] でパッケージを実行すると、そのパッケージが構築されフォルダーに配置されます。 パッケージを実行する前に、パッケージを配置するフォルダーを指定できます。 フォルダーを指定しない場合、既定で **bin** フォルダーが使用されます。 こうした配置方法は、デザイン時配置と呼ばれます。  
  
### SQL Server Data Tools でパッケージを実行するには  
  
1.  ソリューションに複数のプロジェクトが含まれている場合は、ソリューション エクスプローラーで、パッケージを含む [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクトを右クリックし、**[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ プロジェクトを設定します。  
  
2.  プロジェクトに複数のパッケージが含まれている場合は、ソリューション エクスプローラーで、パッケージの 1 つを右クリックし、**[スタートアップ オブジェクトに設定]** をクリックしてスタートアップ パッケージを設定します。  
  
3.  パッケージを実行するには、次のいずれかの手順を実行します。  
  
    -   実行するパッケージを開き、メニュー バーの **[デバッグ開始]** をクリックするか、F5 キーを押します。 パッケージの実行が完了したら、Shift キーを押しながら F5 キーを押して、デザイン モードに戻ります。  
  
    -   ソリューション エクスプローラーでパッケージを右クリックし、**[パッケージの実行]** をクリックします。  
  
### デザイン時配置用に別のフォルダーを指定するには  
  
1.  ソリューション エクスプローラーで、実行するパッケージが含まれる [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] プロジェクト フォルダーを右クリックし、**[プロパティ]** をクリックします。  
  
2.  [**\<プロジェクト名> プロパティ ページ**] ダイアログ ボックスで、**[ビルド]** をクリックします。  
  
3.  OutputPath プロパティの値を更新して、デザイン時配置用に使用するフォルダーを指定し、**[OK]** をクリックします。  
  
## 参照  
 [プロジェクトとパッケージの実行](https://msdn.microsoft.com/library/hh213290.aspx)   
 [Integration Services (SSIS) パッケージ](https://msdn.microsoft.com/library/ms141134.aspx)  
  
  
---
title: "処理オプションの指定 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Analysis Services の配置, 処理オプション"
  - "入力ファイル [Analysis Services]"
  - "配置 [Analysis Services], 処理オプション"
  - "処理オプションの変更"
  - "Analysis Services 配置ウィザード, 処理オプション"
ms.assetid: e9e50817-908e-4210-bc3d-8e2957568241
caps.latest.revision: 32
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# 処理オプションの指定
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードでは、処理オプションを \<*project name*>.deploymentoptions ファイルから読み取ります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、*\<project name>* の **[プロパティ ページ]** ダイアログ ボックスの **[配置]** ページで指定された処理オプションを使用して、\<*project name*>.deploymentoptions ファイルを作成します。  
  
## 配置に関する処理オプションの確認  
 \<*project name*>.deploymentoptions ファイルに保存されている構成設定は次のとおりです。  
  
-   **処理方法** この設定では、配置するオブジェクトを配置後に処理するかどうかと、実行する処理の種類を制御します。 処理オプションには次の 3 つがあります。  
  
    -   既定の処理 (既定)  
  
    -   完全処理  
  
    -   なし  
  
-   **書き戻しテーブル オプション** [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで書き戻しが有効になっている場合、この設定では書き戻しの処理方法を定義します。 書き戻しテーブル オプションには次の 3 つがあります。  
  
    -   既定では、書き戻しテーブルが存在する場合、そのテーブルが使用されます。 書き戻しテーブルが存在しない場合は、新しい書き戻しテーブルが作成されます。  
  
    -   書き戻しテーブルが既に存在する場合、配置は失敗します。 書き戻しテーブルが存在しない場合は、新しい書き戻しテーブルが作成されます。  
  
    -   書き戻しテーブルが既に存在するかどうかにかかわらず、新しい書き戻しテーブルが作成されます。 この場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードによって既存のテーブルが削除され、新しい書き戻しテーブルに置き換えられます。  
  
-   **トランザクション配置** この設定では、メタデータ変更および処理コマンドの配置を 1 つのトランザクションで行うか、別々のトランザクションで行うかを制御します。  
  
    -   このオプションが **True** (既定) の場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではすべてのメタデータ変更およびすべての処理コマンドが 1 つのトランザクションで配置されます。  
  
    -   このオプションが **False** の場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ではメタデータ変更が 1 つのトランザクションで配置され、各処理コマンドがそれぞれ別個のトランザクションで配置されます。  
  
## 配置に関する処理オプションの変更  
 \<*project name*>.deploymentoptions ファイルに保存されているものとは別の処理オプションを使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置する必要が生じる場合があります。 たとえば、すべてのオブジェクトを完全に処理するか、既定の処理オプションを使用して処理するか、まったく処理しないようにする必要が生じることがあります。 キューブまたはディメンションが書き込み可能である場合は、新しい書き戻しテーブルまたは既存の書き戻しテーブルのどちらを使用するかを指定できます。  
  
 配置時に使用する処理オプションを変更するには、プロジェクトを編集して再作成するか、次の手順のいずれかの方法に従って入力ファイル内の処理オプションを変更できます。  
  
#### 入力ファイルの生成後に処理オプションを変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行します。 **[処理オプション]** ページで、配置するプロジェクトの処理オプションを指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「[Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     — または —  
  
-   テキスト エディターを使用して、\<*project name*>.deploymentoptions ファイルを変更します。  
  
## 参照  
 [インストール先の指定](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [ソリューションの配置に関する構成設定の指定](../../analysis-services/multidimensional-models/specifying-configuration-settings-for-solution-deployment.md)  
  
  
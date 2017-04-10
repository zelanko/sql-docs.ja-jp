---
title: "ソリューションの配置に関する構成設定の指定 | Microsoft Docs"
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
  - "Analysis Services 配置ウィザード、構成設定"
  - "入力ファイル [Analysis Services]"
  - "構成オプション [Analysis Services]"
  - "Analysis Services 配置、構成設定"
  - "配置 [Analysis Services], 構成設定"
ms.assetid: 953814a3-85ef-40cc-b46a-d532aa7a6569
caps.latest.revision: 34
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
---
# ソリューションの配置に関する構成設定の指定
  [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードでは、配置スクリプトで使用するパーティションおよびロールの配置オプションを \<*プロジェクト名*>.configsettings ファイルから読み取ります。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] は、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトの作成時にこのファイルを作成します。 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] では、現在のプロジェクトの構成設定を使用して、\<*プロジェクト名*>.configsettings ファイルが作成されます。  
  
## 配置に関する構成設定の確認  
 \<*プロジェクト名*>.configsettings ファイルに保存されている構成設定は次のとおりです。  
  
-   **データ ソース接続文字列** これは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトで指定されている値に基づいた各データ ソースの接続文字列です。 このファイルに接続文字列が保存される際には、常にユーザー ID とパスワードが削除されます。 ただし、配置ウィザードで Analysis Services インスタンスに直接配置を行う場合は、ウィザードで適切なユーザー ID とパスワードを入力して、配置するデータベースを正常に処理することができます。 配置ウィザードで配置スクリプトを保存する場合、この接続情報は配置スクリプト内に保存されません。  
  
-   **権限借用アカウント** この設定では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] が各データ ソースでステートメントを実行するために使用するユーザー名を指定します。 権限借用アカウントが指定されていない場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のログオン アカウントを使用してステートメントが実行されます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ログオン アカウントがデータ ソース内で権限を直接与えられている場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのすべてのデータベース内のデータベース管理者は、だれでもそのログオン アカウントを使用してデータ ソースにアクセスできます。 ユーザー アカウントとパスワードが指定された場合、このファイルに権限借用情報が保存される前に常にこの情報は削除されます。 ただし、配置ウィザードで Analysis Services インスタンスに直接配置を行う場合は、ウィザードで適切なユーザー ID とパスワードを入力して、配置するデータベースを正常に処理することができます。 配置ウィザードで配置スクリプトを保存する場合、この権限借用情報は配置スクリプト内に保存されません。  
  
-   **キーのエラー ログ ファイル** この設定では、データベース内の各キューブ、メジャー グループ、パーティション、およびディメンションのキー エラー ログ ファイルのファイル名とパスを指定します。  
  
-   **ストレージの場所** この設定では、データベース内の各キューブ、メジャー グループ、およびパーティションのストレージの場所を指定します。 オブジェクトの値が指定されていない場合、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードではオブジェクトの既定の場所が使用されます。 たとえば、パーティションにはメジャー グループの場所が使用され、メジャー グループにはキューブの場所が使用され、キューブには [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスのオブジェクトの既定の場所が使用されます。 ストレージの場所には、ローカルまたは汎用名前付け規則 (UNC) のどちらかのパスを指定できます。  
  
-   **レポート サーバー** この設定では、データベース内の各キューブで定義されている各レポート アクションのレポート サーバーとフォルダーの場所を指定します。  
  
## 配置に関する構成設定の変更  
 場合によっては、\<*プロジェクト名*>.configsettings ファイルに保存されているものとは別の構成設定を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトを配置する必要が生じることがあります。 たとえば、1 つまたは複数のデータ ソースへの接続文字列を変更するか、特定のパーティションまたはメジャー グループのストレージの場所を指定する必要が生じることがあります。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトのパーティションおよびロールの配置を変更するには、下記の手順に従って、\<*プロジェクト名*>.configsettings ファイル内のこの情報を変更する必要があります。 プロジェクト内のパーティションおよびロールの設定は変更できません。[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] の [*\<プロジェクト名>\>* **プロパティ ページ**] ダイアログ ボックスにはこれらのオプションが表示されないためです。  
  
> [!NOTE]  
>  構成設定は、すべてのオブジェクトに適用することも、新たに作成したオブジェクトのみに適用することもできます。 以前に配置した [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースに追加のオブジェクトを配置し、既存のオブジェクトを上書きしないようにする場合は、新たに作成したオブジェクトのみに構成設定を適用します。 構成設定をすべてのオブジェクトに適用するか、新たに作成したオブジェクトのみに適用するかを指定するには、\<*プロジェクト名*>.deploymentoptions ファイル内のこのオプションを設定します。 詳細については、「[パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)」を参照してください。  
  
#### 入力ファイルの生成後に構成設定を変更するには  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードを対話形式で実行し、**[構成設定]** ページで配置するオブジェクトの構成設定を指定します。  
  
     — または —  
  
-   [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 配置ウィザードをコマンド プロンプトで実行し、ウィザードを応答ファイル モードで実行するように設定します。 応答ファイル モードの詳細については、「[Analysis Services 配置ウィザードの実行](../../analysis-services/multidimensional-models/running-the-analysis-services-deployment-wizard.md)」を参照してください。  
  
     — または —  
  
-   テキスト エディターを使用して、\<*プロジェクト名*>.configsettings ファイルを変更します。  
  
## 参照  
 [インストール先の指定](../../analysis-services/multidimensional-models/specifying-the-installation-target.md)   
 [パーティションおよびロールの配置オプションの指定](../../analysis-services/multidimensional-models/specifying-partition-and-role-deployment-options.md)   
 [処理オプションの指定](../../analysis-services/multidimensional-models/specifying-processing-options.md)  
  
  
---
title: "SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 56dc1bf8-99d4-41dc-bdc4-f64f1ccfd688
caps.latest.revision: 9
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 9
---
# SQL Server Management Studio を使用した SSIS サーバーでのパッケージの実行
  [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] サーバーにプロジェクトを配置した後は、サーバーでパッケージを実行できます。  
  
 操作レポートを使用して、サーバー上で実行されたパッケージまたは現在実行中のパッケージに関する情報を表示できます。 詳細については、「 [Reports for the Integration Services Server](../../integration-services/performance/reports-for-the-integration-services-server.md)」を参照してください。  
  
### SQL Server Management Studio を使用してサーバーでパッケージを実行するには  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] を開き、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] カタログが含まれている [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のインスタンスに接続します。  
  
2.  オブジェクト エクスプローラーで、**[Integration Services カタログ]** ノード、**[SSISDB]** ノードの順に展開し、配置したプロジェクトに含まれるパッケージに移動します。  
  
3.  パッケージ名を右クリックし、**[実行]** を選択します。  
  
4.  **[パッケージの実行]** ダイアログ ボックスの **[パラメーター]** タブ、**[接続マネージャー]** タブ、**[詳細設定]** タブの設定を使用して、パッケージの実行を構成します。  
  
5.  **[OK]** をクリックしてパッケージを実行します。  
  
     - または -  
  
     ストアド プロシージャを使用してパッケージを実行します。 **[スクリプト]** をクリックして、実行のインスタンスを作成し、実行のインスタンスを開始する Transact-SQL ステートメントを生成します。 ステートメントには catalog.create_execution、catalog.set_execution_parameter_value、および catalog.start_execution の各ストアド プロシージャの呼び出しが含まれています。 これらのストアド プロシージャの詳細については、「[catalog.create_execution (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-create-execution-ssisdb-database.md)」、「[catalog.set_execution_parameter_value (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)」、および「[catalog.start_execution (SSISDB データベース)](../../integration-services/system-stored-procedures/catalog-start-execution-ssisdb-database.md)」をご覧ください。  
  
  
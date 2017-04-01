---
title: "Integration Services (SSIS) Scale Out でパッケージを実行する | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4c2f4cd7-9c47-416d-bb1e-40acc3e05342
caps.latest.revision: 5
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 5
---
# Integration Services (SSIS) Scale Out でパッケージを実行する
Integration Services サーバーにパッケージが展開されたら、Scale Out でパッケージを実行できます。

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>**[Execute Package In Scale Out (Scale Out でパッケージを実行)]** ダイアログを使用してパッケージを実行する 

1. ### <a name="open-the-execute-package-in-scale-out-dialog-box"></a>[Execute Package In Scale Out (Scale Out でパッケージを実行)] ダイアログ ボックスを開く ###
    [!INCLUDE[ssManStudioFull_md](../includes/ssmanstudiofull-md.md)] で、Integration Services サーバーに接続します。 オブジェクト エクスプローラーで、ツリーを展開し、**[Integration Services カタログ]** のノードを表示します。 **SSISDB** ノード、プロジェクト、または実行するパッケージを右クリックし、**[Execute in Scale Out (Scale Out で実行)]** をクリックします。
2. ### <a name="select-packages-and-set-the-options"></a>パッケージを選択してオプションを設定する ###
    **[パッケージの選択内容]** ページで、実行する複数のパッケージを選択し、パッケージごとに環境、パラメーター、接続マネージャー、および詳細オプションを設定します。 これらのオプションを設定するには、パッケージをクリックします。
    
    **[詳細]** タブで、**[再試行回数]** という Scale Out オプションを設定します。 パッケージの実行に失敗した場合の再試行回数を設定します。
3. ### <a name="select-machines"></a>マシンを選択する ###
    **[Machine Selection (マシンの選択)]** ページで、パッケージを実行する Scale Out Worker マシンを選択します。 既定では、任意のマシンでパッケージを実行できます。 

   > [!NOTE]
> パッケージは、**[Machine Selection (マシンの選択)]** ページに表示される、Scale Out Worker サービスのユーザー アカウント資格情報で実行されます。 既定のアカウントは NT Service\SSISScaleOutWorker140 です。 自分のラボ アカウントを変更することができます。

4. ### <a name="run-the-packages-and-view-reports"></a>パッケージを実行してレポートを表示する 
    パッケージの実行を開始するには、**[OK]** をクリックします。 パッケージの実行レポートを表示するには、オブジェクト エクスプローラーでパッケージを右クリックし、**[レポート]**、**[すべての実行]** の順にクリックして実行を見つけます。
    
    
## <a name="run-packages-with-stored-procedures"></a>ストアド プロシージャでパッケージを実行する

1. ### <a name="create-executions"></a>実行を作成する ###
    パッケージごとに [catalog].[create_execution] を呼び出します。 パラメーター **@runincluster** を True に設定します。 一部の Scale Out Worker マシンでパッケージを実行できない場合は、パラメーター **@useanyworker** を False に設定します。   
2. ### <a name="set-execution-parameters"></a>実行パラメーターを設定する ###
    実行ごとに [catalog].[set_execution_parameter_value] を呼び出します。
3. ### <a name="set-scale-out-workers"></a>Scale Out Worker を設定する ###
    [catalog].[add_execution_worker] を呼び出します。 任意のマシンでパッケージを実行できる場合は、このストアド プロシージャを呼び出す必要はありません。 
4. ### <a name="start-executions"></a>実行を開始する ###
    [catalog].[start_execution] を呼び出します。 パラメーター **@retry_count** でパッケージの実行に失敗した場合の再試行回数を設定します。
    
    ### <a name="example"></a>例  ###  
    次の例では、1 つの Scale Out Worker を使用して、Scale Out で package1.dtsx および package2.dtsx という 2 つのパッケージを実行します。  
    ```
    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO

    Declare @execution_id bigint
    EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runincluster=True
    Select @execution_id
    DECLARE @var0 smallint = 1
    EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
    EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
    EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
    GO
    ```


## <a name="permissions"></a>Permissions
Scale Out でパッケージを実行するには、次のアクセス許可のいずれかが必要です。

-   **ssis_admin** データベース ロールのメンバーシップ  

-   **ssis_cluster_executor** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  
    
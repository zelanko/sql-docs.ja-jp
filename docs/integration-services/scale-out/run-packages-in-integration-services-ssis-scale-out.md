---
title: "SQL Server Integration Services (SSIS) Scale Out でパッケージを実行する | Microsoft Docs"
ms.custom: 
ms.date: 07/18/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: scale-out
ms.reviewer: 
ms.suite: sql
ms.technology: integration-services
ms.tgt_pltfrm: 
ms.topic: article
caps.latest.revision: "1"
author: haoqian
ms.author: haoqian
manager: jhubbard
f1_keywords: sql13.ssis.ssms.ispackageexecuteinscaleout.f1
ms.workload: Inactive
ms.openlocfilehash: 88537ff52ada042d642b8915342e374ecca3246e
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="run-packages-in-integration-services-ssis-scale-out"></a>Integration Services (SSIS) Scale Out でパッケージを実行する
Integration Services サーバーにパッケージが展開されたら、Scale Out でパッケージを実行できます。

## <a name="run-packages-with-execute-package-in-scale-out-dialog"></a>[Scale Out でパッケージを実行] ダイアログを使用してパッケージを実行する 

1. [Execute Package In Scale Out (Scale Out でパッケージを実行)] ダイアログ ボックスを開く

    [!INCLUDE[ssManStudioFull_md](../../includes/ssmanstudiofull-md.md)] で、Integration Services サーバーに接続します。 オブジェクト エクスプローラーで、ツリーを展開し、 **[Integration Services カタログ]**のノードを表示します。 **SSISDB** ノード、プロジェクト、または実行するパッケージを右クリックし、 **[Execute in Scale Out (Scale Out で実行)]**をクリックします。

2. パッケージを選択してオプションを設定する

    **[パッケージの選択内容]** ページで、実行する複数のパッケージを選択し、パッケージごとに環境、パラメーター、接続マネージャー、および詳細オプションを設定します。 これらのオプションを設定するには、パッケージをクリックします。
    
    **[詳細]** タブで、 **[再試行回数]**という Scale Out オプションを設定します。 パッケージの実行に失敗した場合の再試行回数を設定します。

    > [!Note]
    > Scale Out Worker サービスを実行しているアカウントがローカル コンピューターの管理者である場合、**[エラー時にダンプする]** オプションのみが有効になります。

3. マシンを選択する

    **[Machine Selection (マシンの選択)]** ページで、パッケージを実行する Scale Out Worker マシンを選択します。 既定では、任意のマシンでパッケージを実行できます。 

   > [!Note] 
   > パッケージは、 **[Machine Selection (マシンの選択)]** ページに表示される、Scale Out Worker サービスのユーザー アカウント資格情報で実行されます。 既定のアカウントは NT Service\SSISScaleOutWorker140 です。 自分のラボ アカウントを変更することができます。

   >[!WARNING]
   >パッケージの実行が同じワーカー上の別のユーザーによってトリガーされた場合、同じアカウントで実行されます。 それらの間にセキュリティ境界はありません。 

4. パッケージを実行してレポートを表示する 

    パッケージの実行を開始するには、 **[OK]** をクリックします。 パッケージの実行レポートを表示するには、オブジェクト エクスプローラーでパッケージを右クリックし、 **[レポート]**、 **[すべての実行]**の順にクリックして実行を見つけます。
    
## <a name="run-packages-with-stored-procedures"></a>ストアド プロシージャでパッケージを実行する

1. 実行を作成する

    パッケージごとに [catalog].[create_execution] を呼び出します。 パラメーター **@runinscaleout** を True に設定します。 一部の Scale Out Worker マシンでパッケージを実行できない場合は、パラメーター **@useanyworker** を False に設定します。   

2. 実行パラメーターを設定する

    実行ごとに [catalog].[set_execution_parameter_value] を呼び出します。

3. Scale Out Worker を設定する

    [catalog].[add_execution_worker] を呼び出します。 任意のマシンでパッケージを実行できる場合は、このストアド プロシージャを呼び出す必要はありません。 

4. 実行を開始する

    [catalog].[start_execution] を呼び出します。 パラメーター **@retry_count** でパッケージの実行に失敗した場合の再試行回数を設定します。
    
#### <a name="example"></a>例
次の例では、1 つの Scale Out Worker を使用して、Scale Out で package1.dtsx および package2.dtsx という 2 つのパッケージを実行します。  

```sql
Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package1.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder1', @project_name=N'project1', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO

Declare @execution_id bigint
EXEC [SSISDB].[catalog].[create_execution] @package_name=N'package2.dtsx', @execution_id=@execution_id OUTPUT, @folder_name=N'folder2', @project_name=N'project2', @use32bitruntime=False, @reference_id=Null, @useanyworker=False, @runinscaleout=True
Select @execution_id
DECLARE @var0 smallint = 1
EXEC [SSISDB].[catalog].[set_execution_parameter_value] @execution_id,  @object_type=50, @parameter_name=N'LOGGING_LEVEL', @parameter_value=@var0
EXEC [SSISDB].[catalog].[add_execution_worker] @execution_id,  @workeragent_id=N'64c020e2-f819-4c2d-a22f-efb31a91e70a'
EXEC [SSISDB].[catalog].[start_execution] @execution_id,  @retry_count=0
GO
```

### <a name="permissions"></a>Permissions
Scale Out でパッケージを実行するには、次のアクセス許可のいずれかが必要です。

-   **ssis_admin** データベース ロールのメンバーシップ  

-   **ssis_cluster_executor** データベース ロールのメンバーシップ  
  
-   **sysadmin** サーバー ロールのメンバーシップ  

## <a name="set-default-execution-mode"></a>既定の実行モードを設定する
既定の実行モードを "Scale Out" に設定するには、SSMS のオブジェクト エクスプローラーで **SSISDB** ノードを右クリックし、**[プロパティ]** を選択します。
**[カタログ プロパティ]** ダイアログで、**[サーバー全体の既定の実行モード]** を **[Scale Out]** に設定します。

これを設定したら、[catalog].[create_execution] の **@runinscaleout**パラメーターを指定する必要はありません。 実行は、Scale Out で自動的に実行されます。 

![実行モード](media\exe-mode.PNG)

既定の実行モードを -Scale Out 以外のモードに戻すには、**[サーバー全体の既定の実行モード]** を **[サーバー]** に設定するだけです。

## <a name="run-package-in-sql-agent-job"></a>SQL エージェント ジョブでパッケージを実行する
SQL エージェント ジョブで、ジョブの 1 つの手順として SSIS パッケージを実行することを選択できます。 Scale Out でパッケージを実行するため、上記の既定の実行モードを利用できます。 既定の実行モードを "Scale Out" に設定すると、SQL エージェント ジョブ内のパッケージが Scale Out で実行されます。

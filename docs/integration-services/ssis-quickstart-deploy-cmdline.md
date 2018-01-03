---
title: "コマンド プロンプトから SSIS プロジェクトを配置する | Microsoft Docs"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: non-specific
ms.suite: sql
ms.custom: 
ms.technology: integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a753aa1418e935604148d0d42afa22716dec1b17
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>ISDeploymentWizard.exe を使用して、コマンド プロンプトから SSIS プロジェクトを配置する
このクイック スタート チュートリアルでは、Integration Services 配置ウィザード `ISDeploymentWizard.exe` を実行して、コマンド プロンプトから、SSIS プロジェクトを配置する方法を示します。

Integration Services 配置ウィザードの詳細については、「[Integration Services 配置ウィザード](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard)」を参照してください。

## <a name="start-the-integration-services-deployment-wizard"></a>Integration Services 配置ウィザードを起動する
1. コマンド プロンプト ウィンドウを開きます。

2. `ISDeploymentWizard.exe` を実行します。 Integration Services 配置ウィザードが開きます。

    `ISDeploymentWizard.exe` を含むフォルダーが `path` 環境変数にない場合、そのディレクトリに変更するために `cd` コマンドを使用する必要がある場合があります。 SQL Server 2017 の場合、このフォルダーは通常 `C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn` です。

## <a name="deploy-a-project-with-the-wizard"></a>ウィザードを使用してプロジェクトを配置する
1. ウィザードの **[概要]** ページで、概要を確認します。 **[次へ]** をクリックして、**[ソースの選択]** ページを開きます。

2. **[ソースの選択]** ページで、配置する既存の SSIS プロジェクトを選びます。
    -   作成したプロジェクト配置ファイルを配置するには、 **[プロジェクト配置ファイル]** を選択して .ispac ファイルのパスを入力します。
    -   SSIS カタログにあるプロジェクトを配置するには、**[Integration Services カタログ]** を選び、サーバー名とカタログ内のプロジェクトのパスを入力します。
    **[次へ]** をクリックして、 **[配置先の選択]** ページを表示します。
  
3.  **[配置先の選択]** ページで、プロジェクトの配置先を選びます。
    -   完全修飾サーバー名を入力します。 対象サーバーが Azure SQL Database サーバーの場合、名前は次の形式になります。`<server_name>.database.windows.net`
    -   **[参照]** をクリックして、SSISDB でターゲット フォルダーを選びます。
    **[次へ]** をクリックして **[レビュー]** ページを開きます。  
  
4.  **[レビュー]** ページで、選択した設定を確認します。
    -   選択内容を変更するには、 **[戻る]**をクリックするか、左ペインでいずれかの手順をクリックします。
    -   **[配置]** をクリックして、配置プロセスを開始します。
  
5.  配置プロセスが完了すると、**[結果]** ページが開きます。 このページでは、各アクションが成功したか、失敗したかを表示します。
    -   アクションが失敗した場合は、**[結果]** 列の **[失敗]** をクリックすると、エラーの説明が表示されます。
    -   必要に応じて、**[レポートの保存]** をクリックして結果を XML ファイルに保存します。
    -   **[閉じる]** をクリックしてウィザードを終了します。

## <a name="next-steps"></a>次の手順
- パッケージを配置する他の方法を検討します。
    - [SSMS を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-ssms.md)
    - [Transact-SQL (SSMS) を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Transact-SQL (VS Code) を使用して SSIS パッケージを配置する](ssis-quickstart-deploy-tsql-vscode.md)
    - [PowerShell を使用して SSIS パッケージを配置する](ssis-quickstart-deploy-powershell.md)
    - [C# を使用して SSIS パッケージを配置する](./ssis-quickstart-deploy-dotnet.md) 
- 配置されたパッケージを実行します。 パッケージを実行するには、いくつかのツールおよび言語から選択することができます。 詳細については、次の記事をご覧ください。
    - [SSMS を使用して SSIS パッケージを実行する](./ssis-quickstart-run-ssms.md)
    - [Transact-SQL (SSMS) を使用して SSIS パッケージを実行する](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact-SQL (VS Code) を使用して SSIS パッケージを実行する](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから SSIS パッケージを実行する](./ssis-quickstart-run-cmdline.md)
    - [PowerShell を使用して SSIS パッケージを実行する](ssis-quickstart-run-powershell.md)
    - [C# を使用して SSIS パッケージを実行する](./ssis-quickstart-run-dotnet.md) 

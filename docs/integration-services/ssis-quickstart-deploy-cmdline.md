---
title: "コマンド プロンプトから、SSIS プロジェクトを配置 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: integration-services
ms.suite: sql
ms.custom: 
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: bc1321dd91a0fcb7ab76b207301c6302bb3a5e64
ms.openlocfilehash: 0f1c7733f0ce6b132c209961a1fd12da80cbd282
ms.contentlocale: ja-jp
ms.lasthandoff: 10/06/2017

---
# <a name="deploy-an-ssis-project-from-the-command-prompt-with-isdeploymentwizardexe"></a>ISDeploymentWizard.exe でコマンド プロンプトから、SSIS プロジェクトを配置します。
このクイック スタート チュートリアルは、Integration Services 配置ウィザードを実行して、コマンド プロンプトから、SSIS プロジェクトを配置する方法を示します`ISDeploymentWizard.exe`です。

Integration Services 配置ウィザードの詳細については、次を参照してください。 [Integration Services 配置ウィザード](packages/deploy-integration-services-ssis-projects-and-packages.md#integration-services-deployment-wizard)です。

## <a name="start-the-integration-services-deployment-wizard"></a>Integration Services 配置ウィザードを開始します。
1. コマンド プロンプト ウィンドウを開きます。

2. Run `ISDeploymentWizard.exe`. Integration Services 配置ウィザードを開きます。

    フォルダーを含む`ISDeploymentWizard.exe`に含まれていない、`path`環境変数を使用する必要があります、`cd`そのディレクトリに変更するコマンド。 SQL Server 2017、このフォルダーは通常`C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`です。

## <a name="deploy-a-project-with-the-wizard"></a>ウィザードを使用してプロジェクトを配置します。
1. **概要**ページ、ウィザードの概要を確認します。 をクリックして**次**を開くには、**ソースの選択**ページ。

2. **ソースの選択** ページで、展開する既存の SSIS プロジェクトを選択します。
    -   作成したプロジェクト配置ファイルを配置するには、 **[プロジェクト配置ファイル]** を選択して .ispac ファイルのパスを入力します。
    -   SSIS カタログに存在するプロジェクトを配置するには選択**Integration Services カタログ**、カタログ内のプロジェクトに、サーバー名とパスを入力します。
    **[次へ]** をクリックして、 **[配置先の選択]** ページを表示します。
  
3.  **先の選択** ページで、プロジェクトの対象を選択します。
    -   完全修飾サーバー名を入力します。 名前がこの形式では、対象サーバーが Azure SQL データベース サーバーの場合:`<server_name>.database.windows.net`です。
    -   をクリックして**参照**SSISDB では、対象フォルダーを選択します。
    をクリックして**次**を開くには、**レビュー**ページ。  
  
4.  **確認** ページで選択した設定を確認します。
    -   選択内容を変更するには、 **[戻る]**をクリックするか、左ペインでいずれかの手順をクリックします。
    -   **[配置]** をクリックして、配置プロセスを開始します。
  
5.  展開処理が完了した後、**結果**ページが開きます。 このページでは、各アクションが成功したか、失敗したかを表示します。
    -   操作に失敗した場合にをクリックして**失敗**で、**結果**エラーの説明を表示する列。
    -   必要に応じて、をクリックして**レポートを保存しています.**結果を XML ファイルに保存します。
    -   をクリックして**閉じる**ウィザードを終了します。

## <a name="next-steps"></a>次の手順
- パッケージを配置するには、その他の方法を検討してください。
    - [SSMS で SSIS パッケージを展開します。](./ssis-quickstart-deploy-ssms.md)
    - [SSIS パッケージにより、TRANSACT-SQL (SSMS) での展開します。](./ssis-quickstart-deploy-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを展開します。](ssis-quickstart-deploy-tsql-vscode.md)
    - [PowerShell を使用した SSIS パッケージを展開します。](ssis-quickstart-deploy-powershell.md)
    - [C# を使用して、SSIS パッケージを展開します。](./ssis-quickstart-deploy-dotnet.md) 
- 配置されたパッケージを実行します。 パッケージを実行するには、いくつかのツールおよび言語から選択することができます。 詳細については、次の記事を参照してください。
    - [SSMS での SSIS パッケージを実行します。](./ssis-quickstart-run-ssms.md)
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [コマンド プロンプトから、SSIS パッケージを実行します。](./ssis-quickstart-run-cmdline.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 


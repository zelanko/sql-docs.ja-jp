---
title: Azure で SSIS パッケージを実行する | Microsoft Docs
ms.description: Provides an overview of the available methods for running packages deployed to Azure SQL Database.
ms.date: 05/29/2018
ms.topic: conceptual
ms.prod: sql
ms.prod_service: integration-services
ms.component: lift-shift
ms.suite: sql
ms.custom: ''
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: e4d733b49f8353fc430f90161ef25c352c8cac8f
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34586087"
---
# <a name="run-an-ssis-package-in-azure"></a>Azure で SSIS パッケージを実行する

この記事で説明するオプションの 1 つを選択することで、Azure SQL Database サーバーで SSISDB カタログ データベースにデプロイされている SSIS パッケージを実行できます。 パッケージは直接実行するか、Azure Data Factory パイプラインの一部として実行できます。 Azure の SSIS の概要については、「[SQL Server Integration Services ワークロードをクラウドにリフト アンド シフトする](ssis-azure-lift-shift-ssis-packages-overview.md)」を参照してください。

- パッケージを直接実行する

  - [SSMS を使用しての実行](#ssms)

  - [ストアド プロシージャを使用しての実行](#sproc)

  - [スクリプトまたはコードを使用しての実行](#script)

- Azure Data Factory パイプラインの一部としてパッケージを実行する

  - [SSIS パッケージ アクティビティの実行で実行する](#exec_activity)

  - [ストアド プロシージャ アクティビティを使用して実行する](#sproc_activity)

> [!NOTE]
> `dtexec.exe` によるパッケージの実行は、Azure にデプロイされているパッケージではテストされていません。

## <a name="ssms"></a> SSMS でのパッケージの実行

SQL Server Management Studio (SSMS) では、SSIS カタログ データベース SSISDB にデプロイされたパッケージを右クリックして **[実行]** を選択することで、**[パッケージの実行]** ダイアログ ボックスを開くことができます。 詳細については、「[SQL Server Management Studio (SSMS) を使用して SSIS プロジェクトを配置する](../ssis-quickstart-run-ssms.md)」を参照してください。

## <a name="sproc"></a> ストアド プロシージャでパッケージを実行する

Azure SQL Database に接続し、Transact-SQL コードを実行できるあらゆる環境で、次のストアド プロシージャを呼び出すことでパッケージを実行できます。

1. **[catalog].[create_execution]**. 詳細については、「[catalog.create_execution](../system-stored-procedures/catalog-create-execution-ssisdb-database.md)」を参照してください。

2. **[catalog].[set_execution_parameter_value]**. 詳細については、「[catalog.set_execution_parameter_value](../system-stored-procedures/catalog-set-execution-parameter-value-ssisdb-database.md)」を参照してください。

3. **[catalog].[start_execution]** 詳細については、「[catalog.start_execution](../system-stored-procedures/catalog-start-execution-ssisdb-database.md)」を参照してください。

詳細については、次の例をご覧ください。

- [Transact-SQL を使用して SSMS から SSIS パッケージを実行する](../ssis-quickstart-run-tsql-ssms.md)

- [Transact-SQL を使用して Visual Studio Code から SSIS パッケージを実行する](../ssis-quickstart-run-tsql-vscode.md)

## <a name="script"></a> スクリプトまたはコードでパッケージを実行する

マネージド API を呼び出すことができるあらゆる開発環境で、`Microsoft.SQLServer.Management.IntegrationServices` 名前空間で `Package` オブジェクトの `Execute` メソッドを呼び出すことでパッケージを実行できます。

詳細については、次の例をご覧ください。

- [PowerShell を使用して SSIS パッケージを実行する](../ssis-quickstart-run-powershell.md)

- [.NET アプリで C# コードを使用して SSIS パッケージを実行する](../ssis-quickstart-run-dotnet.md)

## <a name="exec_activity"></a> SSIS パッケージの実行アクティビティを使用してパッケージを実行する

詳細については、[Azure Data Factory で SSIS パッケージの実行アクティビティを使用して SSIS パッケージを実行する](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-ssis-activity)方法に関するページを参照してください。

## <a name="sproc_activity"></a> ストアド プロシージャ アクティビティを使用してパッケージを実行する

詳細については、「[Azure Data Factory のストアド プロシージャ アクティビティを使用して SSIS パッケージを実行する](https://docs.microsoft.com/azure/data-factory/how-to-invoke-ssis-package-stored-procedure-activity)」をご覧ください。

## <a name="next-steps"></a>次の手順

Azure にデプロイされている SSIS パッケージのスケジュール設定オプションについて学習してください。 詳しくは、[Azure で SSIS パッケージの実行スケジュールを設定する](ssis-azure-schedule-packages.md)方法に関するページを参照してください。
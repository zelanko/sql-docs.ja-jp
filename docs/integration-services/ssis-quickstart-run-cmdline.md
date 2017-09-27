---
title: "コマンド プロンプトから、SSIS パッケージを実行 |Microsoft ドキュメント"
ms.date: 09/25/2017
ms.topic: article
ms.prod: sql-server-2017
ms.technology:
- integration-services
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.translationtype: MT
ms.sourcegitcommit: 656e62f36446db4ef5b232129130a0253d2aebdf
ms.openlocfilehash: a33b8518ec3284f5de73d38c87209057dc1c7487
ms.contentlocale: ja-jp
ms.lasthandoff: 09/22/2017

---
# <a name="run-an-ssis-package-from-the-command-prompt-with-dtexecexe"></a>DTExec.exe を使用してコマンド プロンプトから、SSIS パッケージを実行します。
このクイック スタート チュートリアルを実行して、コマンド プロンプトから、SSIS パッケージを実行する方法を示しています`DTExec.exe`適切なパラメーターを使用します。

> [!NOTE]
> この記事で説明されているメソッドは、Azure SQL Database サーバーに展開されているパッケージでテストされていません。

詳細については`DTExec.exe`を参照してください[dtexec ユーティリティ](https://docs.microsoft.com/en-us/sql/integration-services/packages/dtexec-utility)です。

## <a name="run-a-package-with-dtexec"></a>Dtexec でパッケージを実行します。

フォルダーを含む`DTExec.exe`に含まれていない、`path`環境変数を使用する必要があります、`cd`そのディレクトリに変更するコマンド。 SQL Server 2017、このフォルダーは通常`C:\Program Files (x86)\Microsoft SQL Server\140\DTS\Binn`です。

次の例で使用するパラメーター値には、プログラムで実行されますパッケージを指定したフォルダー パスに、SSIS サーバーの SSIS カタログ データベース (SSISDB) をホストするサーバーは、します。 `/Server`パラメーターは、サーバー名を提供します。 プログラムは、Windows 統合認証では、現在のユーザーとして接続します。 SQL 認証を使用するには指定、`/User`と`Password`適切な値を持つパラメーター。

1. コマンド プロンプト ウィンドウを開きます。

2. 実行`DTExec.exe`の最低値を指定し、`ISServer`と`Server`パラメーターは、次の例で示すように。

    ```cmd
    dtexec /ISServer "\SSISDB\Project1Folder\Integration Services Project1\Package.dtsx" /Server "localhost"
    ```

## <a name="next-steps"></a>次の手順
- パッケージを実行するには、その他の方法を検討してください。
    - [SSMS での SSIS パッケージを実行します。](./ssis-quickstart-run-ssms.md)
    - [TRANSACT-SQL (SSMS) で、SSIS パッケージを実行します。](./ssis-quickstart-run-tsql-ssms.md)
    - [Transact SQL (VS Code) を使用した SSIS パッケージを実行します。](ssis-quickstart-run-tsql-vscode.md)
    - [PowerShell での SSIS パッケージを実行します。](ssis-quickstart-run-powershell.md)
    - [C# を使用して、SSIS パッケージを実行します。](./ssis-quickstart-run-dotnet.md) 


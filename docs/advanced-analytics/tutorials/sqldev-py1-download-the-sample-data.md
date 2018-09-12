---
title: サンプル データのダウンロード手順 1 |Microsoft Docs
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: tutorial
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 07a9b5219649b370b0a5df1e53cf75765f18ec7f
ms.sourcegitcommit: 2666ca7660705271ec5b59cc5e35f6b35eca0a96
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 09/06/2018
ms.locfileid: "43888320"
---
# <a name="step-1-download-the-sample-data"></a>手順 1: サンプル データをダウンロードします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルの一部[SQL 開発者向けの in-database Python analytics](sqldev-in-database-python-for-sql-developers.md)します。 

データと、このチュートリアル用のスクリプトは、Github で共有されます。 この手順では、PowerShell スクリプトを使用して独自のローカル ディレクトリにデータとスクリプト ファイルをダウンロードします。

## <a name="run-the-script"></a>スクリプトを実行します

1. Windows PowerShell コマンド コンソールを開きます。

    オプションを使用**管理者として実行**先ディレクトリを作成または指定したコピー先にファイルの書き込みに管理者特権が必要な場合、します。

2. パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。  ここで使用した既定値は`C:\temp\pysql`します。

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    *DestDir* で指定したフォルダーが存在しない場合、PowerShell スクリプトによって作成されます。
    
    PowerShell スクリプトの実行ポリシーを一時的に設定エラーが発生する場合**無制限**を使用してこのチュートリアルでは、**バイパス**引数と、現在のセッションへの変更のスコープを設定します。 このコマンドを実行しても、構成は変更されません。
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. インターネット接続に応じて、ダウンロードに時間がかかる場合があります。 

## <a name="view-results"></a>結果を表示します。

すべてのファイルがダウンロードされると、  *DestDir*で指定したフォルダーが PowerShell スクリプトによって開かれます。 

+ PowerShell のコマンド プロンプトで、ダウンロードされたファイルを一覧表示、次のコマンドを実行します。

    ```ps
    ls
    ```

![PowerShell スクリプトによってダウンロードされたファイルの一覧](media/sqldev-python-filelist.png "PowerShell スクリプトによってダウンロードされたファイルの一覧")

## <a name="next-step"></a>次の手順

[手順 2: PowerShell を使用した SQL Server へのデータのインポート](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>前の手順

[In-database Python Analytics SQL 開発者向け](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>参照

[SQL Server での Python 拡張機能](../concepts/extension-python.md)



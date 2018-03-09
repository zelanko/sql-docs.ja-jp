---
title: "手順 1: サンプル データのダウンロード |Microsoft ドキュメント"
ms.custom: 
ms.date: 10/17/2017
ms.reviewer: 
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: 
ms.technology: 
ms.tgt_pltfrm: 
ms.topic: tutorial
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 
author: jeannt
ms.author: jeannt
manager: cgronlund
ms.openlocfilehash: 3375e4163533b9f6bf8c96329876faedace14b62
ms.sourcegitcommit: 99102cdc867a7bdc0ff45e8b9ee72d0daade1fd3
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/11/2018
---
# <a name="step-1-download-the-sample-data"></a>手順 1: サンプル データをダウンロードします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、チュートリアルのパート[SQL 開発者のためのデータベースでの Python analytics](sqldev-in-database-python-for-sql-developers.md)です。 

データもこのチュートリアル用のスクリプトは、Github で共有されます。 この手順で独自のローカル ディレクトリに、データ ファイルとスクリプト ファイルをダウンロードするのに PowerShell スクリプトを使用します。

## <a name="run-the-script"></a>スクリプトを実行します。

1. Windows PowerShell コマンド コンソールを開きます。

    オプションを使用**管理者として実行**先ディレクトリを作成または指定したコピー先へファイルを作成、管理特権が必要な場合、します。

2. パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。  ここで使用した既定値は`C:\temp\pysql`します。

    ```ps
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\temp\pysql'
    ```
    
    *DestDir* で指定したフォルダーが存在しない場合、PowerShell スクリプトによって作成されます。
    
    PowerShell スクリプトの実行のポリシーを一時的に設定エラーが発生した場合**無制限**を使用してこのチュートリアルで、**バイパス**引数と、現在のセッションへの変更のスコープです。 このコマンドを実行しても、構成は変更されません。
    
    ```ps
    Set-ExecutionPolicy Bypass -Scope Process
    ```

3. インターネットの接続に応じて、ダウンロードに時間がかかる可能性があります。 

## <a name="view-the-results"></a>結果を表示します。

すべてのファイルがダウンロードされると、  *DestDir*で指定したフォルダーが PowerShell スクリプトによって開かれます。 

+ PowerShell コマンド プロンプトで、ダウンロードされたファイルの一覧に、次のコマンドを実行します。

    ```ps
    ls
    ```

![PowerShell スクリプトによってダウンロードされたファイルの一覧](media/sqldev-python-filelist.png "PowerShell スクリプトによってダウンロードされたファイルの一覧")

## <a name="next-step"></a>次の手順

[手順 2: PowerShell を使用した SQL Server へのデータのインポート](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>前の手順

[データベース内 Python 分析、SQL 開発者向け](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)



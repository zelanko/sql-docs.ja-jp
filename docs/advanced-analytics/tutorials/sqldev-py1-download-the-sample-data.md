---
title: "手順 1: サンプル データのダウンロード |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/25/2017
ms.prod: sql-server-2017
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2017
dev_langs:
- Python
- TSQL
ms.assetid: 
caps.latest.revision: 2
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 147860e9af8cce86d1a7ccbd3e53f20d240fcd49
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="step-1-download-the-sample-data"></a>手順 1: サンプル データのダウンロード

この手順で、サンプル データセットと、スクリプトをダウンロードします。 データとスクリプト ファイルはいずれも Github で共有されていますが、PowerShell スクリプトでデータとスクリプト ファイルをユーザーが選択したローカル ディレクトリにダウンロードできます。

## <a name="download-the-data-and-scripts"></a>データとスクリプトをダウンロードする

1. Windows PowerShell コマンド コンソールを開きます。

    オプションを使用**管理者として実行**先ディレクトリを作成または指定したコピー先へファイルを作成、管理特権が必要な場合、します。

2. パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。  ここで使用した既定値は**TempPythonSQL**です。

    ```
    $source = 'https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/PythonSQL/Download_Scripts_SQL_Walkthrough.ps1'
    $ps1_dest = "$pwd\Download_Scripts_SQL_Walkthrough.ps1"
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir 'C:\tempPythonSQL'
    ```
    
    *DestDir* で指定したフォルダーが存在しない場合、PowerShell スクリプトによって作成されます。
    
    エラーが発生した場合は、PowerShell スクリプトの実行ポリシーを一時的に設定できます**無制限**を使用してこのチュートリアルでは、に対してのみ、**バイパス**引数と、現在の変更のスコープセッションです。 このコマンドを実行しても、構成は変更されません。
    
    `Set\-ExecutionPolicy Bypass \-Scope Process`

3. インターネット接続によっては、ダウンロードに時間がかかる場合があります。 すべてのファイルがダウンロードされると、  *DestDir*で指定したフォルダーが PowerShell スクリプトによって開かれます。 PowerShell コマンド プロンプトで次のコマンドを実行し、ダウンロードされたファイルを確認します。

    ```
    ls
    ```
**結果:**

![PowerShell スクリプトによってダウンロードされたファイルの一覧](media/sqldev-python-filelist.png "PowerShell スクリプトによってダウンロードされたファイルの一覧")

## <a name="next-step"></a>次の手順

[手順 2: PowerShell を使用して SQL Server にデータをインポートする](sqldev-py2-import-data-to-sql-server-using-powershell.md)

## <a name="previous-step"></a>前の手順

[データベース内 Python 分析、SQL 開発者向け](sqldev-in-database-python-for-sql-developers.md)

## <a name="see-also"></a>参照

[Machine Learning Python のサービス](../python/sql-server-python-services.md)




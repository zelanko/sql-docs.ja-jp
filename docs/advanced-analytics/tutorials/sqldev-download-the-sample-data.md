---
title: 'レッスン 1: サンプル データのダウンロード |Microsoft ドキュメント'
ms.custom: ''
ms.date: 07/26/2016
ms.reviewer: ''
ms.suite: sql
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.component: ''
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: tutorial
applies_to:
- SQL Server 2016
dev_langs:
- R
- TSQL
ms.author: heidist
author: HeidiSteen
manager: cgronlun
ms.workload: Inactive
ms.openlocfilehash: 33e0e9ef26085226d3a83d97567bf60eac030f1e
ms.sourcegitcommit: 059fc64ba858ea2adaad2db39f306a8bff9649c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/04/2018
---
# <a name="lesson-1-download-the-sample-data"></a>レッスン 1: サンプル データをダウンロードします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

この手順で、サンプル データセットをダウンロードおよび[!INCLUDE[tsql](../../includes/tsql-md.md)]このチュートリアルで使用されるファイルのスクリプトを作成します。 データとスクリプト ファイルの両方が、GitHub の共有が、PowerShell スクリプトは、独自のローカル ディレクトリに、データ ファイルとスクリプト ファイルをダウンロードします。

## <a name="download-the-data-and-scripts"></a>データとスクリプトをダウンロードします。

1.  Windows PowerShell コマンド コンソールを開きます。
  
    保存先のディレクトリの作成や、指定した宛先へのファイルの書き込みに管理者特権が必要な場合、**[管理者として実行]** オプションを使用します。
  
2.  パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。  ここで使用した既定値は **TempRSQL**です。
  
    ```ps
    $source = ‘https://raw.githubusercontent.com/Azure/Azure-MachineLearning-DataScience/master/Misc/RSQL/Download_Scripts_SQL_Walkthrough.ps1’  
    $ps1_dest = “$pwd\Download_Scripts_SQL_Walkthrough.ps1”
    $wc = New-Object System.Net.WebClient
    $wc.DownloadFile($source, $ps1_dest)
    .\Download_Scripts_SQL_Walkthrough.ps1 –DestDir ‘C:\tempRSQL’
    ```
  
    *DestDir* で指定したフォルダーが存在しない場合、PowerShell スクリプトによって作成されます。
  
    > [!TIP]
    > エラーが発生した場合は、このチュートリアルで使用するためのみに PowerShell スクリプトの実行ポリシーを、Bypass 引数を使用し、変更を現在のセッションにスコープして、一時的に **unrestricted** に設定できます。
    >   
    >````
    > Set\-ExecutionPolicy Bypass \-Scope Process
    >````
    > このコマンドを実行しても、構成は変更されません。
  
    インターネット接続によっては、ダウンロードに時間がかかる場合があります。
  
3.  すべてのファイルがダウンロードされると、  *DestDir*で指定したフォルダーが PowerShell スクリプトによって開かれます。 PowerShell コマンド プロンプトで次のコマンドを実行し、ダウンロードされたファイルを確認します。
  
    ```
    ls
    ```
  
    **結果:**
  
    ![PowerShell スクリプトによってダウンロードされたファイルの一覧](media/rsql-devtut-filelist.png "PowerShell スクリプトによってダウンロードされたファイルの一覧")
  
## <a name="next-lesson"></a>次のレッスン

[レッスン 2: PowerShell を使用して SQL server のデータをインポートします。](../r/sqldev-import-data-to-sql-server-using-powershell.md)

## <a name="previous-lesson"></a>前のレッスン

[SQL 開発者のためのデータベース内 R の分析](../tutorials/sqldev-in-database-r-for-sql-developers.md)

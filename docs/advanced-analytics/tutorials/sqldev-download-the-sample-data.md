---
title: "レッスン 1: サンプル データのダウンロード |Microsoft ドキュメント"
ms.custom: 
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
applies_to:
- SQL Server 2016
dev_langs:
- R
- TSQL
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: 10
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 1843dc06a0587e34e0ed369ea54fd5b71b217b24
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="lesson-1-download-the-sample-data"></a>レッスン 1: サンプル データをダウンロードします。

この記事は、SQL Server で R を使用する方法で SQL 開発者のためのチュートリアルの一部です。

この手順で、サンプル データセットをダウンロードおよび[!INCLUDE[tsql](../../includes/tsql-md.md)]このチュートリアルで使用されるファイルのスクリプトを作成します。 データとスクリプト ファイルの両方が、GitHub の共有が、PowerShell スクリプトは、独自のローカル ディレクトリに、データ ファイルとスクリプト ファイルをダウンロードします。

## <a name="download-the-data-and-scripts"></a>データとスクリプトをダウンロードします。

1.  Windows PowerShell コマンド コンソールを開きます。
  
    保存先のディレクトリの作成や、指定した宛先へのファイルの書き込みに管理者特権が必要な場合、[ **管理者として実行**] オプションを使用します。
  
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


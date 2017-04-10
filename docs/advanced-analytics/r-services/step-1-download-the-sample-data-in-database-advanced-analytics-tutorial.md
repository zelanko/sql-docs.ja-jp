---
title: "手順 1: サンプル データをダウンロードする (高度な分析 (データベース内) のチュートリアル) | Microsoft Docs"
ms.custom: ""
ms.date: "04/19/2016"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "r-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
applies_to: 
  - "SQL Server 2016"
dev_langs: 
  - "R"
  - "TSQL"
ms.assetid: 32a5d5ad-c58a-4669-a90d-ef296b48fcd8
caps.latest.revision: 10
author: "jeannt"
ms.author: "jeannt"
manager: "jhubbard"
caps.handback.revision: 10
---
# 手順 1: サンプル データをダウンロードする (高度な分析 (データベース内) のチュートリアル)
この手順では、このチュートリアルで使用する、サンプル データセットと [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプト ファイルをダウンロードします。 データとスクリプト ファイルはいずれも Github で共有されていますが、PowerShell スクリプトでデータとスクリプト ファイルをユーザーが選択したローカル ディレクトリにダウンロードできます。  
  
## データとスクリプトをダウンロードする  
  
1.  Windows PowerShell コマンド コンソールを開きます。  
  
    保存先のディレクトリの作成や、指定した宛先へのファイルの書き込みに管理者特権が必要な場合、[**管理者として実行**] オプションを使用します。  
  
2.  パラメーター *DestDir* の値を任意のローカル ディレクトリに変更し、次の PowerShell コマンドを実行します。  ここで使用した既定値は **TempRSQL** です。  
  
    ```  
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
  
3.  すべてのファイルがダウンロードされると、*DestDir* で指定したフォルダーが PowerShell スクリプトによって開かれます。 PowerShell コマンド プロンプトで次のコマンドを実行し、ダウンロードされたファイルを確認します。  
  
    ```  
    ls  
    ```  
  
    **結果:**  
  
    ![list of files downloaded by PowerShell script](../../advanced-analytics/r-services/media/rsql-devtut-filelist.PNG "list of files downloaded by PowerShell script")  
  
## 次の手順  
[手順 2: PowerShell を使用して SQL Server にデータをインポートする](../../advanced-analytics/r-services/step-2-import-data-to-sql-server-using-powershell.md)  
  
## 前の手順  
[SQL 開発者向けの高度な分析 (データベース内) (チュートリアル)](../../advanced-analytics/r-services/in-database-advanced-analytics-for-sql-developers-tutorial.md)  
  
## 参照  
[SQL Server R Services のチュートリアル](../../advanced-analytics/r-services/sql-server-r-services-tutorials.md)  
  
  
  

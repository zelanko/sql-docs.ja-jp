---
title: コマンドプロンプトで Database Experimentation Assistant を実行する
description: コマンドプロンプトで Database Experimentation Assistant を実行する
ms.custom: seo-lt-2019
ms.date: 10/22/2018
ms.prod: sql
ms.prod_service: dea
ms.suite: sql
ms.technology: dea
ms.tgt_pltfrm: ''
ms.topic: conceptual
author: HJToland3
ms.author: ajaykar
ms.reviewer: mathoma
ms.openlocfilehash: c3b87eafa460cfef69666a3837f56626dab81d47
ms.sourcegitcommit: d00ba0b4696ef7dee31cd0b293a3f54a1beaf458
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/13/2019
ms.locfileid: "74056572"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt-sql-server"></a>コマンドプロンプトで Database Experimentation Assistant を実行する (SQL Server)

この記事では、コマンドプロンプトウィンドウを使用して Database Experimentation Assistant (DEA) でトレースをキャプチャし、結果を分析する方法について説明します。 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>DEA コマンドを使用して、新しいワークロードキャプチャを開始します。

新しいワークロードキャプチャを開始するには、次のコマンドを実行します。

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**例**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>ワークロードを再生する

1.  分散再生コントローラーコンピューターにログインします。
2.  DEA コマンドを使用してキャプチャしたワークロードトレースを IRF ファイルに変換します。

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  StartReplayCaptureTrace を使用して、SQL Server を実行しているターゲットコンピューターでトレースキャプチャを開始します。
       
    a.  SQL Server Management Studio (SSMS) で、< Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.sql. を開きます。
    
    b.  指定した時間が経過すると、トレースキャプチャが自動的に停止しないように `Set @durationInMins=0` を実行します。
    
    c.  トレースファイルあたりの最大ファイルサイズを設定するには、`Set @maxfilesize`を実行します。 推奨サイズは 200 (MB) です。
    
    d.  `@Tracefile` を編集して、トレースファイルに一意の名前を設定します。
    
    e.  ワークロードを特定のデータベースでのみキャプチャする必要がある場合は、`@dbname` を編集してデータベース名を指定します。 既定では、サーバー全体のワークロードがキャプチャされます。 
4.  ターゲット SQL Server インスタンスに対して IRF ファイルを再生します。

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    a.  ステータスを監視するには、コマンドプロンプトウィンドウを開き、`DReplay status -f 1`を実行します。
        
    b.  パス% が予想より小さい場合などに再生を停止するには、コマンドプロンプトウィンドウを開いて `DReplay cancel`を実行します。

5.  ターゲット SQL Server インスタンスのトレースキャプチャを停止します。
6.  SSMS で `<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`を開きます。
7.  SQL Server を実行しているターゲットコンピューター上のトレースファイルのパスと一致するように `@Tracefile` を編集します。
8.  SQL Server を実行しているターゲットコンピューターに対してスクリプトを実行します。

## <a name="analyze-traces-by-using-the-dea-command"></a>DEA コマンドを使用してトレースを分析する

新しいトレース分析を開始するには、次のコマンドを実行します。

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**例**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>次の手順

DEA とデモの19分の概要については、次のビデオをご覧ください。

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

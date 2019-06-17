---
title: SQL Server のアップグレードのコマンド プロンプトでデータベース実験アシスタントを実行します。
description: コマンド プロンプトでデータベース実験アシスタントを実行します。
ms.custom: ''
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
manager: jroth
ms.openlocfilehash: c4603bf5fec8f1df8ae1e7fe0e711bf7b6e8f1e9
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "66794426"
---
# <a name="run-database-experimentation-assistant-at-a-command-prompt"></a>コマンド プロンプトでデータベース実験アシスタントを実行します。

この記事では、コマンド プロンプト ウィンドウを使用して、データベース実験アシスタント (DEA)、トレースをキャプチャし、結果を分析する方法について説明します。 

## <a name="start-a-new-workload-capture-by-using-the-dea-command"></a>DEA コマンドを使用して、新しいワークロードのキャプチャを開始します。

新しいワークロード キャプチャを開始するには、次のコマンドを実行します。

`Deacmd.exe -o startcapturetrace -s <SQLServerInstance> -e <encryptconnection> -u <trustservercertificate> -d <database name> -p <trace file path> -f <trace file name> -t <Max duration>`

**例**

`Deacmd.exe -o startcapturetrace -s localhost -e -d adventureworks -p c:\test -f sql2008capture -t 60`

## <a name="replay-a-workload"></a>ワークロードを再生します。

1.  分散再生コント ローラー マシンにログインします。
2.  DEA コマンド、IRF ファイルを使用してキャプチャしたワークロード トレースを変換します。

    `DReplay preprocess -m "dreplaycontroller" -i "Path to first trace file" -d "<Folder path on controller>\IrfFolder"`

3.  StartReplayCaptureTrace.sql を使用して SQL Server を実行しているターゲット コンピューター上のトレース キャプチャを開始します。
       
    A.  SQL Server Management Studio (SSMS) で開く < Dea_InstallPath\>\Scripts\StartReplayCaptureTrace.sql します。
    
    B.  実行`Set @durationInMins=0`トレースのキャプチャは、指定時間後に自動的に停止しないようにします。
    
    c.  トレース ファイルあたりの最大ファイル サイズを設定するには、実行`Set @maxfilesize`します。 推奨サイズは、200 (単位は MB) です。
    
    d.  編集`@Tracefile`トレース ファイルの一意の名前を設定します。
    
    e.  編集`@dbname`場合は、特定のデータベースでのみ、ワークロードをキャプチャする必要があります、データベース名を指定します。 既定では、サーバー全体の負荷がキャプチャされます。 
4.  対象の SQL Server インスタンスに対して IRF ファイルを再生するには。

    `DReplay replay -m "dreplaycontroller" -d "<Folder Path on Dreplay Controller>\IrfFolder" -o -s "SQL2016Target" -w "dreplaychild1,dreplaychild2,dreplaycild3,dreplaychild4"`
        
    A.  状態を監視するには、コマンド プロンプト ウィンドウを開き、実行`DReplay status -f 1`します。
        
    B.  再生を停止するなどパス % が、予想より少ないかのようコマンド プロンプト ウィンドウを開き実行`DReplay cancel`します。

5.  ターゲット SQL Server インスタンスでトレースでキャプチャを停止します。
6.  SSMS で開く`<Dea_InstallPath>\Scripts\StopCaptureTrace.sql`します。
7.  編集`@Tracefile`SQL Server を実行しているターゲット コンピューター上のトレース ファイルのパスに一致するようにします。
8.  SQL Server を実行しているターゲット コンピューターに対してスクリプトを実行します。

## <a name="analyze-traces-by-using-the-dea-command"></a>DEA コマンドを使用してトレースを分析します。

新しいトレースの分析を開始するには、次のコマンドを実行します。

`Deacmd.exe -o analysis -a <Target1 trace filepath> -b <Target2 trace filepath> -r reportname -s <SQLserverInstance> -e <encryptconnection> -u <trustservercertificate>`

**例**

`Deacmd.exe -o analysis -a C:\Trace\SQL2008Source\Trace.trc -b C:\ Trace\SQL2014Trace\Trace.trc -r upgrade20082014 -s localhost -e`

## <a name="next-steps"></a>次のステップ

DEA とデモンストレーションを 19 分については、次のビデオをご覧ください。

> [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

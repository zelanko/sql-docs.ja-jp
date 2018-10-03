---
title: Azure データ Studio の SQL Server Profiler の拡張機能 |Microsoft Docs
description: Azure Data Studio 用 SQL Server Profiler 拡張機能 (プレビュー)
ms.custom: tools|sos
ms.date: 09/24/2018
ms.reviewer: alayu; sstein
ms.prod: sql
ms.prod_service: sql-tools
ms.topic: conceptual
author: yualan
ms.author: alayu
manager: craigg
ms.openlocfilehash: f92391c3d18648555a0c65d55915bf6752c195b8
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "48039004"
---
# <a name="sql-server-profiler-extension-preview"></a>SQL Server Profiler の拡張機能 (プレビュー)

SQL Server Profiler の拡張機能 (プレビュー) は、XEvents を使用してビルドを除く SQL Server Management Studio (SSMS) の Profiler のような単純な SQL Server トレース ソリューションを提供します。 SQL Server Profiler は非常に簡単に使用であり、最も一般的なトレースの構成に適した既定値を使います。 UX は、イベントを参照して、関連する TRANSACT-SQL (T-SQL) テキストを表示するために最適化されます。 Azure Data Studio の SQL Server Profiler は、使いやすいエクスペリエンスで T-SQL の実行アクティビティを収集するための適切な既定値も想定しています。 この拡張機能は現在プレビュー段階です。

**一般的な SQL Profiler の用途:**

- 問題の原因を特定するため、問題の発生したクエリを順次実行する。
- 実行速度の遅いクエリを検出し、その原因を診断する。
- 一連の問題を引き起こしている TRANSACT-SQL ステートメントをキャプチャします。
- ワークロードをチューニングする SQL Server のパフォーマンスを監視します。
- 問題を診断するために、さまざまなパフォーマンス カウンターの関連を調べる。


## <a name="install-the-sql-server-profiler-extension"></a>SQL Server Profiler 拡張機能をインストールします。

1. 拡張機能マネージャーを開き、使用可能な拡張機能にアクセスするには、拡張機能 アイコンを選択するか、**ビュー**メニューの**拡張**を選択します。
2. 詳細を表示する使用可能な拡張機能を選択します。

   ![プロファイラーの拡張機能マネージャー](media/extensions/sql-server-profiler-extension/profiler-extension.png)

1. 必要な拡張機能を選択し、**インストール**します。
2. **再読み込み**を選択して拡張機能を有効にします(初めて拡張機能をインストールするときのみ必要です)。

## <a name="start-profiler"></a>Profiler を起動します。

1. Profiler を起動するには、[サーバー] タブで、サーバーへの接続をまず確認します。
2. 接続を確立した後に「 **Alt + P** Profiler を起動します。
3. Profiler を起動する入力**Alt + s.** 拡張イベントの表示を開始できます。
    ![プロファイラーの拡張機能マネージャー](media/extensions/sql-server-profiler-extension/view-profiler.png)    
1. Profiler を停止する次のように入力します**Alt + s。** このホットキー表示が切り替わります。

## <a name="next-steps"></a>次の手順

Profiler と拡張イベントの詳細については、次を参照してください。[拡張イベント](https://docs.microsoft.com/sql/relational-databases/extended-events/extended-events)します。






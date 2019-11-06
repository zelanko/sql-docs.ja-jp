---
title: SQL Server のアップグレード アシスタントで実験をデータベース内分析レポートの表示
description: データベース実験アシスタント分析レポートの表示
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
ms.openlocfilehash: 066297daff3393304b83b77238277f873e1c97fb
ms.sourcegitcommit: b2464064c0566590e486a3aafae6d67ce2645cef
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/15/2019
ms.locfileid: "68050447"
---
# <a name="view-analysis-reports-in-database-experimentation-assistant"></a>データベース実験アシスタント分析レポートの表示

したら[分析レポートを作成](database-experimentation-assistant-create-report.md)でデータベース実験アシスタント (DEA)、レポートを表示し、A によって提供されるパフォーマンスの洞察を得るには、この記事で説明されている手順を完了する/B テストします。

## <a name="select-a-server"></a>サーバーを選択します。

DEA では、メニュー アイコンを選択します。 展開されたメニューで、次のように選択します。**分析レポート**分析レポート ウィンドウを開いてチェックリストのアイコンの横にあります。

**分析レポート**、分析データベースが SQL Server を実行しているコンピューターの名前を入力します。 **[接続]** を選択します。 

![既存のレポートへの接続します。](./media/database-experimentation-assistant-view-report/dea-view-report-connect.png)

すべての依存関係が不足している場合、**の前提条件**ページによってインストールへのリンクを求められます。 前提条件をインストールし、**もう一度お試し**します。

![前提条件 ページ](./media/database-experimentation-assistant-view-report/dea-view-report-prereq.png)

## <a name="select-an-analysis-report-to-view"></a>表示する分析レポートを選択します。

分析レポートの一覧で、レポートを開きますをダブルクリックします。

![既存のレポートを表示します。](./media/database-experimentation-assistant-view-report/dea-view-report-view-existing.png)

このグラフの例で示すように、どの程度、ワークロードが表される、洞察を取得できます。

![ワークロード Rep グラフ](./media/database-experimentation-assistant-view-report/dea-view-report-workload-compare.png)

## <a name="view-and-understand-the-analysis-report"></a>表示し、分析レポートを理解します。

このセクションでは、分析レポートについて説明します。

### <a name="query-categories"></a>クエリのカテゴリ

そのカテゴリに分類するクエリのみを表示する左の円グラフの各種のスライスを選択します。

![レポートの円スライス](./media/database-experimentation-assistant-view-report/dea-view-report-pie-slices.png)

- **クエリを低下**:も A から b の方がクエリ  
- **エラー**:インスタンス A ではなくインスタンス B には、エラーを表示するクエリ  
- **クエリの改善**:インスタンス A に向上よりも、インスタンス B でを実行したクエリ  
- **中間クエリ**:中間のパフォーマンスを持つクエリを変更します。  
- **同じ**:これでパフォーマンスままで、A と B のインスタンス間でのクエリ

### <a name="individual-query-drill-down"></a>個々 のクエリのドリルダウン

特定のクエリに関する詳細な情報を表示するクエリ テンプレートへのリンクを選択することができます。

![クエリのドリルダウン](./media/database-experimentation-assistant-view-report/dea-view-report-drilldown.png)

クエリの概要の比較を開くには特定のクエリを選択します。

![比較の概要](./media/database-experimentation-assistant-view-report/dea-view-report-comparison-summary.png)

クエリが実行された A と B のインスタンスを確認できます。 クエリのテンプレートを確認することもできます。 テーブルには、A と B のインスタンスに固有のクエリ情報が表示されます。

### <a name="error-queries"></a>エラーのクエリ

比較の概要レポートが展開可能な**エラー情報**と**クエリ計画情報**セクション。 セクションでは、エラーを表示する両方のインスタンスの情報を検討してください。

この種のエラーを表示するエラー (赤) 円を選択します。
- **既存のエラー**:A. に含まれていたエラー
- **新しいエラー**:B. に含まれていたエラー
- **エラーを解決**:A が B でないエラー

![エラー グラフ](./media/database-experimentation-assistant-view-report/dea-view-report-error-charts.png)

## <a name="next-steps"></a>次のステップ

- コマンド プロンプトで、分析レポートを生成する方法については、次を参照してください。[コマンド プロンプトで実行](database-experimentation-assistant-run-command-prompt.md)します。

- DEA とデモンストレーションを 19 分については、次のビデオをご覧ください。

  > [!VIDEO https://channel9.msdn.com/Shows/Data-Exposed/Introducing-the-Database-Experimentation-Assistant/player]

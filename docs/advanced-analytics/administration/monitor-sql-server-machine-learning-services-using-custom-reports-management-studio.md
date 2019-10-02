---
title: SSMS でカスタムレポートを使用して Python と R スクリプトの実行を監視する
ms.prod: sql
ms.technology: machine-learning
ms.date: 09/17/2019
ms.topic: conceptual
author: dphansen
ms.author: davidph
monikerRange: '>=sql-server-2016||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 549cdcd35b939b2247b14817271e3d1063fab1e0
ms.sourcegitcommit: fd3e81c55745da5497858abccf8e1f26e3a7ea7d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2019
ms.locfileid: "71714396"
---
# <a name="monitor-python-and-r-script-execution-using-custom-reports-in-sql-server-management-studio"></a>SQL Server Management Studio でカスタムレポートを使用して Python および R スクリプトの実行を監視する
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

SQL Server Management Studio (SSMS) のカスタムレポートを使用して、外部スクリプト (Python と R) の実行、使用されたリソース、問題の診断、SQL Server Machine Learning Services のパフォーマンスの調整を監視します。

これらのレポートでは、次のような詳細情報を表示できます。

- アクティブな Python または R セッション
- インスタンスの構成設定
- Machine learning ジョブの実行統計
- R Services の拡張イベント
- 現在のインスタンスにインストールされている Python または R パッケージ

この記事では、SQL Server Machine Learning Services に提供されているカスタムレポートをインストールして使用する方法について説明します。

SQL Server Management Studio のレポートの詳細については、「 [Management Studio のカスタムレポート](../../ssms/object/custom-reports-in-management-studio.md)」を参照してください。

## <a name="how-to-install-the-reports"></a>レポートのインストール方法

レポートは SQL Server Reporting Services を使用して設計されていますが、SQL Server Management Studio から直接使用できます。 Reporting Services が SQL Server インスタンスにインストールされている必要はありません。

これらのレポートを使用するには、次の手順を実行します。

1. GitHub から SQL Server Machine Learning Services 用の[SSMS カスタムレポート](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)をダウンロードします。

2. Management Studio へのレポートのコピー

    1. SQL Server Management Studio で使用されるカスタム レポート フォルダーを見つけます。 既定では、カスタムレポートは次のフォルダーに格納されます ( **user_name**は Windows ユーザー名)。

        `C:\Users\user_name\Documents\SQL Server Management Studio\Custom Reports`

       別のフォルダーを指定することも、サブフォルダーを作成することもできます。

    2. \* をコピーします。カスタムレポートフォルダーにダウンロードした RDL ファイル。

3. でレポートを実行する Management Studio

    1. Management Studio で、レポートを実行するインスタンスの **[データベース]** ノードを右クリックします。

    2. **[レポート]** 、 **[カスタム レポート]** の順にクリックします。

    3. **[ファイルを開く]** ダイアログ ボックスで、カスタム レポート フォルダーを見つけます。

    4. ダウンロードした RDL ファイルを選択し、 **[開く]** をクリックします。

## <a name="reports"></a>[レポート]

[GitHub の SSMS カスタムレポートリポジトリ](https://github.com/Microsoft/sql-server-samples/tree/master/samples/features/machine-learning-services/ssms-custom-reports)には、次のレポートが含まれています。

| レポート | 説明 |
|-|-|
| Active sessions | 現在 SQL Server インスタンスに接続されていて、Python または R スクリプトを実行しているユーザー。 |
| 構成 | Python または R ランタイムの Machine Learning Services とプロパティのインストール設定。 |
| インスタンスの構成 | Machine Learning Services を構成します。 |
| 実行の統計 | Machine Learning services の実行の統計。 たとえば、外部スクリプト実行の合計数と並列実行数を取得できます。 |
| 拡張イベント | 外部スクリプトの実行に関する洞察を得るために使用できる拡張イベント。 |
| パッケージ | SQL Server インスタンスにインストールされている R または Python のパッケージと、バージョンや名前などのプロパティを一覧表示します。 |
| Resource Usage | SQL Server の CPU、メモリ、IO 消費量、および外部スクリプトの実行を表示します。 外部リソースプールのメモリ設定を表示することもできます。 |

## <a name="next-steps"></a>次の手順

- [動的管理ビュー (Dmv) を使用して SQL Server Machine Learning Services を監視する](monitor-sql-server-machine-learning-services-using-dynamic-management-views.md)
- [R Services の拡張イベント](../r/extended-events-for-sql-server-r-services.md)

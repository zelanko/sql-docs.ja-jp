---
title: Machine learning のトラブルシューティングと FAQ
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
ms.openlocfilehash: 0cd9b4808d361cdbfa661feb31134da46baec3de
ms.sourcegitcommit: c1382268152585aa77688162d2286798fd8a06bb
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/19/2019
ms.locfileid: "68344994"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>SQL Server での機械学習のトラブルシューティング
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

このページは、既知の問題に対処するための出発点として使用します。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 Machine Learning Services (R および Python)

## <a name="known-issues"></a>既知の問題

次の記事では、現在および以前のリリースに関する既知の問題について説明します。

+ [R Services の既知の問題](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>システム情報を収集する方法

エラーが発生した場合、または環境内の問題を理解する必要がある場合は、関連する情報を体系的に収集することが重要です。 次の記事では、セルフヘルプのトラブルシューティング、またはテクニカルサポートの要求を容易にする情報の一覧を示します。

+ [Machine learning のトラブルシューティングのためのデータ収集](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>セットアップと構成のガイド

SQL Server で machine learning を設定していない場合、または機能を追加する場合は、ここから開始します。

+ [SQL Server 2017 Machine Learning Services (データベース内) のインストール](install/sql-machine-learning-services-windows-install.md)
+ [SQL Server 2017 Machine Learning Server (スタンドアロン) のインストール](install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Services (データベース内) のインストール](install/sql-r-services-windows-install.md)
+ [SQL Server 2016 R Server (スタンドアロン) のインストール](install/sql-r-standalone-windows-install.md)
+ [コマンドプロンプトのセットアップ](install/sql-ml-component-commandline-install.md)
+ [オフラインのセットアップ (インターネットなし)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>構成

次の記事には、既定の情報と、インスタンスで machine learning の構成をカスタマイズする方法に関する情報が含まれています。

+ [SQL Server Machine Learning Services での外部スクリプトの同時実行のスケーリング](administration/modify-user-account-pool.md)   
+ [高度な分析拡張機能の構成と管理](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [リソースプールを作成する方法](r/how-to-create-a-resource-pool-for-r.md)
+ [R ワークロードの最適化](r/operationalizing-your-r-code.md)

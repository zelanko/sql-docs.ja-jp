---
title: トラブルシューティングと machine learning - SQL Server Machine Learning Services の FAQ
ms.prod: sql
ms.technology: machine-learning
ms.date: 05/31/2018
ms.topic: conceptual
author: dphansen
ms.author: davidph
manager: cgronlun
ms.openlocfilehash: 4a62dd0710a97a33f5a4703f194df2c6bcef2a54
ms.sourcegitcommit: 2827d19393c8060eafac18db3155a9bd230df423
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/27/2019
ms.locfileid: "58511889"
---
# <a name="troubleshoot-machine-learning-in-sql-server"></a>SQL Server での machine learning をトラブルシューティングします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

開始点としてこのページを使用して、既知の問題の全体を操作します。

**適用対象:** SQL Server 2016 R Services、SQL Server 2017 の Machine Learning サービス (R および Python)

## <a name="known-issues"></a>既知の問題

次の記事では、現在と以前のリリースに関する既知の問題について説明します。

+ [R Services の既知の問題](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)

## <a name="how-to-gather-system-information"></a>システム情報を収集する方法

エラーが発生したするか、または環境内で問題を理解する必要がある場合は、体系的に関連する情報を収集することが重要です。 次の記事では、テクニカル サポートをトラブルシューティングするには、セルフヘルプを容易にする情報または要求の一覧を示します。

+ [Machine learning のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>セットアップと構成ガイド

SQL Server を使用した machine learning を設定していない場合、または機能を追加する場合は、ここから開始します。

+ [SQL Server 2017 Machine Learning Services (In-database) をインストールします。](install/sql-machine-learning-services-windows-install.md)
+ [SQL Server 2017 の Machine Learning Server (スタンドアロン) のインストールします。](install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Services (In-database) をインストールします。](install/sql-r-services-windows-install.md)
+ [SQL Server 2016 R Server (スタンドアロン) のインストールします。](install/sql-r-standalone-windows-install.md)
+ [コマンド プロンプトのセットアップ](install/sql-ml-component-commandline-install.md)
+ [オフラインのセットアップ (インターネットなし)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>構成

次の記事には、machine learning のインスタンス上の構成をカスタマイズする方法と、既定値についてが含まれます。

+ [SQL Server Machine Learning Services での外部スクリプトの同時実行のスケール](administration/modify-user-account-pool.md)   
+ [構成し、高度な分析拡張機能の管理](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [リソース プールを作成する方法](r/how-to-create-a-resource-pool-for-r.md)
+ [R のワークロードの最適化](r/operationalizing-your-r-code.md)

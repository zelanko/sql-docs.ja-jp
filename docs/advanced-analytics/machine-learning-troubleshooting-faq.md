---
title: トラブルシューティングと SQL Server での機械学習のよく寄せられる質問 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 80d153baed382c95c85793e1605b700c2719e13c
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="troubleshoot-machine-learning"></a>機械学習をトラブルシューティングします。
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、セットアップ ガイド、既知の問題、およびリリース ノートにトラブルシューティングへのリンクを提供します。 この記事から、SQL Server の machine learning ソリューションのパフォーマンスの最適化に関するアドバイスを提供する他のアーティクルがリンクされています。

トラブルシューティングのための既知の問題、一般的なセットアップの質問、およびプロシージャを検索するための開始点としてこのページを使用できます。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス (R および Python)

## <a name="known-issues"></a>既知の問題

次の記事では、現在のリリースの既知の問題を一覧表示または以前のリリースでの問題について説明。

+ [R Services の既知の問題](../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)
+ [SQL Server 2016 リリース ノート](../sql-server/sql-server-2016-release-notes.md)
+ [SQL Server 2017 リリース ノート](../sql-server/sql-server-2017-release-notes.md)

## <a name="troubleshooting-prerequisites"></a>前提条件のトラブルシューティング

エラーが発生した場合、または環境内で発生する問題を理解する必要がある場合は、体系的に関連する情報を収集することが重要です。 この情報には、バージョン、エディション、セキュリティ コンテキスト、および実行コンテキストが含まれています。

次の記事では、テクニカル サポートについては、トラブルシューティング、セルフヘルプを容易にするか、要求の一覧を提供します。

+ [機械学習のトラブルシューティングのためのデータの収集](data-collection-ml-troubleshooting-process.md)

## <a name="setup-and-configuration-guides"></a>セットアップおよび構成ガイド

ここから始めてください機械学習と SQL Server を設定していない場合、または機能を追加する場合。

+ [SQL Server 2017 Machine Learning Services (In-database) のインストールします。](install/sql-machine-learning-services-windows-install.md)
+ [SQL Server 2017 Machine Learning サーバー (スタンドアロン) のインストールします。](install/sql-machine-learning-standalone-windows-install.md)
+ [SQL Server 2016 R Services (In-database) のインストールします。](install/sql-r-services-windows-install.md)
+ [SQL Server 2016R Server (スタンドアロン) のインストールします。](install/sql-r-standalone-windows-install.md)
+ [コマンド プロンプトのセットアップ](install/sql-ml-component-commandline-install.md)
+ [オフラインのセットアップ (インターネットなし)](install/sql-ml-component-install-without-internet-access.md)

### <a name="configuration"></a>構成

次の記事には、機械学習のインスタンス上の構成をカスタマイズする方法と既定値は、情報が含まれています。

+ [SQL Server R Services のユーザー アカウント プールを変更します。](r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [構成および高度な分析拡張機能を管理します。](r/configure-and-manage-advanced-analytics-extensions.md)  
+ [リソース プールを作成する方法](r/how-to-create-a-resource-pool-for-r.md)
+ [R のワークロードの最適化](r/operationalizing-your-r-code.md)

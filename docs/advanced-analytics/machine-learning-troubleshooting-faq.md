---
title: "トラブルシューティングと SQL Server での機械学習のよく寄せられる質問 |Microsoft ドキュメント"
ms.custom: 
ms.date: 06/16/2017
ms.prod: machine-learning-services
ms.prod_service: machine-learning-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: sql
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 7c0c86caa318176d1bff25e5562db630a163d0d7
ms.sourcegitcommit: 23433249be7ee3502c5b4d442179ea47305ceeea
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/20/2017
---
# <a name="troubleshoot-machine-learning"></a>機械学習をトラブルシューティングします。

この記事では、マシン学習機能によって SQL Server のセットアップと構成に関連するトラブルシューティングの情報を提供します。 情報には、セットアップ ガイド、既知の問題、およびリリース ノートへのリンクが含まれています。 この記事から、SQL Server の machine learning ソリューションのパフォーマンスの最適化に関するアドバイスを提供する他のアーティクルがリンクされています。

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

+ [R Services または R で Machine Learning のサービスのセットアップします。](../advanced-analytics/r/set-up-sql-server-r-services-in-database.md)
+ [Python の Machine Learning のサービスを設定します。](../advanced-analytics/python/setup-python-machine-learning-services.md)
+ [セットアップに関する FAQ](../advanced-analytics/r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [SqlBindR を使用して R services のインスタンスをアップグレードするには](../advanced-analytics/r/use-sqlbindr-exe-to-upgrade-an-instance-of-sql-server.md)

次の記事では、SQL Server の学習機能をコンピューターのオフラインのセットアップに必要な追加の手順について説明します。

+ [R Services の無人インストール](../advanced-analytics/r/unattended-installs-of-sql-server-r-services.md) 
+ [Python の Machine Learning のサービスの無人インストール](../advanced-analytics/python/unattended-installs-of-sql-server-python-services.md)

機械学習のインターネット接続がないコンピューターの機能をインストールする必要がある場合は、この記事の内容のリンクを使用して、セットアップを開始する前に、R、Python のコンポーネントをダウンロードします。

+ [インターネットへのアクセスなしで Machine Learning コンポーネントをインストールする](../advanced-analytics/r/installing-ml-components-without-internet-access.md)

### <a name="configuration"></a>構成

次の記事には、機械学習のインスタンス上の構成をカスタマイズする方法と既定値は、情報が含まれています。

+ [SQL Server R Services のユーザー アカウント プールを変更します。](../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)  
+ [構成および高度な分析拡張機能を管理します。](../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)  
+ [リソース プールを作成する方法](r/how-to-create-a-resource-pool-for-r.md)
+ [R のワークロードの最適化](r/operationalizing-your-r-code.md)

## <a name="related-tools-and-services"></a>関連ツールとサービス

+ [Microsoft Machine Learning Server のスタンドアロンをセットアップします。](../advanced-analytics/r/create-a-standalone-r-server.md)
+ [Azure VM での R サーバーをセットアップします。](../advanced-analytics/r/provision-the-r-server-only-sql-server-2016-enterprise-vm-on-azure.md)
+ [Windows 用の R Server をインストールします。](https://msdn.microsoft.com/microsoft-r/rserver-install-windows)
+ [R Tools for Visual Studio を入手します。](https://www.visualstudio.com/vs/rtvs/)

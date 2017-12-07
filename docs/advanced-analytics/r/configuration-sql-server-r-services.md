---
title: "構成と管理 |Microsoft ドキュメント"
ms.custom: 
ms.date: 05/31/2016
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e0fd4554-60c6-4181-ac4c-2e366fb434f6
caps.latest.revision: "7"
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 847ece72abb792d12294c83cace7b26511dafffe
ms.sourcegitcommit: 531d0245f4b2730fad623a7aa61df1422c255edc
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/01/2017
---
# <a name="configuration-and-management"></a>構成と管理

この記事では、これらの製品と SQL Server の machine learning サービスをサポートするためにサーバーを構成する方法に関する詳細情報へのリンクを示します。

+ SQL Server 2016 R Services (In-database)
+ SQL Server 2017 Machine Learning Services (In-database)

> [!NOTE]
> 
> このコンテンツは、R 言語のみをサポートする SQL Server 2016 リリースでは、もともと記述されています。
> 
> SQL Server の 2017 で Python が追加されましたが、基になるアーキテクチャとサービス フレームワークは同じのサポートします。 そのため、セキュリティ、メモリ、リソース統制および R スクリプトの場合と同様に Python スクリプトの実行をサポートするその他のオプションを構成することができます。
> 
> ただし、ため Python ワークロードはまだ使用できませんの Python は潜在的な最適化に関する詳細情報、新しい機能をサポートします。 後で確認してください。

## <a name="r-package-management"></a>R パッケージの管理

これらのトピックでは、SQL Server インスタンスに新しい R パッケージをインストール、R パッケージのライブラリの管理、およびデータベースの復元後にパッケージのライブラリを復元する方法について説明します。

+ [R パッケージのインストールと管理](installing-and-managing-r-packages.md)
+ [新しい R パッケージをインストールします。](install-additional-r-packages-on-sql-server.md)
+ [データベース ロールを使用してインスタンスのパッケージの管理を有効にします。](r-package-how-to-enable-or-disable.md)
+ [MiniCRAN を使用して、ローカルのパッケージ リポジトリを作成します。](create-a-local-package-repository-using-minicran.md)
+ [R パッケージが SQl Server にインストールされているかを決定します。](determine-which-packages-are-installed-on-sql-server.md)
+ [SQL Server およびファイル システムとの間の同期の R パッケージ](package-install-uninstall-and-sync.md)
+ [ユーザーのライブラリでインストールされている R パッケージ](packages-installed-in-user-libraries.md)

## <a name="service-configuration"></a>サービスの構成

これらのトピックでは、拡張サービスに関連付けられているセキュリティ プリンシパルを管理する方法と、基になるサービス アーキテクチャに変更を加える方法について説明します。

+ [セキュリティに関する考慮事項](security-considerations-for-the-r-runtime-in-sql-server.md)
+ [SQL Server R サービスのユーザー アカウント プールを変更する](../../advanced-analytics/r/modify-the-user-account-pool-for-sql-server-r-services.md)
+ [Advanced Analytics Extensions の構成と管理](../../advanced-analytics/r/configure-and-manage-advanced-analytics-extensions.md)
+ [データベース ロールを使用してインスタンスのパッケージの管理を有効にします。](r-package-how-to-enable-or-disable.md)
+ [R Services のパフォーマンス チューニング](sql-server-r-services-performance-tuning.md)

## <a name="resource-governance"></a>リソース管理

これらのトピックでは、Enterprise Edition でリソース ガバナー機能ボタンを使用して R または Python のジョブのリソース管理を実装する方法について説明します。

+ [R Services のリソース管理](../../advanced-analytics/r/resource-governance-for-r-services.md)
+ [R のリソース プールを作成する方法](../../advanced-analytics/r/how-to-create-a-resource-pool-for-r.md)

参照してください。

+ [SSMS のカスタム レポートを使用するモニター R](monitor-r-services-using-custom-reports-in-management-studio.md)

## <a name="initial-setup"></a>初期セットアップ

初期セットアップと構成に関連する追加のヘルプは、次のトピックではあります。

+ [アップグレードとインストールに関してよく寄せられる質問](../r/upgrade-and-installation-faq-sql-server-r-services.md)
+ [セキュリティに関する考慮事項](../r/security-considerations-for-the-r-runtime-in-sql-server.md)
+ [R Services の既知の問題](../../advanced-analytics/known-issues-for-sql-server-machine-learning-services.md)


---
title: 管理、および SQL Server の machine learning ソリューションの監視 |Microsoft ドキュメント
ms.prod: sql
ms.technology: machine-learning
ms.date: 04/15/2018
ms.topic: conceptual
author: HeidiSteen
ms.author: heidist
manager: cgronlun
ms.openlocfilehash: 4806224a1606fff58f63f6083fa577aa4066c795
ms.sourcegitcommit: 808d23a654ef03ea16db1aa23edab496b73e5072
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/04/2018
ms.locfileid: "34585704"
---
# <a name="managing-and-monitoring-machine-learning-solutions"></a>管理と machine learning のソリューションの監視
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-winonly](../../includes/appliesto-ss-xxxx-xxxx-xxx-md-winonly.md)]

この記事では、R、Python のソリューションで作業を開始する必要があるデータベース管理者に関連する SQL Server マシン ラーニング サービスの機能について説明します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="security"></a>Security

データベース管理者は、データ サイエンティストは、さまざまなレポート開発者、ビジネス アナリスト、およびビジネス データのユーザーにだけでなく、データ アクセスを提供する必要があります。 R (および Python ようになりました) の SQL Server に統合は、データ サイエンスの役割をサポートする、データベース管理者に多くのメリットを提供します。

+ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のアーキテクチャは、データベースのセキュリティを保護し、データベース インスタンスの運用から R セッションの実行を分離します。

+ R スクリプトを実行するアクセス許可を持つユーザーを指定し、R ジョブで使用されるデータが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に定義されている同じセキュリティ ロールを使用して管理されるようにします。

+ データベース管理者は、ロールを使用して、R パッケージのインストール、および R と Python スクリプトの実行を管理することができます。

詳細については、次のリソースをご覧ください。

+ [SQL Server での R ランタイムのセキュリティに関する考慮事項](../../advanced-analytics/r/security-considerations-for-the-r-runtime-in-sql-server.md)

+ [R のセキュリティの概要](../r/security-overview-sql-server-r.md)

+ [Python のセキュリティの概要](../python/security-overview-sql-server-python-services.md)

+ [SQL Server で既定の R、Python のパッケージ](installing-and-managing-r-packages.md)

## <a name="configuration-and-management"></a>構成と管理

データベース管理者は競合するプロジェクトと優先順位を 1 箇所の連絡先 (データベース サーバー) に統合する必要があります。 運用とレポートのデータ ストアの正常性を維持しながらの分析をサポートする必要があります。 機械学習の SQL Server との統合は、データベース管理者は、データ サイエンス用の効率的なインフラストラクチャの展開において重要な役割をしだいに機能を数多くのメリットを提供します。

+ R、Python のセッションは、サーバーが引き続き、外部スクリプトの実行時に問題がある場合でも、通常どおり実行できるように別のプロセスで実行されます。

+ 低い特権の物理的なユーザー アカウントが含まれてし、外部のスクリプト活動を分離するために使用されます。

+ DBA は、標準の SQL Server リソースの管理ツールを使用して、サーバーの全体的なパフォーマンスが損なわれない大規模な計算を防ぐために、R ランタイムに割り当てられたリソースの量を制御します。

詳細については、次のリソースをご覧ください。

+ [R Services のリソース管理](../r/resource-governance-for-r-services.md)

+ [構成および Advanced Analytics Extensions の管理](../r/configure-and-manage-advanced-analytics-extensions.md)

---
title: "管理と監視 machine learning ソリューション |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 07/26/2016
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f22a-190f-4a28-9088-98a843cd5db2
caps.latest.revision: 15
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 388104730e6d8839843ce61d1c142449d9b02707
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="managing-and-monitoring-machine-learning-solutions"></a>管理と machine learning のソリューションの監視

この記事では、R、Python のソリューションで作業を開始する必要があるデータベース管理者に関連する SQL Server マシン ラーニング サービスの機能について説明します。

**適用されます:** SQL Server 2016 の R Services、SQL Server 2017 機械学習のサービス

## <a name="security"></a>セキュリティ

データベース管理者は、データ サイエンティストは、さまざまなレポート開発者、ビジネス アナリスト、およびビジネス データのユーザーにだけでなく、データ アクセスを提供する必要があります。 R (および Python ようになりました) の SQL Server に統合は、データ サイエンスの役割をサポートする、データベース管理者に多くのメリットを提供します。

+ [!INCLUDE[rsql_productname](../../includes/rsql-productname-md.md)] のアーキテクチャは、データベースのセキュリティを保護し、データベース インスタンスの運用から R セッションの実行を分離します。

+ R スクリプトを実行するアクセス許可を持つユーザーを指定し、R ジョブで使用されるデータが、 [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]に定義されている同じセキュリティ ロールを使用して管理されるようにします。

+ データベース管理者は、ロールを使用して、R パッケージのインストール、および R と Python スクリプトの実行を管理することができます。

詳細については、次のリソースをご覧ください。

+ [SQL Server での R ランタイムのセキュリティに関する考慮事項](../../advanced-analytics/r/security-considerations-for-the-r-runtime-in-sql-server.md)

+ [R のセキュリティの概要](../r/security-overview-sql-server-r.md)

+ [Python のセキュリティの概要](../python/security-overview-sql-server-python-services.md)

+ [R パッケージのインストールと管理](../../advanced-analytics/r-services/installing-and-managing-r-packages.md)

## <a name="configuration-and-management"></a>構成と管理

データベース管理者は競合するプロジェクトと優先順位を 1 箇所の連絡先 (データベース サーバー) に統合する必要があります。 運用とレポートのデータ ストアの正常性を維持しながらの分析をサポートする必要があります。 機械学習の SQL Server との統合は、データベース管理者は、データ サイエンス用の効率的なインフラストラクチャの展開において重要な役割をしだいに機能を数多くのメリットを提供します。

+ R、Python のセッションは、サーバーが引き続き、外部スクリプトの実行時に問題がある場合でも、通常どおり実行できるように別のプロセスで実行されます。

+ 低い特権の物理的なユーザー アカウントが含まれてし、外部のスクリプト活動を分離するために使用されます。

+ DBA は、標準の SQL Server リソースの管理ツールを使用して、サーバーの全体的なパフォーマンスが損なわれない大規模な計算を防ぐために、R ランタイムに割り当てられたリソースの量を制御します。

詳細については、次のリソースをご覧ください。

+ [R Services のリソース管理](../r/resource-governance-for-r-services.md)

+ [R Services の監視](../r/monitoring-r-services.md)

+ [構成および Advanced Analytics Extensions の管理](../r/configure-and-manage-advanced-analytics-extensions.md)


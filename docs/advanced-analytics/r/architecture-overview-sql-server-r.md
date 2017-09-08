---
title: "アーキテクチャの概要 (SQL Server R Services) | Microsoft Docs"
ms.custom: 
ms.date: 07/11/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- r-services
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6c4a4f66-ea3e-4a73-acf2-6c8aeafc94b0
caps.latest.revision: 9
author: jeannt
ms.author: jeannt
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 346dd5d2153a9a318e7bc68d73283278b3a13512
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="architecture-overview-for-r-in-sql-server"></a>SQL Server で R のアーキテクチャの概要

このセクションでは、SQL Server 2017 Machine Learning Services および SQL Server 2016 の R Services のアーキテクチャの概要を説明します。

拡張可能アーキテクチャのアーキテクチャが同一または SQL Server 2016 の非常に類似した」および「SQL Server 2017 リリースでは、および R Python のも同様です。 ただし、ディスカッションを簡略化について説明のみ、R コンポーネントを外部スクリプトの実行、セキュリティ、R ライブラリ、およびオープン ソース r です。 との相互運用をサポートする SQL Server データベース エンジンに追加された新しいコンポーネントを含む

詳細については、各セクションのリンクで提供されます。

## <a name="r-interoperability"></a>R の相互運用性

SQL Server 2016 の R Services と SQL Server 2017 Machine Learning Services (In-database) の両方は、Microsoft によって提供される分散または並列処理をサポートするパッケージと同様に、R のオープン ソース ディストリビューションをインストールします。

このアーキテクチャでは、SQL Server から別のプロセスで R を使用して外部のスクリプトを実行するよう設計されています。 現在の R ユーザーは R コードを移植し、比較的軽微な修正だけで T-SQL で実行できます。

ソリューションを縮小または並列処理を使用して、使用することお勧め、 [RevoScaleR](https://docs.microsoft.com/r-server/r-reference/revoscaler/revoscaler)パッケージまたは[MicrosoftML](https://docs.microsoft.com/r-server/r-reference/microsoftml/microsoftml-package)パッケージです。 これらのライブラリによって提供される分散コンピューティング機能を使用しない場合は、SQL Server のコンテキストで R コードを実行してもいくつかのパフォーマンスの向上を取得できます。

インストールされている外部のスクリプト コンポーネントまたは R と SQL server との対話の詳細については、次を参照してください[R の相互運用性。](../../advanced-analytics/r/r-interoperability-in-sql-server.md)

## <a name="components-to-support-r-integration"></a>R 統合をサポートするコンポーネント

SQL Server 2016 で導入された extensibility framework は SQL Server 2017 で継続しています。 拡張機能のコンポーネントは、R、R とデータベース エンジンの間でデータを渡すと、R ジョブに必要な並列タスクを調整するための外部のランタイムを起動する SQL Server によって使用されます。

これらの追加コンポーネントの役割は、データ交換の速度と圧縮では、セキュリティで保護された、パフォーマンスの高いプラットフォームを提供する外部スクリプトの実行中に改善するためです。

ように、R をサポートするコンポーネントの詳細については、[!INCLUDE[rsql_launchpad_md](../../includes/rsql-launchpad-md.md)]と RLauncher を参照してください[新しいコンポーネント](../../advanced-analytics/r/new-components-in-sql-server-to-support-r.md)です。

## <a name="security"></a>セキュリティ

Machine Learning のサービスまたは SQL Server R Services を使用して R コードを実行すると、セキュリティと管理容易性を提供する、SQL Server プロセスの外部のすべての R スクリプトが実行されます。 このようなプロセスの分離は、ストアド プロシージャの一部として、R スクリプトを実行またはリモート コンピューターから SQL Server コンピューターのジョブへの接続し、計算コンテキストとしてサーバーを使用するジョブを開始するかどうかに関係なく true を保持します。

SQL Server は、ジョブのすべての要求を途中受信、タスク、および Windows ジョブ オブジェクトを使用してデータをセキュリティで保護し、SQL Server ユーザー アカウントとデータベース ロールを使用してデータに対するセキュリティを保持します。

データは、テーブル、データベース、およびインスタンス レベルでの SQL Server のセキュリティを適用することで、コンプライアンスの境界内に保持されます。 データベース管理者は、R ジョブを実行する権限を持っているユーザーと、インストールしたり、R パッケージを共有する権限を持っているユーザーを制御できます。 管理者もリモートまたはローカルのユーザーが R スクリプトの使用状況を監視し、監視および管理できます消費するリソース。

## <a name="next-steps"></a>次の手順

[R 統合をサポートするコンポーネント](new-components-in-sql-server-to-support-r.md)

[R の相互運用性](r-interoperability-in-sql-server.md)

[セキュリティの概要](security-overview-sql-server-r.md)

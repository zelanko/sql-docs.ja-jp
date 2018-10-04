---
title: Linux 上の SQL Server レプリケーション |Microsoft Docs
description: この記事では、Linux に SQL Server レプリケーションについて説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 03/20/2018
ms.topic: article
ms.prod: sql-non-specified
ms.prod_service: database-engine
ms.custom: sql-linux
ms.technology: database-engine
ms.assetid: ''
ms.workload: On Demand
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: a6c4bad8947944d59208a0516e5950d36f64a84e
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47734130"
---
# <a name="sql-server-replication-on-linux"></a>Linux 上の SQL Server レプリケーション

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] 紹介用の SQL Server レプリケーション Linux 上の SQL Server のインスタンス。

Linux SQL Server Management Studio (SSMS) でのレプリケーションを構成[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)します。

SQL Server のインスタンスは、任意のレプリケーション ロールに参加できます。

* パブリッシャー
* ディストリビューター
* サブスクライバー (Subscriber)

レプリケーション スキーマがオペレーティング システム プラットフォームを一致し、混在させることができます。 たとえば、レプリケーション スキーマはパブリッシャーおよびディストリビューター、Linux 上の SQL Server のインスタンスを使用することができ、サブスクライバーは、Windows 上の SQL Server のインスタンスを含めることができます。

Linux 上の SQL Server インスタンスは、任意の種類のレプリケーションに参加できます。

* トランザクション
* Merge
* スナップショット

レプリケーションの詳細については、次を参照してください。 [SQL Server レプリケーションのドキュメント](../relational-databases/replication/sql-server-replication.md)します。

## <a name="supported-features"></a>サポートされる機能

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)]次のレプリケーション機能がサポートされています。

* スナップショット レプリケーション
* トランザクション レプリケーション
* マージ レプリケーション
* ピア ツー ピア レプリケーション
* 既定以外のポートを使用したレプリケーション <!--Add link to explanation-->
* AD 認証を使用したレプリケーション
* Windows および Linux 全体でのレプリケーションの構成
* 即時更新トランザクション レプリケーション

## <a name="limitations"></a>制限事項

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] 次の機能をサポートしません。

* 即時更新サブスクライバー

## <a name="next-steps"></a>次の手順

[Linux 上の SQL Server レプリケーションを構成します。](sql-server-linux-replication-tutorial-tsql.md)

[サンプル: Linux 上の SQL Server レプリケーションを構成します。](sql-server-linux-replication-configure.md)

---
title: Linux 上の SQL Server レプリケーション
description: この記事では、Linux 上の SQL Server レプリケーションについて説明します。
author: MikeRayMSFT
ms.author: mikeray
ms.reviewer: vanto
ms.date: 10/17/2018
ms.topic: article
ms.prod: sql
ms.prod_service: database-engine
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: b049866d9752485cb1b9eb609404a3bd86f28a41
ms.sourcegitcommit: db9bed6214f9dca82dccb4ccd4a2417c62e4f1bd
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/25/2019
ms.locfileid: "68065191"
---
# <a name="sql-server-replication-on-linux"></a>Linux 上の SQL Server レプリケーション

[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md-linuxonly](../includes/appliesto-ss-xxxx-xxxx-xxx-md-linuxonly.md)]

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] では、SQL Server on Linux インスタンス用の SQL Server レプリケーションが導入されています。

SQL Server Management Studio (SSMS) の[レプリケーション ストアド プロシージャ](../relational-databases/system-stored-procedures/replication-stored-procedures-transact-sql.md)を使用して、Linux 上でレプリケーションを構成します。

SQL Server インスタンスは、任意のレプリケーション ロールに参加できます。

* パブリッシャー
* ディストリビューター
* サブスクライバー (Subscriber)

レプリケーション スキーマでは、オペレーティング システムのプラットフォームを混在させて一致させることができます。 たとえば、レプリケーション スキーマにパブリッシャーとディストリビューターの SQL Server on Linux インスタンスを含めることができ、サブスクライバーに Windows 上と Linux 上の SQL Server インスタンスを含めることができます。

Linux 上の SQL Server インスタンスは、任意の種類のレプリケーションに参加できます。

* トランザクション
* Merge
* スナップショット

レプリケーションの詳細については、[SQL Server レプリケーションのドキュメント](../relational-databases/replication/sql-server-replication.md)を参照してください。

## <a name="supported-features"></a>サポートされている機能

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] では、次のレプリケーション機能がサポートされます。

* スナップショット レプリケーション
* トランザクション レプリケーション
* マージ レプリケーション
* ピア ツー ピア レプリケーション
* 既定以外のポートを使用するレプリケーション <!--Add link to explanation-->
* AD 認証を使用するレプリケーション
* Windows と Linux 間でのレプリケーションの構成
* トランザクション レプリケーションの即時更新

## <a name="limitations"></a>制限事項

[!INCLUDE[SQL Server 2019](../includes/sssqlv15-md.md)] では、次の機能はサポートされません。

* 即時更新サブスクライバー
* Oracle パブリッシュ

## <a name="next-steps"></a>次の手順

[Linux 上で SQL Server レプリケーションを構成する](sql-server-linux-replication-tutorial-tsql.md)

[サンプル:Linux 上で SQL Server レプリケーションを構成する](sql-server-linux-replication-configure.md)

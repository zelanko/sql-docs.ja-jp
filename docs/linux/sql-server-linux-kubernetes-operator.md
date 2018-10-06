---
title: SQL Server Always On 可用性グループ Kubernetes 演算子グローバルの要件
description: この記事では、要件については、SQL Server Kubernetes Always On 可用性グループ演算子グローバル パラメーターを説明します。
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.date: 08/09/2018
ms.topic: article
ms.prod: sql
ms.custom: sql-linux
ms.technology: linux
monikerRange: '>=sql-server-ver15||>=sql-server-linux-ver15||=sqlallproducts-allversions'
ms.openlocfilehash: 187517c79f14ddcbf08ffa644e65558fa0a85b38
ms.sourcegitcommit: 4832ae7557a142f361fbf0a4e2d85945dbf8fff6
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/03/2018
ms.locfileid: "48252000"
---
# <a name="sql-server-always-on-availability-group-kubernetes-operator-parameters"></a>SQL Server Always On 可用性グループ Kubernetes 演算子のパラメーター

Kubernetes 上の Always On 可用性グループには、演算子が必要です。 マニフェストには、演算子について説明します。 マニフェストは、`.yaml`ファイル。 内の指定の例を参照してください。 [Always On 可用性グループの SQL Server のコンテナー](sql-server-ag-kubernetes.md)します。

この記事では、演算子のグローバル環境変数について説明します。

## <a name="example"></a>例

次の例では、説明の展開を`mssql-operator`します。

## <a name="global-environment-variables"></a>グローバル環境変数

* `MSSQL_K8S_POD_NAMESPACE` 
  * 必須
  * **説明**: 演算子の Kubernetes 名前空間。

* `MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`
  * 省略可
  * **説明**: sql server の書き込みリースの期間。 書き込み可能な sql server を保持し、スプリット ブレイン シナリオを防止するために使用します。 セカンダリ レプリカは、この新しいリーダーを選択した後の秒数待機します。

* `MSSQL_K8S_MONITOR_PERIOD_SECONDS`
  * 省略可
  * **説明**: 可用性グループの状態を監視する期間。 レプリカの追加し、削除のどの程度の速度を決定します。 必要がありますより小さい`MSSQL_K8S_SQL_WRITE_LEASE_PERIOD_SECONDS`します。
  * **既定の**: 1

* `MSSQL_K8S_LEASE_DURATION_SECONDS`
  * 省略可
  * **説明**: 可用性グループのリーダーのリースの期間。 セカンダリ レプリカがプライマリ レプリカがクラッシュした場合の再選択する前に待機する時間を決定します。 これは、SQL Server の書き込みリースよりも異なります。 
  * **既定の**: 10
  
  >[!NOTE]
  >その他の設定に基づいて自動的に計算される`MSSQL_K8S_LEASE_DURATION_SECONDS`します。

* `MSSQL_K8S_RENEW_DEADLINE_SECONDS`
  * 省略可
  * **説明**: 動作するプライマリ レプリカ与える前に更新リーダーシップを再試行する期間。 必要がありますより小さい`MSSQL_K8S_LEASE_DURATION_SECONDS`します。
  * **既定の**:  `MSSQL_K8S_LEASE_DURATION_SECONDS` /2

* `MSSQL_K8S_RETRY_PERIOD_SECONDS`
  * 省略可
  * **説明**: 期間、機能して[マスター](http://kubernetes.io/docs/concepts/architecture/master-node-communication/)リーダー リースを更新するまで待機します。 必要がありますより小さい`MSSQL_K8S_LEASE_DURATION_SECONDS`します。
  * **既定の**:  `MSSQL_K8S_RENEW_DEADLINE_SECONDS` /2

* `MSSQL_K8S_ACQUIRE_PERIOD_SECONDS` 
  * 省略可
  * **説明**: リーダー リースの有効期限が切れている場合にセカンダリ レプリカがポーリングする期間。 
  * **既定の**: 1


  ## <a name="next-steps"></a>次の手順

[Kubernetes クラスター上の SQL Server 可用性グループ](sql-server-ag-kubernetes.md)

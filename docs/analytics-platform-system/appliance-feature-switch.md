---
title: 機能スイッチ (Analytics Platform System)
description: 分析プラットフォーム システム AU7 で導入された 2 つの機能のスイッチに関する情報を表示します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/24/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: e384a252584fed0e7543a7a4000fc9a70f6533e7
ms.sourcegitcommit: fc3cd23685c6b9b6972d6a7bab2cc2fc5ebab5f2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/25/2018
---
#<a name="appliance-feature-switch"></a>アプライアンス機能のスイッチ
**機能スイッチ**ページには、分析プラットフォーム システム AU7 で導入された 2 つの機能のスイッチに関する情報が表示されます。 このページを使用して、更新または Analytics Platform System の機能と設定の有効/無効にします。 機能スイッチの値を変更するには、サービスの再起動が必要です。

![DWConig アプライアンス機能のスイッチ](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig アプライアンス機能のスイッチ") 

##<a name="autostatsenabled-switch"></a>AutoStatsEnabled スイッチ
自動統計機能を制御します。 この機能スイッチが に設定されている AU7 へのアップグレード後に既定では true です。 アップグレード後に作成されたデータベースは自動作成し、統計の非同期更新を継承します。 既存のデータベースに対して、データベース管理者にはで統計の自動も有効にすることができます [データベースの変更] (/sql/t-sql/statements/alter-database-parallel-data-warehouse)。 統計情報の詳細については、次を参照してください。[統計](../relational-databases/statistics/statistics.md)です。

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>DmsProcessStopMessageTimeoutInSeconds スイッチ
データ移動サービス (DM) は、データ移動を伴うクエリが取り消されたときに、ビジー状態のシステムで同期するために待機する時間を制御します。 既定の 900 秒 (15 分) にこの値を設定 AU7 への更新します。 有効な範囲は、0 – は、3600 秒です。

---
title: 機能スイッチ (Analytics Platform System)
description: Analytics Platform System AU7 で導入された、2 つの機能スイッチの詳細情報を表示します。
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 06/27/2018
ms.author: murshedz
ms.reviewer: martinle
monikerRange: '>= aps-pdw-2016-au7 || = sqlallproducts-allversions'
ms.openlocfilehash: 0d2aadb0e7c0c56c69d89bc94e0ddaacef54e837
ms.sourcegitcommit: 3e1efbe460723f9ca0a8f1d5a0e4a66f031875aa
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/30/2018
ms.locfileid: "50236908"
---
#<a name="appliance-feature-switches"></a>アプライアンスの機能スイッチ
**機能スイッチ**ページは、Analytics Platform System AU7 と後で導入された機能スイッチに関する情報を表示します。 この構成ページを使用して、更新、または Analytics Platform System の機能と設定の有効/無効にします。 機能スイッチの値への変更には、サービスの再起動が必要です。

![DWConig アプライアンス機能スイッチ](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig アプライアンス機能の切り替え") 

##<a name="autostatsenabled"></a>AutoStatsEnabled
自動統計機能を制御します。 この機能スイッチが 設定されている AU7 へのアップグレード後に既定では true。 アップグレード後に作成されたデータベースの自動作成し、統計の非同期更新を継承します。 既存のデータベースに対してデータベース管理者の自動統計をできるように[ALTER DATABASE (並列データ ウェアハウス)](../t-sql/statements/alter-database-transact-sql.md?tabs=sqlpdw)します。 統計の詳細については、次を参照してください。[統計](../relational-databases/statistics/statistics.md)します。

##<a name="maxdopforinsertqueries"></a>MaxDOPForInsertQueries
挿入/選択操作の 1 より大きい maxdop 設定を選択することができます。 この設定のオプションは、0、1、2 および 4 は、既定値は 1 の中にです。

##<a name="usecatalogqueries"></a>UseCatalogQueries
SMO を使用する代わりにメタデータ呼び出しをいくつかのカタログ オブジェクトを使用すると、パフォーマンスの向上を説明しました。 CU7.1、このスイッチで既定で true に設定するには、その動作が制御します。 

##<a name="dmsprocessstopmessagetimeoutinseconds"></a>DmsProcessStopMessageTimeoutInSeconds
データ移動サービス (DMS) は、データの移動を伴うクエリが取り消されたときに、負荷の高いシステムに同期するが待機する時間を制御します。 この値を既定では 900 秒 (15 分) を設定 AU7 への更新します。 有効範囲は、0 ~ 3600 (秒) です。
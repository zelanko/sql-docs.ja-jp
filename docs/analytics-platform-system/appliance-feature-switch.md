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
ms.openlocfilehash: b06c715549cd1c9cf464a13b03790764ebf40b97
ms.sourcegitcommit: 3e5f1545e5c6c92fa32e116ee3bff1018ca946a2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/29/2018
ms.locfileid: "37107180"
---
#<a name="appliance-feature-switch"></a>アプライアンスの機能スイッチ
**機能スイッチ**で Analytics Platform System 2016-AU7 に導入された 2 つの機能スイッチに関する情報を表示するページ。 このページを使用して、更新、または Analytics Platform System の機能と設定の有効/無効にします。 機能スイッチの値を変更するには、サービスの再起動が必要です。

![DWConig アプライアンス機能スイッチ](media/feature-switch/SQL_Server_PDW_DWConfig_feature_switch.png "DWConig アプライアンス機能の切り替え") 

##<a name="autostatsenabled-switch"></a>AutoStatsEnabled スイッチ
自動統計機能を制御します。 この機能スイッチが 設定されている AU7 へのアップグレード後に既定では true。 アップグレード後に作成されたデータベースの自動作成し、統計の非同期更新を継承します。 既存のデータベースに対してデータベース管理者には自動統計をも有効にすることができます [データベースの変更] (/sql/t-sql/statements/alter-database-parallel-data-warehouse)。 統計の詳細については、次を参照してください。[統計](../relational-databases/statistics/statistics.md)します。

##<a name="dmsprocessstopmessagetimeoutinseconds-switch"></a>DmsProcessStopMessageTimeoutInSeconds スイッチ
データ移動サービス (DMS) は、データの移動を伴うクエリが取り消されると、負荷の高いシステムに同期するが待機する時間を制御します。 この値を既定では 900 秒 (15 分) を設定 AU7 への更新します。 有効範囲は、0 ~ 3600 (秒) です。

---
title: SQL Server 2017 Analysis Services の旧バージョンとの互換性 |Microsoft Docs
ms.date: 03/08/2019
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
monikerRange: '>= sql-server-2017 || = sqlallproducts-allversions'
ms.openlocfilehash: 3ad5bed93bf69f004276fd751f7f2fdef1ea9997
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "68210273"
---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Analysis Services の旧バージョンとの互換性 (SQL 2017)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

この記事では、機能の可用性と現在のリリースと以前のリリースの動作の変更について説明します。

## <a name="deprecated-features"></a>非推奨の機能
A*非推奨の機能*は将来のリリースで製品から廃止されますはまだサポートされているし、旧バージョンとの互換性を維持するために現在のリリースに含まれます。 今後のリリースとの互換性を維持するために、新規および既存のプロジェクトで非推奨の機能を使用して停止するをお勧めします。 非推奨の機能では、ドキュメントは更新されません。

次の機能は、このリリースで非推奨とされます。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|
|多次元|データ マイニング|
|多次元|リモート リンク メジャー グループ|
|テーブル|1100 と 1103 互換性レベル モデル|
|テーブル|表形式オブジェクト モデルのプロパティ:Column.TableDetailPosition、Column.IsDefaultLabel、Column.IsDefaultImage|
|ツール|SQL Server Profiler for Trace Capture<br /><br /> この機能に代えて、SQL Server Management Studio に組み込まれている Extended Events Profiler を使用します。  <br /> 「 [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)」を参照してください。|  
|ツール|Server Profiler for Trace Replay <br />置換します。 これに代わる機能はありません。|  
|トレース管理オブジェクトおよびトレース API|Microsoft.AnalysisServices.Trace オブジェクト (Analysis Services Trace および Replay オブジェクトの API を含みます)。 置き換えは、複数の手順で行います。<br /><br /> -トレース構成:Microsoft.SqlServer.Management.XEvent<br />-トレース読み取り:Microsoft.SqlServer.XEvent.Linq<br />-トレース再生。なし|  


## <a name="discontinued-features"></a>廃止された機能
A*機能を廃止*以前のリリースで非推奨とされました。 現在のリリースに含まれるが継続されますが、現在サポートされていません。 廃止された機能を削除することがあります、将来のリリースか更新します。

以前のリリースで非推奨とされた、このリリースではサポートされなくを次の機能です。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|  
|テーブル|VertipaqPagingPolicy メモリ プロパティの値 (2)、メモリを使用してディスクにページングを有効にするには、ファイルがマップされています。|
|多次元|リモート パーティション|  
|多次元|リモート リンク メジャー グループ|  
|多次元|ディメンションの書き戻し|  
|多次元|リンク ディメンション|


## <a name="breaking-changes"></a>互換性に影響する変更
A*互換性に影響する変更*現在のリリースにアップグレードした後、機能、データ モデル、アプリケーション コードまたはスクリプトが不要になった機能を発生します。

このリリースでは、重大な変更はありません。

## <a name="behavior-changes"></a>動作の変更
A*動作の変更*以前のリリースと比較して、現在のリリースで、同じ機能の動作に影響を与えます。 重要な動作の変更のみがについて説明します。 ユーザー インターフェイスの変更は含まれません。

MDSCHEMA_MEASUREGROUP_DIMENSIONS を DISCOVER_CALC_DEPENDENCY、変更の詳細について、 [Analysis Services 用 SQL Server 2017 CTP 2.1 の新](https://blogs.msdn.microsoft.com/analysisservices/2017/05/18/whats-new-in-sql-server-2017-ctp-2-1-for-analysis-services/)お知らせします。


## <a name="see-also"></a>関連項目
[Analysis Services の旧バージョンとの互換性 (SQL Server 2016)](analysis-services-backward-compatibility.md)

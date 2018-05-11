---
title: SQL Server 2017 Analysis Services の旧バージョンと互換性 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: c933bedabebc9683d8f4dbcd0cb1aa235346ef18
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="analysis-services-backward-compatibility-sql-2017"></a>Analysis Services の旧バージョンとの互換性 (SQL 2017)
[!INCLUDE[ssas-appliesto-sql2017](../includes/ssas-appliesto-sql2017.md)]

この記事では、機能の可用性と現在のリリースと、以前のリリースの間での動作の変更について説明します。

## <a name="deprecated-features"></a>非推奨機能
A*非推奨の機能*将来のリリースで製品から廃止されますが、まだサポートされ、旧バージョンとの互換性を維持するために、現在のリリースに含まれています。 今後のリリースとの互換性を維持するために新規および既存のプロジェクトでは非推奨機能を使用して停止するをお勧めします。

このリリースでは、次の機能が廃止されました。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|
|多次元|データ マイニング|
|多次元|リモート リンク メジャー グループ|
|テーブル|1100 と 1103 互換性レベル モデル|
|テーブル|表形式オブジェクト モデルのプロパティ: Column.TableDetailPosition、Column.IsDefaultLabel、Column.IsDefaultImage|
|ツール|SQL Server Profiler for Trace Capture<br /><br /> この機能に代えて、SQL Server Management Studio に組み込まれている Extended Events Profiler を使用します。  <br /> 「[SQL Server 拡張イベントを使用した Analysis Services の監視](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)」を参照してください。|  
|ツール|Server Profiler for Trace Replay <br />置換します。 これに代わる機能はありません。|  
|トレース管理オブジェクトおよびトレース API|Microsoft.AnalysisServices.Trace オブジェクト (Analysis Services Trace および Replay オブジェクトの API を含みます)。 置き換えは、複数の手順で行います。<br /><br /> トレース構成: Microsoft.SqlServer.Management.XEvent<br />-トレース読み取り: Microsoft.SqlServer.XEvent.Linq<br />- トレース再生: なし|  


## <a name="discontinued-features"></a>廃止された機能
A*提供が中止された機能*以前のリリースでは推奨されなくなりました。 現在のリリースに含まれる継続可能性がありますが、現在サポートされていません。 廃止された機能を削除することがあります、将来のリリースか更新します。

次の機能は、以前のリリースで非推奨となったし、このリリースではサポートされなくです。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|  
|テーブル|VertipaqPagingPolicy メモリ プロパティの値 (2)、メモリを使用してディスクへのページングを有効にするには、ファイルがマップされています。|
|多次元|リモート パーティション|  
|多次元|リモート リンク メジャー グループ|  
|多次元|ディメンションの書き戻し|  
|多次元|リンク ディメンション|


## <a name="breaking-changes"></a>重大な変更
A*互換性に影響する変更*現在のリリースにアップグレードした後、機能、データ モデル、アプリケーション コードまたはスクリプトが機能しなくをによりします。

このリリースでは、互換性に影響する変更はありません。

## <a name="behavior-changes"></a>動作の変更
A*動作の変更*現在のリリース以前のリリースと比較して同じ機能の動作に影響します。 重要な動作の変更のみを説明します。 ユーザー インターフェイスの変更は含まれません。

MDSCHEMA_MEASUREGROUP_DIMENSIONS と DISCOVER_CALC_DEPENDENCY への変更の詳細で、 [Analysis Services 用 SQL Server 2017 CTP 2.1 の新機能](https://blogs.msdn.microsoft.com/analysisservices/2017/05/18/whats-new-in-sql-server-2017-ctp-2-1-for-analysis-services/)お知らせします。


## <a name="see-also"></a>参照
[Analysis Services の旧バージョンとの互換性 (SQL Server 2016)](analysis-services-backward-compatibility.md)

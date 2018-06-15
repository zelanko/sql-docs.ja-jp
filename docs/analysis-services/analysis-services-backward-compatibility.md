---
title: SQL Server 2016 Analysis Services の旧バージョンと互換性 |Microsoft ドキュメント
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 5ab4f304d865992a3269b4ee83c9e25f61069e8c
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
ms.locfileid: "34015639"
---
# <a name="analysis-services-backward-compatibility-sql-server-2016"></a>Analysis Services の旧バージョンとの互換性 (SQL Server 2016)
[!INCLUDE[ssas-appliesto-sql2016](../includes/ssas-appliesto-sql2016.md)]

この記事では、機能の可用性と現在のバージョンと以前のバージョン間の動作の変更について説明します。

## <a name="deprecated-features"></a>非推奨機能
A*非推奨の機能*将来のリリースで製品から廃止されますが、まだサポートされ、旧バージョンとの互換性を維持するために、現在のリリースに含まれています。 今後のリリースとの互換性を維持するために新規および既存のプロジェクトでは非推奨機能を使用して停止するをお勧めします。
  
このリリースでは、次の機能が廃止されました。
  
|||  
|-|-|  
|**モード/カテゴリ**|**機能**|  
|多次元|リモート パーティション|  
|多次元|リモート リンク メジャー グループ|  
|多次元|ディメンションの書き戻し|  
|多次元|リンク ディメンション|   
|多次元|プロアクティブ キャッシュ用の SQL Server テーブル通知。  <br />これに代えて、アクティブ キャッシュ用にポーリングを使用します。 <br />「[プロアクティブ キャッシュ (ディメンション)](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md)」および「[プロアクティブ キャッシュ (パーティション)](../analysis-services/multidimensional-models-olap-logical-cube-objects/partitions-proactive-caching.md)」を参照してください。|  
|多次元|セッション キューブ。 これに代わる機能はありません。|  
|多次元|ローカル キューブ。 これに代わる機能はありません。|  
|テーブル|表形式モデルの 1100 および 1103 互換性レベルは、将来のリリースではサポートされません。 代わりのモデルの互換性レベル 1200 以上に設定モデル定義を表形式メタデータに変換を開始します。 「 [Analysis Services での表形式モデルの互換性レベル](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。|  
|ツール|SQL Server Profiler for Trace Capture<br /><br /> この機能に代えて、SQL Server Management Studio に組み込まれている Extended Events Profiler を使用します。  <br /> 「[SQL Server 拡張イベントを使用した Analysis Services の監視](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)」を参照してください。|  
|ツール|Server Profiler for Trace Replay <br />置換します。 これに代わる機能はありません。|  
|トレース管理オブジェクトおよびトレース API|Microsoft.AnalysisServices.Trace オブジェクト (Analysis Services Trace および Replay オブジェクトの API を含みます)。 置き換えは、複数の手順で行います。<br /><br /> トレース構成: Microsoft.SqlServer.Management.XEvent<br />-トレース読み取り: Microsoft.SqlServer.XEvent.Linq<br />- トレース再生: なし|  
  
> [!NOTE]  
>  以前の [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] での非推奨の機能の発表内容は有効です。 これらの機能のコードはまだ製品から削除されていないため、これらの機能の多くはこのリリースにおいても存在します。 以前非推奨機能の中に可能性があるアクセス可能は変わらず廃止されており、物理的にある可能性があります製品からいつでも削除です。  

## <a name="discontinued-features"></a>廃止された機能
A*提供が中止された機能*以前のリリースでは推奨されなくなりました。 現在のリリースに含まれる継続可能性がありますが、現在サポートされていません。 廃止された機能を削除することがあります、将来のリリースか更新します。

次の機能は、以前のリリースで非推奨となったし、このリリースではサポートされなくです。

|||  
|-|-|  
|**機能**|**置換または回避策**|  
|[CalculationPassValue (MDX)](../mdx/calculationpassvalue-mdx.md)|[なし] : この機能は SQL Server 2005 で非推奨となりました。|  
|[CalculationCurrentPass (MDX)](../mdx/calculationcurrentpass-mdx.md)|[なし] : この機能は SQL Server 2005 で非推奨となりました。|  
|NON_EMPTY_BEHAVIOR クエリ オプティマイザー ヒント|[なし] : この機能は SQL Server 2008 で非推奨となりました。|  
|COM アセンブリ|[なし] : この機能は SQL Server 2008 で非推奨となりました。|  
|CELL_EVALUATION_LIST intrinsic セル プロパティ|[なし] : この機能は SQL Server 2005 で非推奨となりました。|  
  
> [!NOTE]  
>  以前の [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] での非推奨の機能の発表内容は有効です。 これらの機能のコードはまだ製品から削除されていないため、これらの機能の多くはこのリリースにおいても存在します。 以前非推奨機能の中に可能性があるアクセス可能は変わらず廃止されており、物理的にある可能性があります製品からいつでも削除です。  

## <a name="breaking-changes"></a>重大な変更
*重大な変更* は、モデルまたはサーバーのアップグレード後に、データ モデル、アプリケーション コード、またはスクリプトが機能しなくなるような変更です。
  
### <a name="net-40-version-upgrade"></a>.NET 4.0 のバージョン アップグレード  
 Analysis Services 管理オブジェクト (AMO)、ADOMD.NET、および表形式オブジェクト モデル (TOM) のクライアント ライブラリのターゲットを .NET 4.0 ランタイム。 これは、.NET 3.5 をターゲットとするアプリケーションにとって重大な変更になる可能性があります。 これらのアセンブリの新しいバージョンを使用するアプリケーションは、.NET 4.0 以降をターゲットとする必要があります。  
  
### <a name="amo-version-upgrade"></a>AMO のバージョン アップグレード  
 このリリースのバージョンのアップグレードは、 [Analysis Services 管理オブジェクト&#40;AMO&#41; ](https://msdn.microsoft.com/library/mt436122.aspx)は特定の状況での互換性に影響する変更です。  以前のバージョンからアップグレードした場合でも、AMO を呼び出す既存のコードやスクリプトは従来と同様に動作します。 ただし、する必要がある場合*再コンパイル*を SQL Server 2016 Analysis Services インスタンスの対象として、アプリケーション、コードまたはスクリプトを稼働させるために次の名前空間を追加する必要があります。  
  
```  
  
using Microsoft.AnalysisServices;  
using Microsoft.AnalysisServices.Core;  
  
```  
  
 コードで Microsoft.AnalysisServices アセンブリを参照するときは常に [Microsoft.AnalysisServices.Core](https://msdn.microsoft.com/library/microsoft.analysisservices.core.aspx) 名前空間が必要になりました。 以前は **Microsoft.AnalysisServices** 名前空間のみに含まれていたオブジェクトが、このリリースでは Core 名前空間に移動されています (オブジェクトがテーブルと多次元の両方のシナリオで同じように使用される場合)。  たとえば、サーバー関連の API は Core 名前空間に移動されました。  
  
 複数の名前空間が存在することになりますが、どちらも同じアセンブリ (Microsoft.AnalysisServices.dll) に含まれます。  
  
### <a name="xevent-discover-changes"></a>XEvent DISCOVER の変更点  
 XEvent 検出 SSMS では、SQL Server 2016 の Analysis Services のストリーミング サポートを向上させる`DISCOVER_XEVENT_TRACE_DEFINITION`は次の XEvent トレースで置き換えられます。  
  
-   DISCOVER_XEVENT_PACKAGES  
  
-   DISCOVER_XEVENT_OBJECT  
  
-   DISCOVER_XEVENT_OBJECT_COLUMNS  
  
-   DISCOVER_XEVENT_SESSION_TARGETS  

## <a name="behavior-changes"></a>動作の変更
*動作の変更* の影響は、現在のバージョンの SQL Server の機能や操作方法が、以前のバージョンの SQL Server とは異なることに表れます。
  
製品動作の変更の例として、既定値の変更、アップグレードまたは復元機能を完了するために必要な手動の構成、または既存の機能の新しい実装などがあります。
  
このリリースで変更される機能の動作は、今のところ既存のモデルやアップグレード後のコードを破壊することはありませんが、ここに一覧を示します。
  
### <a name="analysis-services-in-sharepoint-mode"></a>SharePoint モードの Analysis Services
 インストール後のタスクとしての Power Pivot 構成ウィザードの実行は不要になりました。 これは、すべてのサポートされているバージョンの SharePoint を現在の SQL Server 2016 Analysis Services からモデルを読み込む場合は true です。
  
### <a name="directquery-mode-for-tabular-models"></a>表形式モデルの DirectQuery モード
 *DirectQuery* は、表形式モデル用のデータ アクセス モードです。ここでは、クエリ実行はリアルタイムで結果セットを取得して、バックエンド リレーショナル データベースで実行されます。 通常は、メモリに収まらない非常に大規模なデータセットや、データが揮発性で、表形式モデルに対するクエリで返された最新のデータが必要な場合に使用されます。
  
 DirectQuery は、過去数回のリリースではデータ アクセス モードとして存在します。 SQL Server 2016 の Analysis Services に実装がわずかに変更されては表形式モデルの互換性レベル 1200 以上でと仮定した場合します。 DirectQuery の制限は、以前よりも少なくなりました。 また、さまざまなデータベース プロパティもあります。
  
 既存の表形式モデルで DirectQuery を使用している場合、モデルを現在の互換性レベル 1100 または 1103 に維持して、それらのレベルで実装された DirectQuery として使用し続けることができます。 代わりに、DirectQuery に対して作成された拡張機能から利点を得るには、1200 以上にアップグレードすることができます。
  
 以前の互換性レベル設定では、新しい 1200 以降の互換性レベルでは、対応するはできないために、DirectQuery モデルのインプレース アップグレードはありません。 DirectQuery モードで実行されている既存のテーブル モデルがあれば、する必要があります SQL Server Data Tools でモデルを開いて、DirectQuery をオフ、設定、**互換性レベル**プロパティを 1200 以上とし、再構成、DirectQueryプロパティ。 参照してください[DirectQuery モード](../analysis-services/tabular-models/directquery-mode-ssas-tabular.md)詳細についてはします。


## <a name="see-also"></a>参照
[Analysis Services の旧バージョンとの互換性 (SQL Server 2017)](analysis-services-backward-compatibility-sql2017.md)

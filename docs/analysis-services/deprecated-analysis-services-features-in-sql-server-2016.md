---
title: "SQL Server 2016 に含まれている非推奨の Analysis Services 機能 | Microsoft Docs"
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Analysis Services、旧バージョンとの互換性"
  - "SSAS、旧バージョンとの互換性"
  - "SQL Server Analysis Services、旧バージョンとの互換性"
  - "非推奨機能 [Analysis Services]"
ms.assetid: 2c96ecfe-a170-41d0-bee3-74503f880197
caps.latest.revision: 52
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 52
---
# SQL Server 2016 に含まれている非推奨の Analysis Services 機能
  *非推奨の機能* とは、製品の将来のリリースで削除される予定になっている一方で、下位互換性を保つために現在のリリースでサポートされ、組み込まれている機能を表します。 通常、非推奨の機能は、多くの場合、その発表が行われた後の 2 リリース以内のメジャー リリースで削除されます。 たとえば、 [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] で非推奨と発表された機能は、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]でサポートされない可能性が高くなります。  
  
 **SQL Server の次のメジャー リリースでサポートされない機能**  
  
|||  
|-|-|  
|**カテゴリ**|**機能**|  
|多次元|リモート パーティション|  
|多次元|リモート リンク メジャー グループ|  
|多次元|ディメンションの書き戻し|  
|多次元|リンク ディメンション|  
  
 **SQL Server の将来のリリースでサポートされない機能**  
  
|||  
|-|-|  
|**カテゴリ**|**機能**|  
|多次元|プロアクティブ キャッシュ用の SQL Server テーブル通知。  <br />これに代えて、アクティブ キャッシュ用にポーリングを使用します。 <br />「[プロアクティブ キャッシュ (ディメンション)](../analysis-services/multidimensional-models-olap-logical-dimension-objects/proactive-caching-dimensions.md)」および「[プロアクティブ キャッシュ (パーティション)](../Topic/Proactive%20Caching%20\(Partitions\).md)」を参照してください。|  
|多次元|セッション キューブ。 これに代わる機能はありません。|  
|多次元|ローカル キューブ。 これに代わる機能はありません。|  
|テーブル|表形式モデルの 1100 および 1103 互換性レベルは、将来のリリースではサポートされません。 この機能に代えて、モデルを互換性レベル 1200 で設定し、モデル定義を表形式メタデータに変換します。 「 [Compatibility Level for Tabular models in Analysis Services](../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)」を参照してください。|  
|ツール|SQL Server Profiler for Trace Capture<br /><br /> この機能に代えて、SQL Server Management Studio に組み込まれている Extended Events Profiler を使用します。  <br /> 「 [Monitor Analysis Services with SQL Server Extended Events](../analysis-services/instances/monitor-analysis-services-with-sql-server-extended-events.md)」を参照してください。|  
|ツール|Server Profiler for Trace Replay <br />置換します。 これに代わる機能はありません。|  
|トレース管理オブジェクトおよびトレース API|Microsoft.AnalysisServices.Trace オブジェクト (Analysis Services Trace および Replay オブジェクトの API を含みます)。 置き換えは、複数の手順で行います。<br /><br /> - トレース構成:  Microsoft.SqlServer.Management.XEvent<br />- トレース読み取り:  Microsoft.SqlServer.XEvent.Linq<br />- トレース再生: なし|  
  
> [!NOTE]  
>  以前の [!INCLUDE[ssSQL14](../includes/sssql14-md.md)] での非推奨機能の発表内容は有効です。 これらの機能のコードはまだ製品から削除されていないため、これらの機能の多くはこのリリースにおいても存在します。 以前に非推奨となった機能にアクセスすることはできますが、非推奨であることは変わらず、 [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] リリースの特定の時点で製品から物理的に削除される可能性があります。 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] の [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)]に基づくすべての新しいモデルまたはアプリケーションにおいて、非推奨機能を使用しないことを強くお勧めします。  
  
## 参照  
 [Analysis Services の旧バージョンとの互換性](../analysis-services/analysis-services-backward-compatibility.md)   
 [SQL Server 2016 で提供が中止された Analysis Services の機能](../analysis-services/discontinued-analysis-services-functionality-in-sql-server-2016.md)  
  
  
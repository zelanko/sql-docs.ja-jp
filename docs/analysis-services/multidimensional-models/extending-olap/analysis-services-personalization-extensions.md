---
title: Analysis Services のパーソナル化拡張機能 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/14/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- personalization extensions [Multidimensional Databases]
ms.assetid: 0f144059-24e0-40c0-bde4-d48c75e46598
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: bd55cabe877554254b63ba31e80a504117d2cf36
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/08/2018
---
# <a name="analysis-services-personalization-extensions"></a>Analysis Services のパーソナル化拡張機能
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)][!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、プラグイン アーキテクチャを実装するという概念の基盤です。 プラグイン アーキテクチャでは、新しいキューブ オブジェクトや機能を動的に開発し、他の開発者と簡単に共有することができます。 そのため、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、次を実現するためにできるようにする機能を提供します。  
  
-   **動的な設計と展開**設計し、展開後すぐに[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能のユーザー アクセス権を持つオブジェクトと機能を次のユーザー セッションの開始時です。  
  
-   **インターフェイス非依存**作成に使用するインターフェイスに関係なく、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能、ユーザーのインターフェイスを使用してオブジェクトや機能にアクセスします。  
  
-   **セッション コンテキスト**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、既存のインフラストラクチャのパーマネント オブジェクトではないと、キューブを再処理する必要はありません。 この機能は、ユーザーがデータベースに接続したときにそのユーザー用に公開および作成され、そのユーザー セッションの間だけ使用できます。  
  
-   **迅速な配布**共有[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]これを検索する方法や場所についての詳細な仕様に移動することがなく他のソフトウェア開発者とパーソナル化拡張機能の拡張機能です。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能の用途はさまざまです。 たとえば、会社の売上にさまざまな通貨が使用されているとします。 この場合、キューブにアクセスしている人物の現地通貨で連結売上を返す計算されるメンバーを作成します。 このメンバーをパーソナル化拡張機能として作成します。 その後、この計算されるメンバーをユーザー グループと共有します。 共有すると、ユーザーはサーバーに接続するとすぐに計算されるメンバーにアクセスできるようになります。 ユーザーは、計算されるメンバーの作成に使用されたインターフェイスと同じインターフェイスを使用していなくてもアクセスできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能の既存のマネージ アセンブリ アーキテクチャに対する単純で簡潔な変更および全体で公開されます、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <xref:Microsoft.AnalysisServices.AdomdServer>オブジェクト モデル、多次元式 (MDX) 構文、およびスキーマ行セット。  
  
## <a name="logical-architecture"></a>論理アーキテクチャ  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能のアーキテクチャは、マネージ アセンブリ アーキテクチャと次の 4 つの基本要素に基づいています。  
  
 [PlugInAttribute] カスタム属性  
 サービスの開始時に[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]、必要なアセンブリを読み込んでを判断するクラス、<xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute>カスタム属性です。  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、カスタム属性は、コードを記述して実行時の動作を指定する方法と定義されています。 詳細については、このトピックを参照してください。"[属性の概要](http://go.microsoft.com/fwlink/?LinkId=82929)、"で、 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] MSDN の開発者のガイドです。  
  
 すべてのクラスで、<xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute>カスタム属性は、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]既定のコンス トラクターを呼び出します。 新しいオブジェクトを構築するための共通の場所は、スタートアップ時のすべてのコンス トラクターを呼び出すと、ユーザー操作の独立したなります。  
  
 クラス コンストラクターでは、通常、パーソナル化拡張機能の作成および管理に関する情報の少量のキャッシュの構築に加え、<xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened> および <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing> イベントのサブスクライブが実行されます。 これらのイベントをサブスクライブしないと、共通言語ランタイム (CLR) のガベージ コレクターによって、誤ってクラスにクリーンアップのマークが付けられる可能性があります。  
  
 セッション コンテキスト  
 パーソナル化拡張機能に基づくオブジェクトの場合、クライアント セッション中に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって実行環境が作成され、この環境でほとんどのオブジェクトが動的に作成されます。 他の CLR アセンブリと同様に、この実行環境からも他の関数やストアド プロシージャにアクセスできます。 ユーザー セッションの終了時に[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]動的に作成されたオブジェクトを削除し、実行環境を閉じます。  
  
 イベント  
 オブジェクトの作成は、セッション イベントによってトリガーされる**キューブ-OpenedCubeOpened で**と**キューブ-ClosingCubeClosing で**です。  
  
 クライアントとサーバー間の通信は、特定のイベントを介して行われます。 このイベントによって、クライアントのオブジェクトが作成される状況がクライアントで認識されるようになります。 クライアントの環境は、セッション イベントとキューブ イベントという 2 つのイベント セットを使用して動的に作成されます。  
  
 セッション イベントは、サーバー オブジェクトに関連付けられます。 クライアントが、サーバーにログオンすると[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]セッションとトリガーを作成、<xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened>イベント。 クライアント、サーバー上のセッションの終了時に[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]トリガー、<xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing>イベント。  
  
 キューブ イベントは、接続オブジェクトに関連付けられます。 キューブに接続すると、<xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeOpened> イベントがトリガーされます。 キューブを閉じるか別のキューブに変更することによってキューブへの接続を終了すると、<xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeClosing> イベントがトリガーされます。  
  
 トレーサビリティとエラー処理  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] を使用すると、すべての操作をトレースできます。 未処理のエラーは、Windows イベント ログにレポートされます。  
  
 すべてのオブジェクトの作成および管理はこのアーキテクチャに依存せず、オブジェクトの開発者が責任を負います。  
  
## <a name="infrastructure-foundations"></a>インフラストラクチャの基盤  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能は、既存のコンポーネントに基づいています。 次に、パーソナル化拡張機能を実現する強化や改善の概要を示します。  
  
### <a name="assemblies"></a>アセンブリ  
 カスタム属性 <xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute> をカスタム アセンブリに追加して、[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能のクラスを特定することができます。  
  
### <a name="changes-to-the-adomdserver-object-model"></a>AdomdServer オブジェクト モデルへの変更  
 <xref:Microsoft.AnalysisServices.AdomdServer> オブジェクト モデル内の次のオブジェクトが強化されたか、モデルに追加されています。  
  
#### <a name="new-adomdconnection-class"></a>新しい AdomdConnection クラス  
 新しく追加された <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection> クラスは、プロパティとイベントの両方を介していくつかのパーソナル化拡張機能を公開します。  
  
 **[プロパティ]**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.SessionID%2A>: 現在の接続のセッション ID を表す読み取り専用の文字列値です。  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.ClientCulture%2A>: 現在のセッションに関連付けられているクライアントのカルチャへの読み取り専用の参照です。  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.User%2A>: 現在のユーザーを表す ID インターフェイスへの読み取り専用の参照です。  
  
 **イベント**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeOpened>  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection.CubeClosing>  
  
#### <a name="new-properties-in-the-context-class"></a>Context クラスの新しいプロパティ  
 <xref:Microsoft.AnalysisServices.AdomdServer.Context> クラスには、2 つの新しいプロパティが追加されています。  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Context.Server%2A>: 新しいサーバー オブジェクトへの読み取り専用の参照です。  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Context.CurrentConnection%2A>: 新しい <xref:Microsoft.AnalysisServices.AdomdServer.AdomdConnection> オブジェクトへの読み取り専用の参照です。  
  
#### <a name="new-server-class"></a>新しい Server クラス  
 新しく追加された <xref:Microsoft.AnalysisServices.AdomdServer.Server> クラスは、クラスのプロパティとイベントの両方を介していくつかのパーソナル化拡張機能を公開します。  
  
 **[プロパティ]**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.Name%2A>: サーバー名を表す読み取り専用の文字列値です。  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.Culture%2A>: サーバーに関連付けられているグローバル カルチャへの読み取り専用の参照です。  
  
 **イベント**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened>  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing>  
  
#### <a name="adomdcommand-class"></a>AdomdCommand クラス  
 <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> クラスで、次の MDX コマンドがサポートされるようになりました。  
  
-   [CREATE MEMBER ステートメント (MDX)](../../../mdx/mdx-data-definition-create-member.md)  
  
-   [UPDATE MEMBER ステートメント &#40;です。MDX と #41 です。](../../../mdx/mdx-data-definition-update-member.md)  
  
-   [DROP MEMBER ステートメント &#40;です。MDX と #41 です。](../../../mdx/mdx-data-definition-drop-member.md)  
  
-   [CREATE SET ステートメント (MDX)](../../../mdx/mdx-data-definition-create-set.md)  
  
-   [DROP SET ステートメント &#40;です。MDX と #41 です。](../../../mdx/mdx-data-definition-drop-set.md)  
  
-   [KPI ステートメント &#40; を作成します。MDX と #41 です。](../../../mdx/mdx-data-definition-create-kpi.md)  
  
-   [DROP KPI ステートメント &#40;です。MDX と #41 です。](../../../mdx/mdx-data-definition-drop-kpi.md)  
  
### <a name="mdx-extensions-and-enhancements"></a>MDX の拡張と強化  
 CREATE MEMBER コマンドがで強化され、**キャプション**プロパティ、 **display_folder**プロパティ、および**associated_measure_group**プロパティです。  
  
 UPDATE MEMBER コマンドが追加され、更新が必要になり計算の解決時の優先順位が失われることになる場合のメンバーの再作成が不要になりました。 別の親に計算されるメンバーを移動する更新プログラムは、計算されるメンバーのスコープを変更できませんまたは別の定義**solveorder**です。  
  
 CREATE SET コマンドは、強化、**キャプション**、プロパティ、 **display_folder**プロパティ、および新しい**静的 |動的**キーワード。 *静的*セットは作成時にのみ評価されることを意味します。 *動的*セットは、クエリで使用されるたびには、セットに評価されることを意味します。 既定値は**静的**キーワードを省略した場合。  
  
 CREATE KPI コマンドと DROP KPI コマンドが MDX 構文に追加されました。 KPI は、任意の MDX スクリプトから動的に作成できます。  
  
### <a name="schema-rowsets-extensions"></a>スキーマ行セットの拡張  
 MDSCHEMA_MEMBERS に*スコープ*列を追加します。 スコープの値は MDMEMBER_SCOPE_GLOBAL=1 と MDMEMBER_SCOPE_SESSION=2 です。  
  
 Mdschema_sets *set_evaluation_context*列を追加します。 セットの評価コンテキストの値は MDSET_RESOLUTION_STATIC = 1 と MDSET_RESOLUTION_DYNAMIC = 2 です。  
  
 MDSCHEMA_KPIS に scope 列が追加されました。 スコープの値は MDKPI_SCOPE_GLOBAL=1 と MDKPI_SCOPE_SESSION=2 です。  
  
  

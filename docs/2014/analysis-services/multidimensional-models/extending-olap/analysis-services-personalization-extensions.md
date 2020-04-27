---
title: Analysis Services 個人用設定拡張 |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: reference
helpviewer_keywords:
- personalization extensions [Multidimensional Databases]
ms.assetid: 0f144059-24e0-40c0-bde4-d48c75e46598
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 313b1764dfb17c3a8b49fa3ffa139668f9b2b421
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/26/2020
ms.locfileid: "62726118"
---
# <a name="analysis-services-personalization-extensions"></a>Analysis Services のパーソナル化拡張機能
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、プラグインアーキテクチャを実装するという概念の基盤です。 プラグイン アーキテクチャでは、新しいキューブ オブジェクトや機能を動的に開発し、他の開発者と簡単に共有することができます。 そのため、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能により、次のことを実現できる機能が提供されます。  
  
-   **動的な設計と配置**パーソナル化拡張機能を設計[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]して展開するとすぐに、ユーザーは次のユーザーセッションの開始時にオブジェクトと機能にアクセスできます。  
  
-   **インターフェイスの独立**パーソナル化拡張機能の[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]作成に使用するインターフェイスに関係なく、ユーザーは任意のインターフェイスを使用してオブジェクトや機能にアクセスできます。  
  
-   **セッションコンテキスト** [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]のパーソナル化拡張機能は、既存のインフラストラクチャ内の永続的なオブジェクトではなく、キューブを再処理する必要がありません。 この機能は、ユーザーがデータベースに接続したときにそのユーザー用に公開および作成され、そのユーザー セッションの間だけ使用できます。  
  
-   **迅速な配布**この[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]拡張機能を検索する場所や方法を詳細に説明する必要なく、パーソナル化拡張機能を他のソフトウェア開発者と共有します。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能の用途はさまざまです。 たとえば、会社の売上にさまざまな通貨が使用されているとします。 この場合、キューブにアクセスしている人物の現地通貨で連結売上を返す計算されるメンバーを作成します。 このメンバーをパーソナル化拡張機能として作成します。 その後、この計算されるメンバーをユーザー グループと共有します。 共有すると、ユーザーはサーバーに接続するとすぐに計算されるメンバーにアクセスできるようになります。 ユーザーは、計算されるメンバーの作成に使用されたインターフェイスと同じインターフェイスを使用していなくてもアクセスできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、既存のマネージアセンブリアーキテクチャに対する単純で洗練された[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] <xref:Microsoft.AnalysisServices.AdomdServer>変更であり、オブジェクトモデル、多次元式 (MDX) 構文、およびスキーマ行セット全体で公開されます。  
  
## <a name="logical-architecture"></a>論理アーキテクチャ  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能のアーキテクチャは、マネージド アセンブリ アーキテクチャと次の 4 つの基本要素に基づいています。  
  
 [PlugInAttribute] カスタム属性  
 サービスを開始すると[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、は必要なアセンブリを読み込み、 <xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute>カスタム属性を持つクラスを特定します。  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、カスタム属性は、コードを記述して実行時の動作を指定する方法と定義されています。 詳細については、MSDN の[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]開発者ガイドの「属性の[概要](https://go.microsoft.com/fwlink/?LinkId=82929)」を参照してください。  
  
 <xref:Microsoft.AnalysisServices.AdomdServer.PlugInAttribute>カスタム属性を持つすべてのクラスに[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]ついて、は既定のコンストラクターを呼び出します。 起動時にすべてのコンストラクターを呼び出すと、新しいオブジェクトの作成元となる、ユーザー操作に依存しない共通の場所が提供されます。  
  
 クラス コンストラクターでは、通常、パーソナル化拡張機能の作成および管理に関する情報の少量のキャッシュの構築に加え、<xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened> および <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing> イベントのサブスクライブが実行されます。 これらのイベントをサブスクライブしないと、共通言語ランタイム (CLR) のガベージ コレクターによって、誤ってクラスにクリーンアップのマークが付けられる可能性があります。  
  
 セッション コンテキスト  
 パーソナル化拡張機能に基づくオブジェクトの場合、クライアント セッション中に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって実行環境が作成され、この環境でほとんどのオブジェクトが動的に作成されます。 他の CLR アセンブリと同様に、この実行環境からも他の関数やストアド プロシージャにアクセスできます。 ユーザーセッションが終了すると[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、は動的に作成されたオブジェクトを削除し、実行環境を閉じます。  
  
 イベント  
 オブジェクトの作成は、セッション イベント `On-Cube-OpenedCubeOpened` および `On-Cube-ClosingCubeClosing` によってトリガーされます。  
  
 クライアントとサーバー間の通信は、特定のイベントを介して行われます。 このイベントによって、クライアントのオブジェクトが作成される状況がクライアントで認識されるようになります。 クライアントの環境は、セッション イベントとキューブ イベントという 2 つのイベント セットを使用して動的に作成されます。  
  
 セッション イベントは、サーバー オブジェクトに関連付けられます。 クライアントがサーバーにログオンすると、は[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]セッションを作成し、 <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened>イベントをトリガーします。 クライアントがサーバー上でセッションを終了すると[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、に<xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing>よってイベントがトリガーされます。  
  
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
  
 **プロパティ**  
  
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
  
 **プロパティ**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.Name%2A>: サーバー名を表す読み取り専用の文字列値です。  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.Culture%2A>: サーバーに関連付けられているグローバル カルチャへの読み取り専用の参照です。  
  
 **イベント**  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionOpened>  
  
-   <xref:Microsoft.AnalysisServices.AdomdServer.Server.SessionClosing>  
  
#### <a name="adomdcommand-class"></a>AdomdCommand クラス  
 <xref:Microsoft.AnalysisServices.AdomdServer.AdomdCommand> クラスで、次の MDX コマンドがサポートされるようになりました。  
  
-   [CREATE MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-create-member)  
  
-   [MDX&#41;&#40;のメンバーステートメントの更新](/sql/mdx/mdx-data-definition-update-member)  
  
-   [DROP MEMBER ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-drop-member)  
  
-   [CREATE SET ステートメント (MDX)](/sql/mdx/mdx-data-definition-create-set)  
  
-   [DROP SET ステートメント &#40;MDX&#41;](/sql/mdx/mdx-data-definition-drop-set)  
  
-   [MDX&#41;&#40;KPI ステートメントを作成する](/sql/mdx/mdx-data-definition-create-kpi)  
  
-   [MDX&#41;&#40;の KPI ステートメントの削除](/sql/mdx/mdx-data-definition-drop-kpi)  
  
### <a name="mdx-extensions-and-enhancements"></a>MDX の拡張と強化  
 CREATE MEMBER コマンドに `caption` プロパティ、`display_folder` プロパティ、および `associated_measure_group` プロパティが追加されました。  
  
 UPDATE MEMBER コマンドが追加され、更新が必要になり計算の解決時の優先順位が失われることになる場合のメンバーの再作成が不要になりました。 更新では、計算されるメンバーのスコープの変更、計算されるメンバーの別の親への移動、または別の `solveorder` の定義は実行できません。  
  
 CREATE SET コマンドに `caption` プロパティ、`display_folder` プロパティ、および新しい `STATIC | DYNAMIC` キーワードが追加されました。 *Static*は、set が作成時にのみ評価されることを意味します。 *動的*とは、セットがクエリで使用されるたびに、セットが評価されることを意味します。 キーワードが省略された場合、既定値は `STATIC` になります。  
  
 CREATE KPI コマンドと DROP KPI コマンドが MDX 構文に追加されました。 KPI は、任意の MDX スクリプトから動的に作成できます。  
  
### <a name="schema-rowsets-extensions"></a>スキーマ行セットの拡張  
 On MDSCHEMA_MEMBERS *scope*列が追加されます。 スコープの値は MDMEMBER_SCOPE_GLOBAL=1 と MDMEMBER_SCOPE_SESSION=2 です。  
  
 MDSCHEMA_SETS *set_evaluation_context*列が追加されます。 セットの評価コンテキストの値は MDSET_RESOLUTION_STATIC = 1 と MDSET_RESOLUTION_DYNAMIC = 2 です。  
  
 MDSCHEMA_KPIS に scope 列が追加されました。 スコープの値は MDKPI_SCOPE_GLOBAL=1 と MDKPI_SCOPE_SESSION=2 です。  
  
  

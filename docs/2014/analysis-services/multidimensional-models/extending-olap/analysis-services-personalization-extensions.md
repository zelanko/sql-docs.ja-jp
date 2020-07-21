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
ms.openlocfilehash: 0cd36cb2882659bff902d9830af0c5acefd98444
ms.sourcegitcommit: 04ba0ed3d860db038078609d6e348b0650739f55
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/27/2020
ms.locfileid: "85468977"
---
# <a name="analysis-services-personalization-extensions"></a>Analysis Services のパーソナル化拡張機能
  [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、プラグインアーキテクチャを実装するという概念の基盤です。 プラグイン アーキテクチャでは、新しいキューブ オブジェクトや機能を動的に開発し、他の開発者と簡単に共有することができます。 そのため、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] パーソナル化拡張機能により、次のことを実現できる機能が提供されます。  
  
-   **動的な設計と配置**パーソナル化拡張機能を設計して展開するとすぐに [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、ユーザーは次のユーザーセッションの開始時にオブジェクトと機能にアクセスできます。  
  
-   **インターフェイスの独立**パーソナル化拡張機能の作成に使用するインターフェイスに関係なく [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 、ユーザーは任意のインターフェイスを使用してオブジェクトや機能にアクセスできます。  
  
-   **セッションコンテキスト** [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、既存のインフラストラクチャ内のパーマネントオブジェクトではなく、キューブを再処理する必要はありません。 この機能は、ユーザーがデータベースに接続したときにそのユーザー用に公開および作成され、そのユーザー セッションの間だけ使用できます。  
  
-   **迅速な配布**[!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]この拡張機能を検索する場所や方法を詳細に説明する必要なく、パーソナル化拡張機能を他のソフトウェア開発者と共有します。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能の用途はさまざまです。 たとえば、会社の売上にさまざまな通貨が使用されているとします。 この場合、キューブにアクセスしている人物の現地通貨で連結売上を返す計算されるメンバーを作成します。 このメンバーをパーソナル化拡張機能として作成します。 その後、この計算されるメンバーをユーザー グループと共有します。 共有すると、ユーザーはサーバーに接続するとすぐに計算されるメンバーにアクセスできるようになります。 ユーザーは、計算されるメンバーの作成に使用されたインターフェイスと同じインターフェイスを使用していなくてもアクセスできます。  
  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)]パーソナル化拡張機能は、既存のマネージアセンブリアーキテクチャに対する単純で洗練された変更であり、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120))オブジェクトモデル、多次元式 (MDX) 構文、およびスキーマ行セット全体で公開されます。  
  
## <a name="logical-architecture"></a>論理アーキテクチャ  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能のアーキテクチャは、マネージド アセンブリ アーキテクチャと次の 4 つの基本要素に基づいています。  
  
 [PlugInAttribute] カスタム属性  
 サービスを開始すると、は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 必要なアセンブリを読み込み、 [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb678014(v=sql.120))カスタム属性を持つクラスを特定します。  
  
> [!NOTE]  
>  [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] では、カスタム属性は、コードを記述して実行時の動作を指定する方法と定義されています。 詳細については、MSDN の開発者ガイドの「属性の[概要](https://go.microsoft.com/fwlink/?LinkId=82929)」を参照してください [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 。  
  
 [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb678014(v=sql.120))カスタム属性を持つすべてのクラスで、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 既定のコンストラクターが呼び出されます。 起動時にすべてのコンストラクターを呼び出すと、新しいオブジェクトの作成元となる、ユーザー操作に依存しない共通の場所が提供されます。  
  
 クラスコンストラクターは、パーソナル化拡張機能の作成と管理に関する情報の小さなキャッシュを構築するだけでなく、通常は[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))イベントと[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))イベントをサブスクライブします。このような場合は、 これらのイベントをサブスクライブしないと、共通言語ランタイム (CLR) のガベージ コレクターによって、誤ってクラスにクリーンアップのマークが付けられる可能性があります。  
  
 セッション コンテキスト  
 パーソナル化拡張機能に基づくオブジェクトの場合、クライアント セッション中に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] によって実行環境が作成され、この環境でほとんどのオブジェクトが動的に作成されます。 他の CLR アセンブリと同様に、この実行環境からも他の関数やストアド プロシージャにアクセスできます。 ユーザーセッションが終了すると、は [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] 動的に作成されたオブジェクトを削除し、実行環境を閉じます。  
  
 イベント  
 オブジェクトの作成は、セッション イベント `On-Cube-OpenedCubeOpened` および `On-Cube-ClosingCubeClosing` によってトリガーされます。  
  
 クライアントとサーバー間の通信は、特定のイベントを介して行われます。 このイベントによって、クライアントのオブジェクトが作成される状況がクライアントで認識されるようになります。 クライアントの環境は、セッション イベントとキューブ イベントという 2 つのイベント セットを使用して動的に作成されます。  
  
 セッション イベントは、サーバー オブジェクトに関連付けられます。 クライアントがサーバーにログオンすると、に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] よってセッションが作成され、 [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))イベントがトリガーされます。 クライアントがサーバー上のセッションを終了すると、に [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] よって[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))イベントがトリガーされます。  
  
 キューブ イベントは、接続オブジェクトに関連付けられます。 キューブに接続すると、 [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb630581(v=sql.120))イベントがトリガーされますが、 キューブを閉じるか、別のキューブに変更することによって、キューブへの接続を閉じると、 [microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb630371(v=sql.120))イベントがトリガーされます。  
  
 トレーサビリティとエラー処理  
 [!INCLUDE[ssSqlProfiler](../../../includes/sssqlprofiler-md.md)] を使用すると、すべての操作をトレースできます。 未処理のエラーは、Windows イベント ログにレポートされます。  
  
 すべてのオブジェクトの作成および管理はこのアーキテクチャに依存せず、オブジェクトの開発者が責任を負います。  
  
## <a name="infrastructure-foundations"></a>インフラストラクチャの基盤  
 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] のパーソナル化拡張機能は、既存のコンポーネントに基づいています。 次に、パーソナル化拡張機能を実現する強化や改善の概要を示します。  
  
### <a name="assemblies"></a>アセンブリ  
 カスタム属性[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb678014(v=sql.120))をカスタムアセンブリに追加して、 [!INCLUDE[ssASnoversion](../../../includes/ssasnoversion-md.md)] パーソナル化拡張機能クラスを識別することができます。  
  
### <a name="changes-to-the-adomdserver-object-model"></a>AdomdServer オブジェクト モデルへの変更  
 [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms131779(v=sql.120))オブジェクトモデルの次のオブジェクトが、モデルに対して強化または追加されています。  
  
#### <a name="new-adomdconnection-class"></a>新しい AdomdConnection クラス  
 [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb678193(v=sql.120))クラスは新しく追加され、プロパティとイベントの両方を介していくつかのパーソナル化拡張機能を公開します。  
  
 **プロパティ**  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll *](/previous-versions/sql/sql-server-2014/bb678099(v=sql.120))は、現在の接続のセッション Id を表す読み取り専用の文字列値です。 SessionID * です。  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll *。](/previous-versions/sql/sql-server-2014/bb677433(v=sql.120))現在のセッションに関連付けられているクライアントカルチャへの読み取り専用の参照です。  
  
-   Microsoft.analysisservices.sharepoint.integration.dll * は、現在のユーザーを表す id インターフェイスへの読み取り専用の参照です。[ユーザー * です](/previous-versions/sql/sql-server-2014/bb630315(v=sql.120))。  
  
 **イベント**  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll が開かれています。](/previous-versions/sql/sql-server-2014/bb630581(v=sql.120))  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll が失われています。](/previous-versions/sql/sql-server-2014/bb630371(v=sql.120))  
  
#### <a name="new-properties-in-the-context-class"></a>Context クラスの新しいプロパティ  
 [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143353(v=sql.120))クラスには、次の2つの新しいプロパティがあります。  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll *](/previous-versions/sql/sql-server-2014/bb678098(v=sql.120))(新しいサーバーオブジェクトへの読み取り専用の参照) を表示します。  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll *](/previous-versions/sql/sql-server-2014/bb630975(v=sql.120))(新しい[microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb678193(v=sql.120))オブジェクトへの読み取り専用の参照)。.......... 接続 *。  
  
#### <a name="new-server-class"></a>新しい Server クラス  
 [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/bb677955(v=sql.120))クラスは新規で、クラスのプロパティとイベントの両方を通じていくつかのパーソナル化拡張機能を公開します。  
  
 **プロパティ**  
  
-   [Microsoft.AnalysisServices.AdomdServer.Server.Name *](/previous-versions/sql/sql-server-2014/bb677694(v=sql.120))、サーバー名を表す読み取り専用の文字列値。  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll *](/previous-versions/sql/sql-server-2014/bb677437(v=sql.120))。サーバーに関連付けられているグローバルカルチャへの読み取り専用の参照です。  
  
 **イベント**  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll が開かれました。](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))  
  
-   [Microsoft.analysisservices.sharepoint.integration.dll を終了しています。](/previous-versions/sql/sql-server-2014/bb630427(v=sql.120))  
  
#### <a name="adomdcommand-class"></a>AdomdCommand クラス  
 [Microsoft.analysisservices.sharepoint.integration.dll](/previous-versions/sql/sql-server-2014/ms143286(v=sql.120))クラスでは、次の MDX コマンドがサポートされるようになりました。  
  
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
  
  

---
title: "SQL Server Management Studio で DMX クエリを作成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: analysis-services
ms.service: 
ms.component: data-mining
ms.reviewer: 
ms.suite: sql
ms.technology:
- analysis-services
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- templates [Analysis Services], queries
- SQL Server Management Studio [Analysis Services], DMX queries
- predictions [Analysis Services], DMX prediction queries
- predictions [DMX]
- prediction queries [DMX]
- queries [DMX], prediction queries
- mining models [Analysis Services], DMX
ms.assetid: 568ce40a-1f53-47eb-8c79-14347cdfde83
caps.latest.revision: 43
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 51a8ea188eb54adf0ac208225dd7c5fda417178c
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio で DMX クエリを作成する
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] には、マイニング モデルおよびマイニング構造に対する、予測クエリ、コンテンツ クエリ、およびデータ定義クエリを作成できる一連の機能が用意されています。  
  
-   グラフィカルな予測クエリ ビルダーは、 [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] と [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]の両方で使用でき、予測クエリを記述し、データ セットをモデルにマッピングするプロセスを簡略化します。  
  
-   テンプレート エクスプローラーに用意されているクエリ テンプレートを使用すると、さまざまな種類の予測クエリなど、さまざまな種類の DMX クエリの作成をすぐに開始できます。 テンプレートには、コンテンツ クエリ用、入れ子になったデータ セットを使用したクエリ用、マイニング構造からケースを返すクエリ用だけでなく、データ定義クエリ用もあります。  
  
-   MDX および DMX のクエリ ペインのメタデータ エクスプローラーには、DMX 関数の一覧のほかに、使用できるモデルと構造の一覧が表示されます。それらをクエリ ビルダーにドラッグ アンド ドロップできます。 この機能を使用すると、正しいオブジェクト名を入力することなく簡単に指定できます。  
  
 ここでは、メタデータ エクスプローラーと DMX クエリ エディターを使用して、DMX クエリを作成する方法について説明します。  
  
##  <a name="BKMK_Templates"></a> DMX クエリ テンプレート  
 基本的な DMX クエリを作成するためのテンプレートは、テンプレート エクスプローラーから利用できます。 **DMX** フォルダーには、データ マイニング テンプレートが含まれています。テンプレートは、次のカテゴリに分類されます。  
  
-   **モデル コンテンツ**  
  
-   **モデル管理**  
  
-   **予測クエリ**  
  
-   **構造コンテンツ**  
  
 頻繁に実行するクエリまたはコマンドのカスタム テンプレートを作成することもできます。  
  
## <a name="xmla-query-templates"></a>XMLA クエリ テンプレート  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] には、XMLA クエリのテンプレートも用意されています。  
  
 XMLA と DMX を使用して実行できるクエリの種類は一部重複しています。 たとえば、モデル コンテンツ クエリは DMX またはデータ マイニング スキーマ行セットを使用して作成できますが、スキーマ行セットには DMX コンテンツ クエリでは公開されない情報が含まれている場合があります。  
  
 また、DMX と XMLA での操作の処理方法には、いくつかの重要な違いがあります。 たとえば、XMLA を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体のバックアップなどの管理操作を実行できますが、DMX には [EXPORT (DMX)](../../dmx/export-dmx.md) という簡単なコマンドが用意されています。1 つのマイニング モデルをバックアップする場合は、このコマンドの方が適しています。  
  
##  <a name="BKMK_Building_Queries"></a> DMX クエリの作成と実行  
  
#### <a name="open-a-new-dmx-query-window"></a>新しい DMX クエリ ウィンドウを開く  
  
1.  **で** [新しいクエリ] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]をクリックし、 **[新しい分析サーバー DMX クエリ]**を選択します。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスが表示されたら、操作するマイニング モデルが含まれている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを選択します。  
  
#### <a name="open-template-explorer"></a>テンプレート エクスプローラーを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]**をクリックします。  
  
2.  **[分析サーバー]** をクリックして、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に適用するテンプレートのツリー ビューを表示します。  
  
#### <a name="apply-a-template-to-build-a-query"></a>テンプレートを適用したクエリの作成  
  
-   適切なクエリの種類を右クリックし、 **[開く]**をクリックします。  
  
-   または、テンプレートをクエリ エディターにドラッグします。  
  
-   また、 **[クエリ]**メニューの **[パラメーター値の指定]** オプションを使用して、クエリのパラメーターを入力することもできます。  
  
 テンプレートから特定の種類のクエリを作成する方法の例については、次の各トピックを参照してください。  
  
 [テンプレートからの単一予測クエリの作成](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
  
 [マイニング モデルのコンテンツ クエリの作成](../../analysis-services/data-mining/create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング クエリ ツール](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [データ マイニング拡張機能 &#40;DMX&#41; リファレンス](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  


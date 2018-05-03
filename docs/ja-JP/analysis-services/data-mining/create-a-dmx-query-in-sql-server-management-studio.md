---
title: SQL Server Management Studio で DMX クエリを作成 |Microsoft ドキュメント
ms.date: 05/01/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: data-mining
ms.topic: article
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 939d21c596a3f023afaae6931ba1c53efe0ab85b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="create-a-dmx-query-in-sql-server-management-studio"></a>SQL Server Management Studio で DMX クエリを作成する
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]一連の予測クエリ、コンテンツ クエリ、およびマイニング モデル、マイニング構造に対するデータ定義クエリを作成するための機能を提供します。  
  
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
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]XMLA クエリ テンプレートも提供します。  
  
 XMLA と DMX を使用して実行できるクエリの種類は一部重複しています。 たとえば、モデル コンテンツ クエリは DMX またはデータ マイニング スキーマ行セットを使用して作成できますが、スキーマ行セットには DMX コンテンツ クエリでは公開されない情報が含まれている場合があります。  
  
 また、DMX と XMLA での操作の処理方法には、いくつかの重要な違いがあります。 たとえば、XMLA を使用して、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベース全体のバックアップなどの管理操作を実行できますが、DMX には [EXPORT (DMX)](../../dmx/export-dmx.md) という簡単なコマンドが用意されています。1 つのマイニング モデルをバックアップする場合は、このコマンドの方が適しています。  
  
##  <a name="BKMK_Building_Queries"></a> DMX クエリの作成と実行  
  
#### <a name="open-a-new-dmx-query-window"></a>新しい DMX クエリ ウィンドウを開く  
  
1.  **で** [新しいクエリ] [!INCLUDE[ssManStudio](../../includes/ssmanstudio-md.md)]をクリックし、 **[新しい分析サーバー DMX クエリ]** を選択します。  
  
2.  **[サーバーへの接続]** ダイアログ ボックスが表示されたら、操作するマイニング モデルが含まれている [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスを選択します。  
  
#### <a name="open-template-explorer"></a>テンプレート エクスプローラーを開く  
  
1.  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]で、 **[表示]** メニューの **[テンプレート エクスプローラー]** をクリックします。  
  
2.  **[分析サーバー]** をクリックして、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に適用するテンプレートのツリー ビューを表示します。  
  
#### <a name="apply-a-template-to-build-a-query"></a>テンプレートを適用したクエリの作成  
  
-   適切なクエリの種類を右クリックし、 **[開く]** をクリックします。  
  
-   または、テンプレートをクエリ エディターにドラッグします。  
  
-   また、 **[クエリ]** メニューの **[パラメーター値の指定]** オプションを使用して、クエリのパラメーターを入力することもできます。  
  
 テンプレートから特定の種類のクエリを作成する方法の例については、次の各トピックを参照してください。  
  
 [テンプレートから単一予測クエリを作成します。](../../analysis-services/data-mining/create-a-singleton-prediction-query-from-a-template.md)  
  
 [マイニング モデルに対するコンテンツ クエリを作成します。](../../analysis-services/data-mining/create-a-content-query-on-a-mining-model.md)  
  
## <a name="see-also"></a>参照  
 [データ マイニング クエリ ツール](../../analysis-services/data-mining/data-mining-query-tools.md)   
 [データ マイニング拡張機能 (&) #40";"DMX"&"#41;参照](../../dmx/data-mining-extensions-dmx-reference.md)  
  
  

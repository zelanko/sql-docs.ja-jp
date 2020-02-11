---
title: MDX クエリエディター (Analysis Services-多次元データ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.mdx.f1
helpviewer_keywords:
- Query Editor [MDX]
- MDX Query Editor
ms.assetid: 777f2c23-1c1c-4b72-9d19-48a4866551f8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 579af162998ffaa7c9483a6e6d29a87f98e96fac
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66077878"
---
# <a name="mdx-query-editor-analysis-services---multidimensional-data"></a>MDX クエリ エディター (Analysis Services - 多次元データ)
  MDX クエリ エディターを使用すると、多次元式 (MDX) 言語で記述されたステートメントおよびスクリプトを作成および実行できます。  
  
## <a name="features"></a>[機能]  
  
-   MDX クエリ エディターのクエリ エディター ペインに、スクリプトを入力します。  
  
-   スクリプトを実行するには、 **F5**キーを押すか、ツール バーの **[実行]** をクリックします。または、 **[クエリ]** メニューの **[実行]** をクリックします。 コードの一部だけが選択されている場合、その部分だけが実行されます。 コードが選択されていない状態では、MDX クエリ エディターの内容全体が実行されます。  
  
-   メタデータ ペインには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに格納されているキューブなどのオブジェクトのメタデータが表示されます。  
  
-   MDX 構文のヘルプを表示するには、MDX クエリ エディター内でキーワードを選択し、 **F1**キーを押します。  
  
-   MDX 構文のダイナミック ヘルプを表示するには、 **[ヘルプ]** メニューの **[ダイナミック ヘルプ]** をクリックしてダイナミック ヘルプ コンポーネントを開きます。 ダイナミック ヘルプの場合、キーワードをクエリ エディターに入力すると、ヘルプ トピックが **[ダイナミック ヘルプ]** ウィンドウに表示されます。  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>[SQL Server Analysis Services エディター] ツール バー  
 MDX クエリ エディターが開いているときは、次の表に示すボタンを備えた [ [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] エディター] ツール バーが表示されます。  
  
|期間|定義|  
|----------|----------------|  
|**接続する**|
  **インスタンスへの接続を確立するための** [サーバーへの接続] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ダイアログ ボックスを開きます。|  
|**切断**|MDX クエリ エディターと [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの接続を解除します。|  
|**接続の変更**|別の **インスタンスへの接続を確立するための** [サーバーへの接続] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ダイアログ ボックスを開きます。|  
|**現在の接続を使用した新しいクエリ**|現在の MDX クエリ エディター ウィンドウの接続情報を使用して、新しい MDX クエリ エディター ウィンドウを開きます。|  
|**使用できるデータベース**|接続を同じインスタンス上の別の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに変更します。|  
|**おい**|選択されているコードを実行します。コードが選択されていない場合は、MDX クエリ エディター内のコード全体を実行します。|  
|**分解**|選択されているコードの構文をチェックします。 コードが選択されていない場合は、MDX クエリ エディター ウィンドウ内のコード全体の構文をチェックします。|  
|**実行中のクエリの取り消し**|キャンセル要求をサーバーに送信します。 即座にキャンセルできないクエリもあります。そのようなクエリは、適切なキャンセル条件が整うまでキャンセルできません。 クエリが取り消されると、トランザクションがロールバックされる間に遅延が発生することがあります。|  
  
## <a name="mdx-query-editor-window"></a>MDX クエリ エディター ウィンドウ  
 MDX クエリ エディター ウィンドウでは、次の表に示すオプションを使用できます。  
  
|期間|定義|  
|----------|----------------|  
|**クエリ エディター ウィンドウ**|MDX クエリ エディターで実行される MDX ステートメントおよびスクリプトを入力します。<br /><br /> クエリ エディターのコンテキスト メニューには、次のオプションがあります。<br /><br /> **切り取り**: 現在の選択範囲をクリップボードにコピーし、クエリエディターウィンドウから選択を削除します。<br /><br /> **コピー**: 現在の選択項目をクリップボードにコピーします。<br /><br /> **貼り付け**: クリップボードの内容を現在の選択範囲に貼り付けます。<br /><br /> [**接続**]: [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスへの接続を確立するための [**サーバーへの接続**] ダイアログボックスを開きます。<br /><br /> **切断**: 現在のクエリエディターを[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスから切断します。<br /><br /> **すべてのクエリを切断**: 現在開いているすべてのクエリエディターを切断します。<br /><br /> [**接続の変更**]: 別[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]のインスタンスへの接続を確立するために、[**サーバーへの接続**] ダイアログボックスを開きます。<br /><br /> [**オブジェクトエクスプローラーでサーバーを開く**] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] : 現在のクエリエディターが接続されているインスタンスを**オブジェクトエクスプローラー**で開きます。<br /><br /> **Execute**: 選択したコードを実行します。コードが選択されていない場合は、現在のクエリエディターでコード全体を実行します。<br /><br /> [**プロパティウィンドウ]**: 現在のクエリ[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]ウィンドウのに [**プロパティ**] ウィンドウが表示されます。<br /><br /> [**クエリオプション**]: [**クエリオプション**] ダイアログボックスが表示されます。|  
|**メタデータ ウィンドウ**|現在接続されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのメタデータを表示します。|  
|**Cube**|現在接続されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内のキューブを選択して、キューブに関連付けられているメタデータを **[メタデータ]** タブに表示します。|  
|**Metadata**|
  **[キューブ]** で選択されているキューブのメタデータ (メジャー グループとメジャー、主要業績評価指標、ディメンション、階層、レベル、メンバー、およびメンバー プロパティなど) を表示します。 オブジェクトの完全修飾キーを取得するには、次のどちらかの操作を行います。<br /><br /> オブジェクトを **[メタデータ]** タブからクエリ ペインにドラッグします。<br /><br /> オブジェクトを右クリックし、 **[コピー]** をクリックします。次に、クエリ ペインを右クリックし、 **[貼り付け]** をクリックします。|  
|**関数**|MDSCHEMA_FUNCTIONS スキーマ行セットから取得された、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースで使用できる MDX 関数のメタデータを表示します。 関数の構文を取得するには、次のどちらかの操作を行います。<br /><br /> オブジェクトを **[関数]** タブからクエリ ペインにドラッグします。<br /><br /> 関数を右クリックし、 **[コピー]** をクリックします。次に、クエリ ペインを右クリックし、 **[貼り付け]** をクリックします。|  
|**[結果] ウィンドウ**|MDX ステートメントまたはスクリプトの結果がグリッドに表示されます。|  
|**[メッセージ] ウィンドウ**|MDX ステートメントまたはスクリプトの実行に関する情報が表示されます。 たとえば、実行中に発生したエラーや、実行後に取得されたセルの数などが表示されます。|  
  
  

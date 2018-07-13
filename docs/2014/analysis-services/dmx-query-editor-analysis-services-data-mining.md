---
title: DMX クエリ エディター (Analysis Services - データ マイニング) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.sqlserverstudio.startpage.dmx.f1
ms.assetid: 7ac877a1-0f29-46b9-9a51-73b02172bef1
caps.latest.revision: 21
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 1c1efcb4ecef6c311882b471a56535543bcc25b1
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37236062"
---
# <a name="dmx-query-editor-analysis-services---data-mining"></a>DMX クエリ エディター (Analysis Services - データ マイニング)
  DMX クエリ エディターを使用すると、データ マイニング拡張機能 (DMX) 言語で記述されたステートメントを作成したり実行したりできます。  
  
## <a name="features"></a>[機能]  
  
-   DMX クエリ エディターのクエリ エディター ペインに、スクリプトを入力します。  
  
-   スクリプトを実行するには、 **F5**キーを押すか、ツール バーまたは **[クエリ]** メニューの **[実行]** をクリックします。 コードの一部だけが選択されている場合、その部分だけが実行されます。 コードが選択されていない状態では、MDX クエリ エディターの内容全体が実行されます。  
  
-   メタデータ ペインには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに格納されているキューブなどのオブジェクトのメタデータが表示されます。  
  
-   DMX 構文のヘルプを表示するには、DMX クエリ エディター内でキーワードを選択し、 **F1**キーを押します。  
  
-   DMX 構文のダイナミック ヘルプを表示するには、 **[ヘルプ]** メニューの **[ダイナミック ヘルプ]** メニューをクリックしてダイナミック ヘルプ コンポーネントを開きます。 ダイナミック ヘルプの場合、キーワードをクエリ エディターに入力すると、ヘルプ トピックが **[ダイナミック ヘルプ]** ウィンドウに表示されます。  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>[SQL Server Analysis Services エディター] ツール バー  
 DMX クエリ エディターが開いているときは、次の表に示すボタンを備えた **[SQL Server Analysis Services エディター]** ツール バーが表示されます。  
  
|項目|定義|  
|----------|----------------|  
|**Connect**|Analysis Services インスタンスへの接続を確立するための **[サーバーへの接続]** ダイアログ ボックスを開きます。|  
|**[接続解除]**|DMX クエリ エディターと [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの接続を解除します。|  
|**[接続の変更]**|別の **インスタンスへの接続を確立するための** [サーバーへの接続] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ダイアログ ボックスを開きます。|  
|**[新しいクエリを現在の接続で実行]**|現在の DMX クエリ エディター ウィンドウの接続情報を使用して、新しい DMX クエリ エディター ウィンドウを開きます。|  
|**[使用できるデータベース]**|接続を同じインスタンス上の別の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに変更します。|  
|**実行**|選択されているコードを実行します。コードが選択されていない場合は、DMX クエリ エディター内のコード全体を実行します。|  
|**解析**|選択されているコードの構文をチェックします。 コードが選択されていない場合は、DMX クエリ エディター ウィンドウのコード全体の構文をチェックします。|  
|**[クエリ実行のキャンセル]**|キャンセル要求をサーバーに送信します。 即座にキャンセルできないクエリもあります。そのようなクエリは、適切なキャンセル条件が整うまでキャンセルできません。 キャンセル時は、トランザクションがロールバックされる間に遅延が発生することがあります。|  
  
## <a name="dmx-query-editor-window"></a>DMX クエリ エディター ウィンドウ  
 DMX クエリ エディター ウィンドウでは、次の表に示すオプションを使用できます。  
  
|項目|定義|  
|----------|----------------|  
|**クエリ エディター ウィンドウ**|DMX クエリ エディターで実行される DMX ステートメントおよびスクリプトを入力します。<br /><br /> クエリ エディターのコンテキスト メニューには、次のオプションがあります。<br /><br /> **切り取り**: 現在の選択範囲をクリップボードにコピーし、クエリ エディター ウィンドウから選択範囲を削除します。<br /><br /> **[コピー]**: 現在選択している部分をクリップボードにコピーします。<br /><br /> **貼り付け**: 現在の選択項目のクリップボードの内容を貼り付けます。<br /><br /> **[接続]**: [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を確立するための **[サーバーへの接続]** ダイアログ ボックスを開きます。<br /><br /> **切断**: 現在のクエリ エディターからの切断、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス。<br /><br /> **すべてのクエリの切断**: すべての開いているクエリ エディターの接続解除します。<br /><br /> **接続を変更する**: 開きます、**サーバーへの接続**ダイアログ ボックスで、さまざまなへの接続を確立するために、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス。<br /><br /> **オブジェクト エクスプ ローラーでサーバーを開く**: 開きます、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスで、現在のクエリ エディターが接続されている**オブジェクト エクスプ ローラー**します。<br /><br /> **実行**: 選択したコードを実行するか、コードが選択されていない場合は、現在のクエリ エディターでコード全体を実行します。<br /><br /> **[プロパティ] ウィンドウ**: 表示、**プロパティ**ウィンドウ[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の現在のクエリ ウィンドウ。<br /><br /> **クエリ オプション**: 表示、**クエリ オプション** ダイアログ ボックス。|  
|**[メタデータ] ウィンドウ**|現在接続されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースのメタデータを表示します。|  
|**Cube**|現在接続されている [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベース内のキューブを選択して、キューブに関連付けられているメタデータを **[メタデータ]** タブに表示します。|  
|**メタデータ**|**[キューブ]** で選択されているキューブのメタデータ (メジャー グループとメジャー、主要業績評価指標、ディメンション、階層、レベル、メンバー、およびメンバー プロパティなど) を表示します。 オブジェクトの完全修飾キーを取得するには、次のどちらかの操作を行います。<br /><br /> オブジェクトを **[メタデータ]** タブからクエリ ペインにドラッグします。<br /><br /> または。<br /><br /> オブジェクトを右クリックし、 **[コピー]** をクリックします。次に、クエリ ペインを右クリックし、 **[貼り付け]** をクリックします。|  
|**関数**|DMSCHEMA_MINING_FUNCTIONS スキーマ行セットから取得された、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースで使用できる DMX 関数のメタデータを表示します。<br /><br /> 関数の構文を取得するには、次のどちらかの操作を行います。<br /><br /> オブジェクトを **[関数]** タブからクエリ ペインにドラッグします。<br /><br /> または。<br /><br /> 関数を右クリックし、 **[コピー]** をクリックします。次に、クエリ ペインを右クリックし、 **[貼り付け]** をクリックします。|  
|**結果ウィンドウ**|DMX ステートメントの結果がグリッドに表示されます。|  
|**[メッセージ] ウィンドウ**|DMX ステートメントの実行に関する情報が表示されます。 たとえば、実行中に発生したエラーや、実行後に取得されたセルの数などが表示されます。|  
  
## <a name="see-also"></a>参照  
 [Analysis Services のデザイナーおよびダイアログ ボックス&#40;多次元データ&#41;](analysis-services-designers-and-dialog-boxes-multidimensional-data.md)   
 [データ マイニング拡張機能&#40;DMX&#41;リファレンス](/sql/dmx/data-mining-extensions-dmx-reference)   
 [MDX クエリ エディター &#40;Analysis Services - 多次元データ&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [XMLA クエリ エディター &#40;Analysis Services - 多次元データ&#41;](xmla-query-editor-analysis-services-multidimensional-data.md)   
 [クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [SQL Server Management Studio のキーボード ショートカット](../ssms/sql-server-management-studio-keyboard-shortcuts.md)   
 [メニューとショートカット キーをカスタマイズします。](../ssms/customize-menus-and-shortcut-keys.md)   
 [クエリ エディターでのコードの色分け](../relational-databases/scripting/color-coding-in-query-editors.md)  
  
  

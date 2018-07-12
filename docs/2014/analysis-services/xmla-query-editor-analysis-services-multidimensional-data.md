---
title: XMLA クエリ エディター (Analysis Services - 多次元データ) |Microsoft Docs
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
- sql12.asvs.editor.xmla.f1
helpviewer_keywords:
- XMLA Query Editor
- Query Editor [XMLA]
ms.assetid: 14623019-7839-4038-9d12-2f8953d2ec04
caps.latest.revision: 24
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 221ea55990b98a9723928f52cd5432f13760cc91
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37211432"
---
# <a name="xmla-query-editor-analysis-services---multidimensional-data"></a>XMLA クエリ エディター (Analysis Services - 多次元データ)
  XMLA クエリ エディターを使用すると、多次元式 (XMLA) 言語で記述されたステートメントおよびスクリプトを作成したり実行したりできます。  
  
## <a name="features"></a>[機能]  
  
-   XMLA クエリ エディターのクエリ エディター ペインに、スクリプトを入力します。  
  
-   スクリプトを実行するには、 **F5**キーを押すか、ツール バーの **[実行]** をクリックします。または、 **[クエリ]** メニューの **[実行]** をクリックします。 コードの一部だけが選択されている場合、その部分だけが実行されます。 コードが選択されていない状態では、XMLA クエリ エディターの内容全体が実行されます。  
  
-   メタデータ ペインには、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに格納されているキューブなどのオブジェクトのメタデータが表示されます。  
  
-   XMLA 構文のヘルプを表示するには、XMLA クエリ エディター内でキーワードを選択し、 **F1**キーを押します。  
  
-   XMLA 構文のダイナミック ヘルプを表示するには、 **[ヘルプ]** メニューの **[ダイナミック ヘルプ]** メニューをクリックしてダイナミック ヘルプ コンポーネントを開きます。 ダイナミック ヘルプの場合、キーワードをクエリ エディターに入力すると、ヘルプ トピックが **[ダイナミック ヘルプ]** ウィンドウに表示されます。  
  
## <a name="sql-server-analysis-services-editors-toolbar"></a>[SQL Server Analysis Services エディター] ツール バー  
 XMLA クエリ エディターが開いたとき、次のボタンを備えた **[SQL Server Analysis Services エディター]** ツール バーが表示されます。  
  
|項目|定義|  
|----------|----------------|  
|**Connect**|**インスタンスへの接続を確立するための** [サーバーへの接続] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ダイアログ ボックスを開きます。|  
|**[接続解除]**|XMLA クエリ エディターと [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスの接続を解除します。|  
|**[接続の変更]**|別の **インスタンスへの接続を確立するための** [サーバーへの接続] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] ダイアログ ボックスを開きます。|  
|**[新しいクエリを現在の接続で実行]**|現在の [XMLA クエリ エディター] ウィンドウの接続情報を使用して、新しい [XMLA クエリ エディター] ウィンドウを開きます。|  
|**[使用できるデータベース]**|接続を同じインスタンス上の別の [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースに変更します。|  
|**実行**|選択されているコードを実行します。コードが選択されていない場合は、XMLA クエリ エディター内のコード全体を実行します。|  
|**解析**|選択されているコードの構文をチェックします。 コードが選択されていない場合は、XMLA クエリ エディター ウィンドウのコード全体の構文をチェックします。|  
|**[クエリ実行のキャンセル]**|キャンセル要求をサーバーに送信します。 即座にキャンセルできないクエリもあります。そのようなクエリは、適切なキャンセル条件が整うまでキャンセルできません。 クエリが取り消されると、トランザクションがロールバックされる間に遅延が発生することがあります。|  
  
## <a name="xmla-query-editor-window"></a>[XMLA クエリ エディター] ウィンドウ  
 XMLA クエリ エディターでは次のオプションを使用できます。  
  
|項目|定義|  
|----------|----------------|  
|**クエリ エディター ウィンドウ**|XMLA クエリ エディターで実行される XMLA ステートメントおよびスクリプトを入力します。<br /><br /> クエリ エディターのコンテキスト メニューには、次のオプションがあります。<br /><br /> **切り取り**: 現在の選択範囲をクリップボードにコピーし、クエリ エディター ウィンドウから選択範囲を削除します。<br />**[コピー]**: 現在選択している部分をクリップボードにコピーします。<br />**貼り付け**: 現在の選択項目のクリップボードの内容を貼り付けます。<br />**[接続]**: [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] インスタンスへの接続を確立するための **[サーバーへの接続]** ダイアログ ボックスを開きます。<br />**切断**: 現在のクエリ エディターからの切断、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス。<br />**すべてのクエリの切断**: すべての開いているクエリ エディターの接続解除します。<br />**接続を変更する**: 開きます、**サーバーへの接続**ダイアログ ボックスで、さまざまなへの接続を確立するために、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンス。<br />**オブジェクト エクスプ ローラーでサーバーを開く**: 開きます、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]インスタンスで、現在のクエリ エディターが接続されている**オブジェクト エクスプ ローラー**します。<br />**実行**: 選択したコードを実行するか、コードが選択されていない場合は、現在のクエリ エディターでコード全体を実行します。<br />**[プロパティ] ウィンドウ**: 表示、**プロパティ**ウィンドウ[!INCLUDE[ssManStudioFull](../includes/ssmanstudiofull-md.md)]の現在のクエリ ウィンドウ。<br />**クエリ オプション**: 表示、**クエリ オプション** ダイアログ ボックス。|  
|**結果ウィンドウ**|XMLA ステートメントまたはスクリプトの結果がテキスト形式で表示されます。|  
|**[メッセージ] ウィンドウ**|XMLA ステートメントまたはスクリプトの実行に関する情報が表示されます。 たとえば、実行中に発生したエラーや、実行後に取得されたセルの数などが表示されます。|  
  
## <a name="see-also"></a>参照  
 [MDX クエリ エディター &#40;Analysis Services - 多次元データ&#41;](mdx-query-editor-analysis-services-multidimensional-data.md)   
 [DMX クエリ エディター &#40;Analysis Services - データ マイニング&#41;](dmx-query-editor-analysis-services-data-mining.md)   
 [クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)   
 [SQL Server Management Studio のキーボード ショートカット](../ssms/sql-server-management-studio-keyboard-shortcuts.md)  
  
  

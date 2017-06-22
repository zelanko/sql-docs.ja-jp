---
title: "スクリプトの生成 (SQL Server Management Studio) | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9711c617-3c68-4e5a-aea3-befc64d51524
caps.latest.revision: 6
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1bf73031c7e2e302d6174e6f21a005c3106f4cb2
ms.contentlocale: ja-jp
ms.lasthandoff: 06/22/2017

---
# <a name="generate-scripts-sql-server-management-studio"></a>スクリプトの生成 (SQL Server Management Studio)
  [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)][!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを生成するための 2 つのメカニズムが用意されています。 複数のオブジェクト用のスクリプトは、 **スクリプトの生成とパブリッシュ ウィザード**を使用して作成できます。 また、個々のオブジェクトまたは複数のオブジェクト用のスクリプトを、 **オブジェクト エクスプローラー** の **[スクリプト化]**メニューを使用して生成することもできます。  
  
1.  **Choose a method:**  [Generate and Publish Scripts Wizard](#GenPubScriptWiz), [Object Explorer Script As Menu](#OEScriptAsMenu)  
  
2.  **To use the Script As menu:**  [Script a Single Object](#ScriptSingleObject), [Script Two Objects Using Object Explorer](#ScriptTwoObjectsOE), [Script Two Objects Using Object Explorer Details](#ScriptTwoObjectsOED)  
  
## <a name="before-you-begin"></a>はじめに  
 要件に最も適したメカニズムを選択します。  
  
###  <a name="GenPubScriptWiz"></a> スクリプトの生成とパブリッシュ ウィザード  
 **スクリプトの生成とパブリッシュ ウィザード** を使用し、多数のオブジェクトの [!INCLUDE[tsql](../../includes/tsql-md.md)] スクリプトを作成できます。 このウィザードでは、データベース内の全オブジェクトのスクリプトを生成することも、選択したオブジェクトのサブセットのスクリプトを生成することもできます。 ウィザードには、権限、照合順序、制約、その他を含めるかどうかなど、スクリプトのさまざまなオプションがあります。 ウィザードの使用方法の詳細については、「 [スクリプトの生成とパブリッシュ ウィザード](../../relational-databases/scripting/generate-and-publish-scripts-wizard.md)」を参照してください。  
  
###  <a name="OEScriptAsMenu"></a> オブジェクト エクスプローラーの [スクリプト化] メニュー  
 オブジェクト エクスプローラーの **[スクリプト化]** メニューを使用し、単一オブジェクト、複数オブジェクト、または単一オブジェクトの複数のステートメントのスクリプトを作成できます。 いずれか 1 つのスクリプト タイプを選択できます。たとえば、オブジェクトの作成、変更、削除を選択できます。 スクリプトは、クエリ エディター ウィンドウ、ファイル、またはクリップボードに保存できます。 スクリプトは Unicode 形式で作成されます。  
  
##  <a name="ScriptSingleObject"></a> 単一のオブジェクトのスクリプトを生成するには  
 **単一のオブジェクトのスクリプトを生成するには**  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、スクリプト化するオブジェクトを含むデータベースを展開します。  
  
3.  オブジェクトのカテゴリを展開します。 たとえば、 **[テーブル]** または **[ビュー]** ノードを展開します。  
  
4.  オブジェクトを右クリックし、**[\<オブジェクト タイプ をスクリプト化]** をポイントします。たとえば、**[テーブルをスクリプト化]** をポイントします。  
  
5.  **[CREATE]** または **[ALTER]**などのスクリプト タイプをポイントします。  
  
6.  スクリプトを保存する場所を選択します。 **[新しいクエリ エディター ウィンドウ]** や **[クリップボード]**などを選択します。  
  
##  <a name="ScriptTwoObjectsOE"></a> オブジェクト エクスプローラーで 2 つのオブジェクトのスクリプトを生成するには  
 **オブジェクト エクスプローラーで 2 つのオブジェクトのスクリプトを生成するには**  
  
 プロシージャを削除した後でプロシージャを作成したり、テーブルを作成した後でテーブルを変更するなど、1 つのスクリプトで複数のオプションを実行させたい場合もあります。 テーブル、ビュー、ストアド プロシージャなど、異なる種類のオブジェクトを参照するスクリプトを作成する必要がある場合は、複数のオブジェクトのスクリプトを生成する次の手順を実行することもできます。  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、スクリプト化するオブジェクトを含むデータベースを展開します。  
  
3.  スクリプト化する最初のオブジェクトを右クリックし、**[\<オブジェクト タイプ をスクリプト化]** をポイントし、**[名前を付けて保存]** の選択項目で出力先として **[新しいクエリ エディター ウィンドウ]** を選択します。  
  
4.  スクリプトを作成する 2 番目のオブジェクトに移動します。  
  
5.  オブジェクトを右クリックして、**[\<オブジェクト タイプ をスクリプト化]** をポイントし、**[名前を付けて保存]** の選択項目で出力先として **[クリップボード]** を選択します。  
  
6.  最初のオブジェクトで開いたクエリ エディター ウィンドウに、2 番目のオブジェクトのスクリプトをクリップボードから貼り付けます。  
  
##  <a name="ScriptTwoObjectsOED"></a> [オブジェクト エクスプローラーの詳細] を使用して 2 つのオブジェクトのスクリプトを生成するには  
 **[オブジェクト エクスプローラーの詳細] で 2 つのオブジェクトのスクリプトを生成するには**  
  
 **[オブジェクト エクスプローラーの詳細]** ペインを使用し、同じカテゴリに含まれる複数のオブジェクトのスクリプトを生成できます。  
  
1.  オブジェクト エクスプローラーで、 [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] のインスタンスに接続し、そのインスタンスを展開します。  
  
2.  **[データベース]**を展開し、スクリプト化するオブジェクトを含むデータベースを展開します。  
  
3.  スクリプトを作成するオブジェクトの種類のカテゴリ ノード ( **[テーブル]** ノードなど) を展開します。  
  
4.  **F7** キーを押すか、 **[表示]**メニューの **[オブジェクト エクスプローラーの詳細]** をクリックして、 **[オブジェクト エクスプローラーの詳細]**ペインを開きます。  
  
5.  スクリプトを作成するオブジェクトのいずれかを左クリックします。  
  
6.  Ctrl キーを押しながら、スクリプトを作成する 2 番目のオブジェクトを左クリックします。  
  
7.  選択したオブジェクトのいずれかを右クリックし、**[\<オブジェクト タイプ をスクリプト化]** をクリックします。  
  
  

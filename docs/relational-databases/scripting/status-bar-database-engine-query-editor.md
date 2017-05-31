---
title: "ステータス バー (データベース エンジン クエリ エディター) | Microsoft Docs"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- database-engine
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7f2d6f4-bb94-4cf5-a096-c34397e679af
caps.latest.revision: 7
author: BYHAM
ms.author: rickbyh
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 34d7a9bfaf04f1ea7d201083201aa3c8a3895061
ms.contentlocale: ja-jp
ms.lasthandoff: 04/11/2017

---
# <a name="status-bar-database-engine-query-editor"></a>ステータス バー (データベース エンジン クエリ エディター)
  [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウのステータス バーでは、各ウィンドウが [!INCLUDE[ssDE](../../includes/ssde-md.md)] のどのインスタンスに接続しているかを色分けして示すことができます。  
  
1.  **Before you begin:**  [Status Bar Colors](#StatusBarColors)  
  
2.  **To set a server status color in:**  [Object Explorer](#SetOEServerColor), [Registered Server](#SetRegServerColor)  
  
3.  **To use a status color:**  [Open Query Editor Using a Server Color](#OpenServerColor), [Open a Query Editor Specifying a Status Color](#OpenSpecColor)  
  
##  <a name="StatusBarColors"></a> ステータス バーの色  
 **[オブジェクト エクスプローラー]** または **[登録済みサーバー]**の特定のサーバー ノードとステータス バーの色を関連付けることができます。 ステータス バーの色を指定できるのは、 [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続されているサーバー ノードのみで、他の SQL Server テクノロジのノードでは指定できません。 また、新しい [!INCLUDE[ssDE](../../includes/ssde-md.md)] クエリ エディター ウィンドウを [!INCLUDE[ssDE](../../includes/ssde-md.md)]のインスタンスに接続するたびに、作成したステータス バーの色を指定することもできます。 その後、サーバー ノードに定義された状態の色を使用してクエリ エディター ウィンドウを開くか、そのエディター ウィンドウに対して一意の色を指定することができます。  
  
 オブジェクト エクスプローラーのサーバー ノードに対して、作成したステータス バーの色を設定する場合、その設定を接続時に行う必要があります。 既存のサーバー ノードに関連付けられている色を変更するには、接続解除してから、新しい色を指定して再接続する必要があります。  
  
##  <a name="SetOEServerColor"></a> オブジェクト エクスプローラーでのサーバー状態の色の設定  
 **オブジェクト エクスプローラーでサーバー状態の色を設定するには**  
  
1.  **[オブジェクト エクスプローラー]**で、 **[接続]** ボタンをクリックし、次に **[データベース エンジン]**をクリックします。  
  
2.  **[サーバーへの接続]** ダイアログで、**[オプション >>]** を選択します。  
  
3.  **[作成した色を使用する]** チェック ボックスをオンにします。  
  
4.  色を選択するには、 **[選択]** ボタンをクリックします。  
  
5.  基本の色または作成した色を選択して、[OK] をクリックします。  
  
6.  残りの接続情報を入力して、 **[接続]** ボタンをクリックします。  
  
##  <a name="SetRegServerColor"></a> 登録済みサーバーの状態の色の設定  
 **登録済みサーバーの状態の色を設定するには**  
  
1.  **[登録済みサーバー]**で、サーバー ノードを右クリックして、 **[プロパティ]**をクリックします。  
  
2.  **[サーバー登録プロパティの編集]** ダイアログ ボックスで、 **[接続プロパティ]** タブをクリックします。  
  
3.  **[作成した色を使用する]** チェック ボックスをオンにします。  
  
4.  色を選択するには、 **[選択]** ボタンをクリックします。  
  
5.  基本の色または作成した色を選択して、[OK] をクリックします。  
  
6.  **[サーバー登録プロパティの編集]** ダイアログ ボックスで、 **[保存]** ボタンをクリックします。  
  
##  <a name="OpenServerColor"></a> サーバーの色を使用したエディターの起動  
 **サーバーの色を使用してエディター ウィンドウを開くには**  
  
-   **オブジェクト エクスプローラー** または **[登録済みサーバー]**でサーバー ノードを右クリックして、 **[新しいクエリ]**をクリックします。  
  
-   または、サーバー ノードを強調表示して、 **[新しいクエリ]** ツール バー ボタンをクリックします。  
  
-   エディター ウィンドウのステータス バーでは、関連付けられたサーバーに定義されている色が使用されます。  
  
##  <a name="OpenSpecColor"></a> 状態の色の指定によるエディターの起動  
 **状態の色を指定してエディター ウィンドウを開くには**  
  
-   **[ファイル]** メニューの **[新規作成]**をポイントし、 **[データベース エンジン クエリ]**をクリックします。  
  
-   **[サーバーへの接続]** ダイアログで、**[オプション >>]** を選択します。  
  
-   **[作成した色を使用する]** チェック ボックスをオンにします。  
  
-   色を選択するには、 **[選択]** ボタンをクリックします。  
  
-   基本の色または作成した色を選択して、[OK] をクリックします。  
  
-   残りの接続情報を入力して、 **[接続]** ボタンをクリックします。  
  
## <a name="see-also"></a>参照  
 [クエリおよびテキスト エディター &#40;SQL Server Management Studio&#41;](../../relational-databases/scripting/query-and-text-editors-sql-server-management-studio.md)  
  
  

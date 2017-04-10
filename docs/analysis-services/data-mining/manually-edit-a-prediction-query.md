---
title: "手動での予測クエリの編集 | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "予測クエリの変更"
  - "マイニング モデル予測 [Analysis Services], 予測クエリの変更"
  - "手動による予測クエリの変更 [Analysis Services]"
ms.assetid: 9f6a9298-49d5-4675-ad49-977a47dff5a6
caps.latest.revision: 17
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 17
---
# 手動での予測クエリの編集
  予測クエリ ビルダーでクエリのデザインを終えたら、データ マイニング デザイナーの **[マイニング モデル予測]** タブにあるクエリ テキスト ビューに切り替えて、クエリを変更できます。 画面の下部に、クエリ ビルダーによって作成されたクエリを含んでいるテキスト エディターが表示されます。  
  
 クエリ テキスト ビューに切り替えると、クエリへの追加を行う場合に便利です。 たとえば、WHERE 句や ORDER BY 句を追加できます。  
  
 予測クエリ ビルダーのグリッドを使用してオブジェクトおよび列の名前を挿入し、個々の予測関数の構文を設定してから、手動編集モードに切り替えて、パラメーター値を変更します。  
  
> [!NOTE]  
>  **クエリ テキスト** ビューから**デザイン** ビューに戻ると、**クエリ テキスト** ビューで行った変更は失われます。  
  
### クエリの変更  
  
1.  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーにある **[マイニング モデル予測]** タブで、**[SQL]** をクリックします。  
  
     画面の下部にあるグリッドが、クエリを含んでいるテキスト エディターに置き換わります。 このエディターでクエリの変更を入力できます。  
  
2.  クエリを実行するには、**[マイニング モデル]** メニューの **[結果]** をクリックするか、クエリ結果に切り替えるボタンをクリックします。  
  
    > [!NOTE]  
    >  作成したクエリが無効であれば、[結果] ウィンドウにはエラーも結果も表示されません。 **[デザイン]** ボタンをクリックするか、**[マイニング モデル]** メニューの **[デザイン]** または **[クエリ]** をクリックして問題を修正し、再度クエリを実行してください。  
  
## 参照  
 [データ マイニング クエリ](../../analysis-services/data-mining/data-mining-queries.md)   
 [予測クエリ ビルダー &#40;データ マイニング&#41;](../Topic/Prediction%20Query%20Builder%20\(Data%20Mining\).md)   
 [レッスン 6: 予測の作成と操作 &#40;基本的なデータ マイニング チュートリアル&#41;](../Topic/Lesson%206:%20Creating%20and%20Working%20with%20Predictions%20\(Basic%20Data%20Mining%20Tutorial\).md)  
  
  
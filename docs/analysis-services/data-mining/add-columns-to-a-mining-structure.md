---
title: "マイニング構造への列の追加 | Microsoft Docs"
ms.custom: ""
ms.date: "03/13/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "マイニング構造 [Analysis Services], 列"
  - "列 [データ マイニング], マイニング構造列"
  - "列の追加"
ms.assetid: 3f879344-9f66-4178-851a-e8c5ccccf4cb
caps.latest.revision: 30
author: "Minewiskan"
ms.author: "owend"
manager: "jhubbard"
caps.handback.revision: 30
---
# マイニング構造への列の追加
  データ マイニング ウィザードで定義したマイニング構造に列を追加するには、[!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] のデータ マイニング デザイナーを使用します。 マイニング構造の定義に使用したデータ ソース ビューに存在する列はどれでも追加できます。  
  
> [!NOTE]  
>  マイニング構造に列のコピーを複数追加することもできます。ただし、同じモデル内で 1 つの列のインスタンスが複数にならないようにし、ソースと派生列の間に誤った相関関係ができるのを防ぐ必要があります。  
  
### マイニング構造に列を追加するには  
  
1.  データ マイニング デザイナーで **[マイニング構造]** タブを選択します。  
  
2.  マイニング構造を右クリックして **[列の追加]** を選択します。  
  
     **[列の選択]** ダイアログ ボックスが開きます。  
  
3.  **[基になるテーブル]** で、列が格納されているデータ ソース ビュー内のテーブルを選択します。  
  
4.  **[基になる列]** で、マイニング構造に追加する列を選択します。  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
> [!NOTE]  
>  既に存在する列を追加すると、構造にコピーが追加され、その名前に "1" が付加されます。 コピーされた列の名前をわかりやすい名前に変更するには、マイニング構造列の **[名前]** プロパティに新しい名前を入力します。  
  
## 参照  
 [マイニング構造のタスクと操作方法](../../analysis-services/data-mining/mining-structure-tasks-and-how-tos.md)  
  
  
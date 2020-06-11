---
title: '[入れ子になったテーブルキー列の選択] ダイアログボックス ([マイニング構造] ビュー) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
author: minewiskan
ms.author: owend
ms.openlocfilehash: 79dd1eca0d12061cef0ab5453933df08f78954d1
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84538354"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a>[入れ子になったテーブル キー列の選択] ダイアログ ボックス ([マイニング構造] ビュー)
  **[入れ子になったテーブル キー列の選択]** ダイアログ ボックスを使用すると、新しい入れ子になったテーブルのキーとして動作する列を指定できます。 ダイアログ ボックスを閉じると、指定したキー列を含む新しいテーブルがマイニング構造に追加されます。 入れ子になったテーブルに新たに列を追加するには、構造を右クリックして **[列の追加]** をクリックします。 このダイアログ ボックスに含まれているオプションは、OLAP マイニング モデルを使用するか、リレーショナル マイニング モデルを使用するかによって異なります。  
  
## <a name="options"></a>オプション  
 **ソース テーブル**  
 マイニング モデルの基になるテーブルです。  
  
 このオプションは、リレーショナル マイニング モデルにのみ使用されます。  
  
 **ソース列**  
 入れ子になったテーブルのキーとして使用できる、基になるテーブル内の使用可能なすべての列の一覧です。  
  
 このオプションは、リレーショナル マイニング モデルにのみ使用されます。  
  
 **[列の型を表示]**  
 使用できる列のデータ型の一覧です。 データ型を選択または選択解除して、 **[基になる列]** 内の列の一覧をフィルタリングします。 オンになっているデータ型に一致する列だけが **[基になる列]** の一覧に表示されます。  
  
 このオプションは、リレーショナル マイニング モデルにのみ使用されます。  
  
 **属性**  
 入れ子になったテーブルのキーとして使用できる属性の一覧です。  
  
 このオプションは、OLAP マイニング モデルにのみ使用されます。  
  
## <a name="see-also"></a>参照  
 [マイニング構造ビュー &#40;データマイニングモデルデザイナー&#41;](mining-structure-view-data-mining-model-designer.md)  
  
  

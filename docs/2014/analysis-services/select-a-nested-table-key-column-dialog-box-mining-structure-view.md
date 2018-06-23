---
title: 選択、入れ子になったテーブル キー列 ダイアログ ボックス (マイニング構造 ビュー) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dm.miningmodeleditor.structure.addnestedtable.f1
helpviewer_keywords:
- Select a Nested Table Key Column dialog box
ms.assetid: f68b89a7-17df-45f8-ba7f-b458cd9b1ec3
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: d197434bbff97fa3fab1f1e2031c0b37b69d9ce1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071552"
---
# <a name="select-a-nested-table-key-column-dialog-box-mining-structure-view"></a>[入れ子になったテーブル キー列の選択] ダイアログ ボックス ([マイニング構造] ビュー)
  **[入れ子になったテーブル キー列の選択]** ダイアログ ボックスを使用すると、新しい入れ子になったテーブルのキーとして動作する列を指定できます。 ダイアログ ボックスを閉じると、指定したキー列を含む新しいテーブルがマイニング構造に追加されます。 入れ子になったテーブルに新たに列を追加するには、構造を右クリックして **[列の追加]** をクリックします。 このダイアログ ボックスに含まれているオプションは、OLAP マイニング モデルを使用するか、リレーショナル マイニング モデルを使用するかによって異なります。  
  
## <a name="options"></a>および  
 **ソース テーブル**  
 マイニング モデルの基になるテーブルです。  
  
 このオプションは、リレーショナル マイニング モデルにのみ使用されます。  
  
 **基になる列**  
 入れ子になったテーブルのキーとして使用できる、基になるテーブル内の使用可能なすべての列の一覧です。  
  
 このオプションは、リレーショナル マイニング モデルにのみ使用されます。  
  
 **列の型を表示します。**  
 使用できる列のデータ型の一覧です。 データ型を選択または選択解除して、 **[基になる列]** 内の列の一覧をフィルタリングします。 オンになっているデータ型に一致する列だけが **[基になる列]** の一覧に表示されます。  
  
 このオプションは、リレーショナル マイニング モデルにのみ使用されます。  
  
 **Attributes**  
 入れ子になったテーブルのキーとして使用できる属性の一覧です。  
  
 このオプションは、OLAP マイニング モデルにのみ使用されます。  
  
## <a name="see-also"></a>参照  
 [[マイニング構造] ビュー&#40;データ マイニング モデル デザイナー&#41;](mining-structure-view-data-mining-model-designer.md)  
  
  
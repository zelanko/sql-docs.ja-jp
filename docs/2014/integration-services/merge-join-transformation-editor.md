---
title: マージ結合変換エディター |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.mergejointransformation.f1
helpviewer_keywords:
- Merge Join Transformation Editor
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
caps.latest.revision: 30
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 1f548972d99242a4bc3d3423eeed748de2c31704
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36165572"
---
# <a name="merge-join-transformation-editor"></a>マージ結合変換エディター
  **[マージ結合変換エディター]** ダイアログ ボックスを使用すると、結合の種類、結合列、および結合によって組み合わされた 2 つの入力をマージするための出力列を指定できます。  
  
> [!IMPORTANT]  
>  マージ結合変換では、入力データが並べ替えられている必要があります。 この重要な要件の詳細については、「 [マージ変換およびマージ結合変換用にデータを並べ替える](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。  
  
 マージ結合変換の詳細については、「 [Merge Join Transformation](data-flow/transformations/merge-join-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[結合の種類]**  
 内部結合、左外部結合、または完全結合を使用するかどうかを指定します。  
  
 **[入力の入れ替え]**  
 **[入力の入れ替え]** ボタンを使用して、入力間の順序を切り替えます。 この選択は、左外部結合オプションで使用すると便利です。  
  
 **入力**  
 出力をマージする各列は、使用できる入力の一覧から最初に選択します。  
  
 入力は 2 つの個別のテーブルに表示されます。 出力に含める列を選択します。 テーブル間の結合を作成する列をドラッグします。 結合を削除するには、選択してから Del キーを押します。  
  
 **入力列**  
 選択した入力の使用できる列の一覧からマージする出力に含める列を選択します。  
  
 **[出力の別名]**  
 各出力列の別名を入力します。 既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [マージ変換およびマージ結合変換用のデータの並べ替え](data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [マージ結合変換を使用してデータセットを拡張します。](data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [マージ変換](data-flow/transformations/merge-transformation.md)   
 [全体結合変換](data-flow/transformations/union-all-transformation.md)  
  
  
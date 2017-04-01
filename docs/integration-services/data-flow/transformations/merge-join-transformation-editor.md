---
title: "マージ結合変換エディター | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.mergejointransformation.f1"
helpviewer_keywords: 
  - "マージ結合変換エディター"
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# マージ結合変換エディター
  **[マージ結合変換エディター]** ダイアログ ボックスを使用すると、結合の種類、結合列、および結合によって組み合わされた 2 つの入力をマージするための出力列を指定できます。  
  
> [!IMPORTANT]  
>  マージ結合変換では、入力データが並べ替えられている必要があります。 この重要な要件の詳細については、「[マージ変換およびマージ結合変換用にデータを並べ替える](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)」を参照してください。  
  
 マージ結合変換の詳細については、「 [Merge Join Transformation](../../../integration-services/data-flow/transformations/merge-join-transformation.md)」を参照してください。  
  
## オプション  
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
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [マージ変換およびマージ結合変換用にデータを並べ替える](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [マージ結合変換を使用してデータセットを拡張する](../../../integration-services/data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [マージ変換](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [全体結合変換](../../../integration-services/data-flow/transformations/union-all-transformation.md)  
  
  
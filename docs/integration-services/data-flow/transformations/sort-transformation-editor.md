---
title: "並べ替え変換エディター | Microsoft Docs"
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
  - "sql13.dts.designer.sorttransformation.f1"
helpviewer_keywords: 
  - "並べ替え変換エディター"
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# 並べ替え変換エディター
  **[並べ替え変換エディター]** ダイアログ ボックスを使用すると、並べ替える列を選択し、並べ替え順を設定して、重複する部分を削除するかどうかを指定できます。  
  
 並べ替え変換の詳細については、「 [Sort Transformation](../../../integration-services/data-flow/transformations/sort-transformation.md)」を参照してください。  
  
## オプション  
 **使用できる入力列**  
 このチェック ボックスを使用して、並べ替える列を指定します。  
  
 **名前**  
 使用できる各入力列の名前を表示します。  
  
 **パススルー**  
 並べ替えられる出力に列が含まれるかどうかを指定します。  
  
 **入力列**  
 各行に対して使用できる入力列の一覧から選択します。 選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。  
  
 **[出力の別名]**  
 各出力列の別名を入力します。 既定は入力列の名前です。一意のわかりやすい名前を付けることもできます。  
  
 **[並べ替えの種類]**  
 昇順で並べ替えるか、降順で並べ替えるかを示します。  
  
 **並べ替え順序**  
 列を並べ替える順序を示します。 各列に対して手動で設定する必要があります。  
  
 **[比較フラグ]**  
 文字列比較オプションについては、「[文字列データの比較](../../../integration-services/data-flow/comparing-string-data.md)」を参照してください。  
  
 **[重複した並べ替え値を含む行を削除する]**  
 指定された文字列比較オプションに基づいて、重複した列を変換出力にコピーするか、すべての重複部分に対して 1 つのエントリを作成するかを示します。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  
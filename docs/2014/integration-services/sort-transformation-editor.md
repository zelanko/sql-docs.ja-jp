---
title: 並べ替え変換エディター |Microsoft ドキュメント
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
- sql12.dts.designer.sorttransformation.f1
helpviewer_keywords:
- Sort Transformation Editor
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
caps.latest.revision: 24
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: b4dc4369d766a0a656cd0af32331a00c11e961b9
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36178466"
---
# <a name="sort-transformation-editor"></a>並べ替え変換エディター
  **[並べ替え変換エディター]** ダイアログ ボックスを使用すると、並べ替える列を選択し、並べ替え順を設定して、重複する部分を削除するかどうかを指定できます。  
  
 並べ替え変換の詳細については、「 [Sort Transformation](data-flow/transformations/sort-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **使用できる入力列**  
 このチェック ボックスを使用して、並べ替える列を指定します。  
  
 **Name**  
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
 文字列比較オプションについては、「 [文字列データの比較](data-flow/comparing-string-data.md)」を参照してください。  
  
 **[重複した並べ替え値を含む行を削除する]**  
 指定された文字列比較オプションに基づいて、重複した列を変換出力にコピーするか、すべての重複部分に対して 1 つのエントリを作成するかを示します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
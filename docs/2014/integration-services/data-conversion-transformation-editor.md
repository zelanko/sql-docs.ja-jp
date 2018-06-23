---
title: データ変換変換エディター |Microsoft ドキュメント
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
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
caps.latest.revision: 28
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9c5157175181c7a43a2c8e3209c23905a4129d2d
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36074641"
---
# <a name="data-conversion-transformation-editor"></a>データ変換変換エディター
  **[データ変換変換エディター]** ダイアログ ボックスを使用すると、変換対象の列や列の変換先のデータ型を選択したり、変換属性を設定したりできます。  
  
> [!NOTE]  
>  `FastParse`データ変換の変換の出力列のプロパティでは使用できません、**データ変換変換エディター**を使用して設定できますが、**詳細エディター**です。 このプロパティの詳細については、「 [変換のカスタム プロパティ](data-flow/transformations/transformation-custom-properties.md)」の「データ変換の変換」を参照してください。  
  
 データ変換の変換の詳細については、「 [データ変換の変換](data-flow/transformations/data-conversion-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **使用できる入力列**  
 変換対象の列のチェック ボックスを使用して選択します。 選択した列が入力列として下のテーブルに追加されます。  
  
 **入力列**  
 使用できる入力列の一覧から変換対象の列を選択します。 上記のチェック ボックスに、選択内容が反映されます。  
  
 **[出力の別名]**  
 それぞれの新しい列の別名を入力します。 既定値は`Copy of`後に入力列の名前。 ただし、一意のわかりやすい名前を選択できます。  
  
 **[データ型]**  
 一覧から利用可能なデータ型を選択します。 詳細については、「 [Integration Services Data Types](data-flow/integration-services-data-types.md)」を参照してください。  
  
 **Length**  
 文字列データの列の長さを設定します。  
  
 **Precision**  
 数値データの有効桁数を設定します。  
  
 **Scale**  
 数値データの小数点以下桁数を設定します。  
  
 **コード ページ**  
 DT_STR 型の列に適したコード ページを選択します。  
  
 **[エラー出力の構成]**  
 [[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [データ変換の変換を使用してデータを別のデータ型に変換する](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
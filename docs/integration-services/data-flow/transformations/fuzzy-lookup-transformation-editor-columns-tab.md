---
title: "あいまい参照変換エディター ([列] タブ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.fuzzylookuptransformation.columns.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: aaf45327-79e9-4760-9b4d-546ace91b5b4
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 487c138e91e1e0d3097432cf1c856fe2cdbcd609
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="fuzzy-lookup-transformation-editor-columns-tab"></a>[あいまい参照変換エディター]\ ([列] タブ)
  **[あいまい参照変換エディター]** ダイアログ ボックスの **[列]** タブを使用すると、入力列および出力列のプロパティを設定できます。  
  
 あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **使用できる入力列**  
 入力列をドラッグして、使用できる参照列に接続します。 これらの列は、サポートされているデータ型と一致する必要があります。 マッピングする行を選択して右クリックし、 [[リレーションシップの作成]](../../../integration-services/data-flow/transformations/create-relationships.md) ダイアログ ボックスでマッピングを編集します。  
  
 **名**  
 使用可能な入力列の名前が表示されます。  
  
 **パススルー**  
 変換先の出力に入力列を含めるかどうかを指定します。  
  
 **使用できる参照列**  
 チェック ボックスを使用して、あいまい参照操作を実行する列を選択します。  
  
 **参照列**  
 使用できる参照テーブル列の一覧から参照列を選択します。 選択内容が **[使用できる参照列]** テーブルのチェック ボックスに反映されます。 **[使用できる参照列]** テーブルの列を選択すると、返される一致行ごとに参照テーブル列の値を含む出力列が作成されます。  
  
 **出力の別名**  
 各参照列の出力の別名を入力します。 既定では、参照列の名前に数値のインデックス値が追加されます。一意のわかりやすい名前を付けることもできます。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [あいまい参照変換エディター &#40;参照テーブル タブ&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [あいまい参照変換エディター &#40;詳細設定タブ&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-advanced-tab.md)  
  
  

---
title: "あいまい参照変換エディター (詳細 タブ) |Microsoft ドキュメント"
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
- sql13.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 6036e6f61ef2bb3d0f974642fd6c595e2199f73b
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>[あいまい参照変換エディター] ([詳細設定] タブ)
  **[あいまい参照変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、あいまい参照のパラメーターを設定できます。  
  
 あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **参照ごとの出力に一致する項目の最大数**  
 変換で返される、各入力行の一致の最大数を指定します。 既定値は **1**です。  
  
 **類似性のしきい値**  
 スライダーを使用して、コンポーネント レベルの類似性のしきい値を設定します。 値を 1 に近づけるほど、参照元の値と参照先の値との類似性が高くなければ一致しないと見なされます。 しきい値を大きくすると、照合の対象となるレコードが少なくなるため、照合の速度が向上します。  
  
 **トークン区切り記号**  
 列の値をトークンにする際に使用される区切り記号を指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [あいまい参照変換エディター &#40;参照テーブル タブ&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [あいまい参照変換エディター &#40;列タブ&#41;](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  

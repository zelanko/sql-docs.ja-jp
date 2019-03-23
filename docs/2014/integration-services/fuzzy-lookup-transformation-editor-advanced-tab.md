---
title: あいまい参照変換エディター (詳細 タブ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.fuzzylookuptransformation.advanced.f1
helpviewer_keywords:
- Fuzzy Lookup Transformation Editor
ms.assetid: 0a2919be-2ea7-4c06-82b8-0ffad5f0dd83
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 0739bb7100e61147e0ba35cb1cc75b1367634924
ms.sourcegitcommit: 5a8678bf85f65be590676745a7fe4fcbcc47e83d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2019
ms.locfileid: "58376249"
---
# <a name="fuzzy-lookup-transformation-editor-advanced-tab"></a>[あいまい参照変換エディター] ([詳細設定] タブ)
  **[あいまい参照変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、あいまい参照のパラメーターを設定できます。  
  
 あいまい参照変換の詳細については、「 [Fuzzy Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[参照ごとの出力に対する最大一致数]**  
 変換で返される、各入力行の一致の最大数を指定します。 既定値は **1**です。  
  
 **[類似性のしきい値]**  
 スライダーを使用して、コンポーネント レベルの類似性のしきい値を設定します。 値を 1 に近づけるほど、参照元の値と参照先の値との類似性が高くなければ一致しないと見なされます。 しきい値を大きくすると、照合の対象となるレコードが少なくなるため、照合の速度が向上します。  
  
 **[トークン区切り記号]**  
 列の値をトークンにする際に使用される区切り記号を指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [あいまい参照変換エディター ([参照テーブル] タブ)](../../2014/integration-services/fuzzy-lookup-transformation-editor-reference-table-tab.md)   
 [あいまい参照変換エディター ([列] タブ)](../../2014/integration-services/fuzzy-lookup-transformation-editor-columns-tab.md)  
  
  

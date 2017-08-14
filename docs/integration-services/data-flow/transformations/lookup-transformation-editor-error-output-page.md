---
title: "[参照変換エディター]\\ ([エラー出力] ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.lookuptransformation.erroroutput.f1
ms.assetid: 15d53bb0-8be1-46fb-b459-04a397e75fac
caps.latest.revision: 14
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 120a040b37f3eae7e7ce4fc317f39434116f2ece
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lookup-transformation-editor-error-output-page"></a>[参照変換エディター]\ ([エラー出力] ページ)
  **[参照変換エディター]** ダイアログ ボックスの **[エラー出力]** ページを使用すると、エラー処理オプションを指定できます。  
  
 参照変換の詳細については、「 [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **入力/出力**  
 入力の名前を表示します。  
  
 **列**  
 使用されていません。  
  
 **[エラー]**  
 参照データセットに一致するエントリがない行を処理したときに発生させるエラーの種類を指定します。  
  
-   エラーを無視し、行を出力にダイレクトします。  
  
-   行をエラー出力にリダイレクトします。  
  
-   コンポーネントを失敗させます。  
  
 このオプションは、 **[エントリが一致しない行の処理方法を指定する]** ボックスの一覧で **[一致なしの出力に行をリダイレクトする]** を選択した場合には使用できません。 この一覧は、 **[参照変換エディター]** ダイアログ ボックスの **[全般]** ページにあります。  
  
 **関連項目:** [データのエラー処理](../../../integration-services/data-flow/error-handling-in-data.md)  
  
 **切り捨て**  
 データの切り捨てが発生したときの動作を指定します。  
  
-   エラーを無視します。  
  
-   行をリダイレクトします。  
  
-   コンポーネントを失敗させます。  
  
 **Description**  
 操作の説明を表示します。  
  
 **[選択したセルに設定する値]**  
 エラーまたは切り捨てが発生したときのすべての選択済みセルの動作を指定します。  
  
-   エラーを無視します。  
  
-   行をリダイレクトします。  
  
-   コンポーネントを失敗させます。  
  
 **[適用]**  
 選択したセルにエラー処理オプションを適用します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  

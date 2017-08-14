---
title: "[用語抽出変換エディター]\\ ([詳細] タブ) |Microsoft ドキュメント"
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
- sql13.dts.designer.termextraction.advanced.f1
helpviewer_keywords:
- Term Extraction Transformation Editor
ms.assetid: 87118281-6e3c-499e-bac4-fa4c24bb12c6
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 605085b59357a98011c801f8aa4675e89c3cd8a9
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="term-extraction-transformation-editor-advanced-tab"></a>[用語抽出変換エディター]\ ([詳細設定] タブ)
  **[用語抽出変換エディター]** ダイアログ ボックスの **[詳細設定]** タブを使用すると、頻度、長さ、語または句の抽出の有無など、抽出に関するプロパティを指定できます。  
  
 用語抽出変換の詳細については、「 [Term Extraction Transformation](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[名詞]**  
 変換によって個別の名詞のみを抽出するように指定します。  
  
 **[名詞句]**  
 変換によって個別の名詞句のみを抽出するように指定します。  
  
 **[名詞と名詞句]**  
 変換によって名詞と名詞句を両方とも抽出するように指定します。  
  
 **頻度**  
 スコアが用語の頻度であることを指定します。  
  
 **[TFIDF]**  
 スコアが用語の TFIDF 値であることを指定します。 TFIDF スコアは、Term Frequency と Inverse Document Frequency の積です。"用語 T の TFIDF = (T の頻度) * log( (入力の行数) / (T を含む行数) )" として定義されます。  
  
 **[頻度のしきい値]**  
 語または句を抽出する前の語または句の出現回数を指定します。 既定値は 2 です。  
  
 **[用語の最大長]**  
 句の最大長を語数で指定します。 このオプションは、名詞句のみに影響を与えます。 既定値は 12 です。  
  
 **[用語抽出で大文字と小文字を区別する]**  
 抽出で大文字と小文字を区別するかどうかを指定します。 既定値は **False**です。  
  
 **[エラー出力の構成]**  
 [[エラー出力の構成]](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) ダイアログ ボックスは、エラーが発生した行に対するエラー処理を指定するために使用します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [用語抽出変換エディター & #40 です。用語抽出 タブ &#41;](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-term-extraction-tab.md)   
 [用語抽出変換エディターと &#40; です。「除外」 タブと &#41; です。](../../../integration-services/data-flow/transformations/term-extraction-transformation-editor-exclusion-tab.md)   
 [用語参照変換](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)  
  
  

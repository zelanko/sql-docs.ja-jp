---
title: "参照変換エディター (詳細 ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.lookuptransformation.advanced.f1
helpviewer_keywords:
- Lookup Transformation Editor
ms.assetid: f3395c65-0320-47f9-8d83-daaa082d8713
caps.latest.revision: 42
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 13b342d7db5106451f7355c7dd1672181443f18d
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="lookup-transformation-editor-advanced-page"></a>[参照変換エディター] ([詳細設定] ページ)
  **[参照変換エディター]** ダイアログ ボックスの **[詳細設定]** ページを使用して、部分キャッシュを構成し、参照変換用 SQL ステートメントを変更します。  
  
 参照変換の詳細については、「 [Lookup Transformation](../../../integration-services/data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[キャッシュ サイズ (32 ビット)]**  
 32 ビット コンピューター用のキャッシュ サイズを MB 単位で調整します。 既定値は 5 MB です。  
  
 **[キャッシュ サイズ (64 ビット)]**  
 64 ビット コンピューター用のキャッシュ サイズを MB 単位で調整します。 既定値は 5 MB です。  
  
 **[エントリが一致しない行のキャッシュを有効にする]**  
 一致するエントリが参照データセットにない行をキャッシュします。  
  
 **[キャッシュからの割り当て]**  
 一致するエントリが参照データセットにない行に対して割り当てるキャッシュの割合を指定します。  
  
 **[SQL ステートメントを変更する]**  
 参照データセットを生成するために使用される SQL ステートメントを変更します。  
  
> [!NOTE]  
>  このページで指定するオプションの SQL ステートメントは、 **[参照変換エディター]** の **[接続]**ページで指定したテーブル名を上書きおよび置換します。 詳細については、「 [[参照変換エディター] &#40;[接続] ページ&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)」を参照してください。  
  
 **[パラメーターの設定]**  
 **[クエリ パラメーターの設定]** ダイアログ ボックスを使用して、入力列をパラメーターにマップします。  
  
## <a name="external-resources"></a>外部リソース  
 blogs.msdn.com のブログ「 [キャッシュ モードの参照](http://go.microsoft.com/fwlink/?LinkId=219518) 」  
  
## <a name="see-also"></a>参照  
 [[参照変換エディター] &#40;[全般] ページ&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-general-page.md)   
 [[参照変換エディター] &#40;[接続] ページ&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-connection-page.md)   
 [参照変換エディター」 (&) &#40; です。「列」 ページと &#41; です。](../../../integration-services/data-flow/transformations/lookup-transformation-editor-columns-page.md)   
 [[参照変換エディター] &#40;[エラー出力] ページ&#41;](../../../integration-services/data-flow/transformations/lookup-transformation-editor-error-output-page.md)   
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [あいまい参照変換](../../../integration-services/data-flow/transformations/fuzzy-lookup-transformation.md)  
  
  

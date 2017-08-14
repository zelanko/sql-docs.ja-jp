---
title: "[用語参照変換エディター]\\ ([用語参照] タブ) |Microsoft ドキュメント"
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
- sql13.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
caps.latest.revision: 26
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 79e7f405e9418b47985efd7bcc8bb13b14f20ec6
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>[用語参照変換エディター]\ ([用語参照] タブ)
  **[用語参照変換エディター]** ダイアログ ボックスの **[用語参照]** タブを使用すると、入力列を参照テーブルの参照列にマップし、各出力列の別名を提供できます。  
  
 用語参照変換の詳細については、「 [Term Lookup Transformation](../../../integration-services/data-flow/transformations/term-lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **使用できる入力列**  
 チェック ボックスを使用して、出力にそのまま渡す入力列を選択します。 **[使用できる参照列]** の一覧に入力列をドラッグして、入力列を参照テーブル内の参照列にマップします。 入力列と参照列は、DT_NTEXT または DT_WSTR のサポートされるデータ型が同じである必要があります。 マッピングする行を選択して右クリックし、 [[リレーションシップの作成]](../../../integration-services/data-flow/transformations/create-relationships.md) ダイアログ ボックスでマッピングを編集します。  
  
 **使用できる参照列**  
 参照テーブル内の使用できる列を表示します。 一致させる用語の一覧を含む列を選択します。  
  
 **パススルー列**  
 使用できる入力列の一覧から選択します。 選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。  
  
 **出力列の別名**  
 各出力列の別名を入力します。 既定では列の名前が使用されますが、一意なわかりやすい名前を自由に付けることができます。  
  
 **エラー出力を構成します。**  
 [[エラー出力の構成]](http://msdn.microsoft.com/library/5f8da390-fab5-44f8-b268-d8fa313ce4b9) ダイアログ ボックスは、エラーが発生した行に対するエラー処理オプションを指定するために使用します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [用語参照変換エディター &#40;参照テーブル タブ&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-reference-table-tab.md)   
 [用語参照変換エディター &#40;詳細設定タブ&#41;](../../../integration-services/data-flow/transformations/term-lookup-transformation-editor-advanced-tab.md)   
 [用語抽出変換](../../../integration-services/data-flow/transformations/term-extraction-transformation.md)  
  
  

---
title: '[用語参照変換エディター] ([用語参照] タブ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.termlookup.termlookup.f1
helpviewer_keywords:
- Term Lookup Transformation Editor
ms.assetid: 245d3466-d51f-4073-978a-694a8d9dfaec
author: janinezhang
ms.author: janinez
ms.openlocfilehash: d67c8c02e79583b5c8f4295abc4d71c2b05dae8b
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/17/2020
ms.locfileid: "84962075"
---
# <a name="term-lookup-transformation-editor-term-lookup-tab"></a>[用語参照変換エディター] ([用語参照] タブ)
  **[用語参照変換エディター]** ダイアログ ボックスの **[用語参照]** タブを使用すると、入力列を参照テーブルの参照列にマップし、各出力列の別名を提供できます。  
  
 用語参照変換の詳細については、「 [Term Lookup Transformation](data-flow/transformations/lookup-transformation.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[使用できる入力列]**  
 チェック ボックスを使用して、出力にそのまま渡す入力列を選択します。 **[使用できる参照列]** の一覧に入力列をドラッグして、入力列を参照テーブル内の参照列にマップします。 入力列と参照列は、DT_NTEXT または DT_WSTR のサポートされるデータ型が同じである必要があります。 マッピングする行を選択して右クリックし、 [[リレーションシップの作成]](data-flow/transformations/create-relationships.md) ダイアログ ボックスでマッピングを編集します。  
  
 **[使用できる参照列]**  
 参照テーブル内の使用できる列を表示します。 一致させる用語の一覧を含む列を選択します。  
  
 **[パススルー列]**  
 使用できる入力列の一覧から選択します。 選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。  
  
 **[出力列の別名]**  
 各出力列の別名を入力します。 既定では列の名前が使用されますが、一意なわかりやすい名前を自由に付けることができます。  
  
 **[エラー出力の構成]**  
 [[エラー出力の構成]](../../2014/integration-services/configure-error-output.md) ダイアログ ボックスは、エラーが発生した行に対するエラー処理オプションを指定するために使用します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[用語参照変換エディター] &#40;[参照テーブル] タブ&#41;](../../2014/integration-services/term-lookup-transformation-editor-reference-table-tab.md)   
 [[用語参照変換エディター] &#40;[詳細設定] タブ&#41;](../../2014/integration-services/term-lookup-transformation-editor-advanced-tab.md)   
 [用語抽出変換](data-flow/transformations/term-extraction-transformation.md)  
  
  

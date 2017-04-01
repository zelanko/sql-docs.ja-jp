---
title: "データ変換変換エディター | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontransformation.f1"
helpviewer_keywords: 
  - "データ変換変換エディター"
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# データ変換変換エディター
  **[データ変換変換エディター]** ダイアログ ボックスを使用すると、変換対象の列や列の変換先のデータ型を選択したり、変換属性を設定したりできます。  
  
> [!NOTE]  
>  データ変換の変換の出力列の **FastParse** プロパティは、**[データ変換変換エディター]** ではアクセスできませんが、**[詳細エディター]** を使用して設定できます。 このプロパティの詳細については、「[変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)」の「データ変換の変換」を参照してください。  
  
 データ変換の変換の詳細については、「[データ変換の変換](../../../integration-services/data-flow/transformations/data-conversion-transformation.md)」を参照してください。  
  
## オプション  
 **使用できる入力列**  
 変換対象の列のチェック ボックスを使用して選択します。 選択した列が入力列として下のテーブルに追加されます。  
  
 **入力列**  
 使用できる入力列の一覧から変換対象の列を選択します。 上記のチェック ボックスに、選択内容が反映されます。  
  
 **[出力の別名]**  
 それぞれの新しい列の別名を入力します。 既定では、入力列の名前の後に " **のコピー** " が追加された別名になりますが、固有のわかりやすい名前を選択することもできます。  
  
 **データ型**  
 一覧から利用可能なデータ型を選択します。 詳細については、「 [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md)」を参照してください。  
  
 **長さ**  
 文字列データの列の長さを設定します。  
  
 **有効桁数**  
 数値データの有効桁数を設定します。  
  
 **Scale**  
 数値データの小数点以下桁数を設定します。  
  
 **コード ページ**  
 DT_STR 型の列に適したコード ページを選択します。  
  
 **[エラー出力の構成]**  
 [[エラー出力の構成]](../Topic/Configure%20Error%20Output.md) ダイアログ ボックスを使用して、エラーの処理方法を指定します。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)   
 [データ変換の変換を使用してデータを別のデータ型に変換する](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
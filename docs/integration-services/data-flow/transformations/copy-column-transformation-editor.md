---
title: "列コピー変換エディター | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.copymaptransformation.f1"
helpviewer_keywords: 
  - "列コピー変換エディター"
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
caps.latest.revision: 26
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 26
---
# 列コピー変換エディター
  **[列コピー変換エディター]** ダイアログ ボックスを使用すると、コピーする列を選択して、新しい出力列に名前を割り当てることができます。  
  
 列コピー変換の詳細については、「[列コピー変換](../../../integration-services/data-flow/transformations/copy-column-transformation.md)」をご覧ください。  
  
> [!NOTE]  
>  すべての変換元データを変換先へ単にコピーする場合、列コピー変換を使用する必要がないことがあります。 データ変換が不要な場合、状況によっては変換元を変換先に直接接続できます。 このような場合は、SQL Server インポートおよびエクスポート ウィザードを使用してパッケージを作成することをお勧めします。 パッケージでは、必要に応じて、後から機能強化や再構成が可能です。 詳細については、「 [SQL Server Import and Export Wizard](../Topic/SQL%20Server%20Import%20and%20Export%20Wizard.md)」を参照してください。  
  
## オプション  
 **使用できる入力列**  
 チェック ボックスを使用して、コピーする列を選択します。 選択した列が入力列として下のテーブルに追加されます。  
  
 **入力列**  
 使用できる入力列の一覧からコピーする列を選択します。 選択内容が **[使用できる入力列]** テーブルのチェック ボックスに反映されます。  
  
 **[出力の別名]**  
 新しい出力列の別名をそれぞれ入力します。 既定では、入力列の名前の後に「**のコピー**」と付きます。一意のわかりやすい名前を付けることもできます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  
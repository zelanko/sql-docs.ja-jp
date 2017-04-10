---
title: "行数変換 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.rowcounttrans.f1"
helpviewer_keywords: 
  - "変数の更新"
  - "行数変換"
  - "行の数"
  - "変数 [Integration Services], 更新"
  - "カウント、行"
ms.assetid: b68293b9-a68c-40be-9d81-77342da1be29
caps.latest.revision: 43
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 43
---
# 行数変換
  行数変換は、行がデータ フローを通過するときに行をカウントし、最終的な行数を変数に格納します。  
  
 [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] パッケージで行数を使用して、スクリプト、式、およびプロパティ式で使用される変数を更新できます  (たとえば、行数を格納する変数を使用して、電子メールのメッセージ テキストを更新して行数を含めることができます)。行数変換で使用する変数は、既存の変数で、行数変換を使用するデータ フローが属するデータ フロー タスクの範囲に含まれている必要があります。  
  
 変換では、最後の行が変換を完了した後にのみ行数の値が変数に格納されます。 そのため、変数の値は、行数変換を含むデータ フローで更新された値を使用できるタイミングでは更新されません。 更新された変数は、別のデータ フローで使用できます。  
  
 この変換は 1 つの入力と 1 つの出力をとります。 エラー出力はサポートされていません。  
  
## 行数変換の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../../../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 **[詳細エディター]** ダイアログ ボックスには、プログラムによって設定できるプロパティが反映されます。 **[詳細エディター]** ダイアログ ボックスまたはプログラムで設定できるプロパティの詳細については、次のトピックのいずれかを参照してください。  
  
-   [共通プロパティ](../Topic/Common%20Properties.md)  
  
-   [変換のカスタム プロパティ](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
## 関連タスク  
 このコンポーネントのプロパティの設定方法の詳細については、「[データ フロー コンポーネントのプロパティを設定する](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md)」を参照してください。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; の変数](../../../integration-services/integration-services-ssis-variables.md)   
 [データ フロー](../../../integration-services/data-flow/data-flow.md)   
 [Integration Services の変換](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
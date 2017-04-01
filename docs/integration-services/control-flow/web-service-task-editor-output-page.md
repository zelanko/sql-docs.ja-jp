---
title: "[Web サービス タスク エディター] ([出力] ページ) | Microsoft Docs"
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
  - "sql13.dts.designer.webservicestask.output.f1"
helpviewer_keywords: 
  - "Web サービス タスク エディター"
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 27
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 27
---
# [Web サービス タスク エディター] ([出力] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[出力]** ページを使用すると、Web メソッドから返された結果を格納する場所を指定できます。  
  
 このタスクの詳細については、「[Web サービス タスク](../../integration-services/control-flow/web-service-task.md)」を参照してください。  
  
## 静的オプション  
 **[OutputType]**  
 結果を格納するときに使用するストレージ型を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|結果をファイルに格納します。 この値を選択すると、動的オプションの **[ファイル]** が表示されます。|  
|**変数**|結果を変数に格納します。 この値を選択すると、動的オプションの **[変数]** が表示されます。|  
  
## [OutputType] の動的オプション  
  
### [OutputType] = [ファイル接続]  
 **ファイル**  
 一覧でファイル接続マネージャーを選択するか、**[\<新しい接続>]** をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### [OutputType] = [変数]  
 **変数**  
 変数を一覧から選択するか、**[\<新しい変数>]** をクリックして新しい変数を作成します。  
  
 **関連項目:** [Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](../Topic/Add%20Variable.md)  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Web サービス タスク エディター ([全般] ページ)](../Topic/Web%20Service%20Task%20Editor%20\(General%20Page\).md)   
 [[Web サービス タスク エディター] ([入力] ページ)](../Topic/Web%20Service%20Task%20Editor%20\(Input%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)  
  
  
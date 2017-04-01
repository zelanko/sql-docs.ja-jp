---
title: "[Analysis Services DDL 実行タスク エディター] ([DDL] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/04/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.asexecuteddltask.ddl.f1"
helpviewer_keywords: 
  - "Analysis Services DDL 実行タスク エディター"
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 30
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 30
---
# [Analysis Services DDL 実行タスク エディター] ([DDL] ページ)
  **[Analysis Services DDL 実行タスク エディター]** ダイアログ ボックスの **[DDL]** ページを使用すると、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データベースへの接続を指定でき、データ定義言語 (DDL) ステートメントのソースについての情報を表示できます。  
  
 このタスクの詳細については、「[Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md)」(Analysis Services DDL 実行タスク) を参照してください。  
  
## 静的オプション  
 **接続**  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 接続マネージャーを一覧で選択するか、**[\<新しい接続>]** をクリックして **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](../Topic/Add%20Analysis%20Services%20Connection%20Manager%20Dialog%20Box%20UI%20Reference.md)、[Analysis Services 接続マネージャー](../../integration-services/connection-manager/analysis-services-connection-manager.md)  
  
 **[SourceType]**  
 DDL ステートメントのソースの種類を指定します。 このプロパティには、次の表に示すオプションがあります。  
  
|値|Description|  
|-----------|-----------------|  
|**[直接入力]**|**[SourceDirect]** テキスト ボックスに格納される DDL ステートメントへのソースを設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
|**[ファイル接続]**|DDL ステートメントを含むファイルへのソースを設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
|**変数**|ソースを変数に設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
  
## 動的オプション  
  
### [SourceType] = [直接入力]  
 **ソース**  
 DDL ステートメントを入力するか、参照ボタン (**[...]**) をクリックしてから **[DDL ステートメント]** ダイアログ ボックスでステートメントを入力します。  
  
### [SourceType] = [ファイル接続]  
 **ソース**  
 一覧でファイル接続を選択するか、**[\<新しい接続>]** をクリックし、**[ファイル接続マネージャー エディター]** ダイアログ ボックスを使用して新しい接続を作成します。  
  
 **関連項目:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)  
  
### [SourceType] = [変数]  
 **ソース**  
 一覧で変数を選択するか、**[\<新しい変数...>]** をクリックし、**[変数の追加]** ダイアログ ボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services DDL 実行タスク エディター ([全般] ページ)](../Topic/Analysis%20Services%20Execute%20DDL%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [制御フロー](../../integration-services/control-flow/control-flow.md)   
 [Analysis Services スクリプト言語 (XMLA 用 ASSL)](../../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [XML for Analysis &#40;XMLA&#41 リファレンス](../../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
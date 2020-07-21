---
title: Analysis Services DDL 実行タスクエディター ([DDL] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 923a5d549cff00af096b905ac6dc06f20e132a80
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439519"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>[Analysis Services DDL 実行タスク エディター] ([DDL] ページ)
  **[Analysis Services DDL 実行タスク エディター]** ダイアログ ボックスの **[DDL]** ページを使用すると、 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースへの接続を指定でき、データ定義言語 (DDL) ステートメントのソースについての情報を表示できます。  
  
 このタスクの詳細については、「 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md)」(Analysis Services DDL 実行タスク) を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **接続**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接続マネージャーを一覧から選択するか、[ \<**New connection...**> **Analysis Services 接続マネージャーの追加**] ダイアログボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)、 [Analysis Services 接続マネージャー](connection-manager/analysis-services-connection-manager.md)  
  
 **SourceType**  
 DDL ステートメントのソースの種類を指定します。 このプロパティには、次の表に示すオプションがあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|**直接入力**|**[SourceDirect]** テキスト ボックスに格納される DDL ステートメントへのソースを設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
|**ファイル接続**|DDL ステートメントを含むファイルへのソースを設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
|**Variable**|ソースを変数に設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
  
## <a name="dynamic-options"></a>動的オプション  
  
### <a name="sourcetype--direct-input"></a>[SourceType] = [直接入力]  
 **ソース**  
 Ddl ステートメントを入力するか、参照ボタン ([...] **)** をクリックして、[ **ddl ステートメント**] ダイアログボックスにステートメントを入力します。  
  
### <a name="sourcetype--file-connection"></a>[SourceType] = [ファイル接続]  
 **ソース**  
 ファイル接続を一覧から選択するか、[ \<**New connection...**> **ファイル接続マネージャー** ] ダイアログボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [[ファイル接続マネージャー エディター]](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>[SourceType] = [変数]  
 **ソース**  
 変数を一覧から選択するか、[ \<**New variable...**> **変数の追加**] ダイアログボックスを使用して新しい変数を作成します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services DDL 実行タスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [制御フロー](control-flow/control-flow.md)   
 [Analysis Services スクリプト言語 &#40;ASSL&#41; リファレンス](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla)   
 [XML for Analysis (XML for Analysis) リファレンス](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)  
  
  

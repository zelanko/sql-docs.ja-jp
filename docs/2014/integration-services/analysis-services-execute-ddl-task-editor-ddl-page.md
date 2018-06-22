---
title: Analysis Services DDL 実行タスク エディター (DDL ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.asexecuteddltask.ddl.f1
helpviewer_keywords:
- Analysis Services Execute DDL Task Editor
ms.assetid: f21bf8d0-ec5f-4c18-9de0-8875addb927b
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9499537bdb59778ab4dc5d511c16e3fb4cb9be08
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36083697"
---
# <a name="analysis-services-execute-ddl-task-editor-ddl-page"></a>[Analysis Services DDL 実行タスク エディター] ([DDL] ページ)
  **[Analysis Services DDL 実行タスク エディター]** ダイアログ ボックスの **[DDL]** ページを使用すると、[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] データベースへの接続を指定でき、データ定義言語 (DDL) ステートメントのソースについての情報を表示できます。  
  
 このタスクの詳細については、「 [Analysis Services Execute DDL Task](control-flow/analysis-services-execute-ddl-task.md)」(Analysis Services DDL 実行タスク) を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **Connection**  
 [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] プロジェクトまたは [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 接続マネージャーを一覧で選択するか、\<**[新しい接続...]**> をクリックして **[Analysis Services 接続マネージャーの追加]** ダイアログ ボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [[Analysis Services 接続マネージャーの追加] ダイアログ ボックスの UI リファレンス](connection-manager/add-analysis-services-connection-manager-dialog-box-ui-reference.md)、[Analysis Services 接続マネージャー](connection-manager/analysis-services-connection-manager.md)  
  
 **[SourceType]**  
 DDL ステートメントのソースの種類を指定します。 このプロパティには、次の表に示すオプションがあります。  
  
|値|説明|  
|-----------|-----------------|  
|**[直接入力]**|**[SourceDirect]** テキスト ボックスに格納される DDL ステートメントへのソースを設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
|**[ファイル接続]**|DDL ステートメントを含むファイルへのソースを設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
|**変数**|ソースを変数に設定します。 この値を選択すると、次に示す動的オプションが表示されます。|  
  
## <a name="dynamic-options"></a>動的オプション  
  
### <a name="sourcetype--direct-input"></a>[SourceType] = [直接入力]  
 **Source**  
 DDL ステートメントを入力するか、参照ボタン ( **[...]** ) をクリックしてから **[DDL ステートメント]** ダイアログ ボックスでステートメントを入力します。  
  
### <a name="sourcetype--file-connection"></a>[SourceType] = [ファイル接続]  
 **Source**  
 一覧でファイル接続を選択するか、\<**[新しい接続...]**> をクリックし、**[ファイル接続マネージャー]** ダイアログ ボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [[ファイル接続マネージャー エディター]](connection-manager/file-connection-manager.md)  
  
### <a name="sourcetype--variable"></a>[SourceType] = [変数]  
 **Source**  
 一覧で変数を選択するか、\<**[新しい変数...]**> をクリックし、**[変数の追加]** ダイアログ ボックスを使用して新しい接続を作成します。  
  
 **関連トピック:** [Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Analysis Services DDL 実行タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [制御フロー](control-flow/control-flow.md)   
 [Analysis Services スクリプト言語&#40;ASSL&#41;参照](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md)   
 [XML for Analysis &#40;XMLA&#41;参照](../analysis-services/xmla/xml-for-analysis-xmla-reference.md)  
  
  
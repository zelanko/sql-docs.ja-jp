---
title: "Web サービス タスク エディター (出力 ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 27
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: f4bd03a4844548b7dfbc976224c09c47f0ab2a4f
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="web-service-task-editor-output-page"></a>[Web サービス タスク エディター] ([出力] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[出力]** ページを使用すると、Web メソッドから返された結果を格納する場所を指定できます。  
  
 このタスクの詳細については、「 [Web サービス タスク](../../integration-services/control-flow/web-service-task.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **[OutputType]**  
 結果を格納するときに使用するストレージ型を選択します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[ファイル接続]**|結果をファイルに格納します。 この値を選択すると、動的オプションの **[ファイル]**が表示されます。|  
|**変数**|結果を変数に格納します。 この値を選択すると、動的オプションの **[変数]**が表示されます。|  
  
## <a name="outputtype-dynamic-options"></a>[OutputType] の動的オプション  
  
### <a name="outputtype--file-connection"></a>[OutputType] = [ファイル接続]  
 **ファイル**  
 一覧で、ファイル接続マネージャーを選択するかクリックして\<**新しい接続をしています.**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](../../integration-services/connection-manager/file-connection-manager.md)、[ファイル接続マネージャー エディター](../../integration-services/connection-manager/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>[OutputType] = [変数]  
 **変数**  
 一覧に変数を選択するか、をクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連項目:** [Integration Services (SSIS) の変数](../../integration-services/integration-services-ssis-variables.md)、[変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Web サービス タスク エディター & #40 です。[全般] ページ &#41;](../../integration-services/control-flow/web-service-task-editor-general-page.md)   
 [Web サービス タスク エディターと &#40; 入力ページと &#41;](../../integration-services/control-flow/web-service-task-editor-input-page.md)   
 [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
  

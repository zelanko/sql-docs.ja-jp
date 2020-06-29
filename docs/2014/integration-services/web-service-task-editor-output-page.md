---
title: '[Web サービスタスクエディター] ([出力] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
author: chugugrace
ms.author: chugu
ms.openlocfilehash: c6d753b7ef37d515140a3fc32137dd4680fa3079
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85439819"
---
# <a name="web-service-task-editor-output-page"></a>[Web サービス タスク エディター] ([出力] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[出力]** ページを使用すると、Web メソッドから返された結果を格納する場所を指定できます。  
  
 このタスクの詳細については、「 [Web Service Task](control-flow/web-service-task.md)」(Web サービス タスク) を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **OutputType**  
 結果を格納するときに使用するストレージ型を選択します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**ファイル接続**|結果をファイルに格納します。 この値を選択すると、動的オプションの **[ファイル]** が表示されます。|  
|**Variable**|結果を変数に格納します。 この値を選択すると、動的オプションの **[変数]** が表示されます。|  
  
## <a name="outputtype-dynamic-options"></a>[OutputType] の動的オプション  
  
### <a name="outputtype--file-connection"></a>[OutputType] = [ファイル接続]  
 **[最近使ったファイル]**  
 ファイル接続マネージャーを一覧から選択するか、をクリックして \<**New Connection...**> 新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、 [ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>[OutputType] = [変数]  
 **Variable**  
 変数を一覧から選択するか、をクリックして \<**New Variable...**> 新しい変数を作成します。  
  
 **関連トピック:**[SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)[変数の追加](../../2014/integration-services/add-variable.md)    
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Web サービスタスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [[Web サービスタスクエディター] &#40;入力ページ&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  

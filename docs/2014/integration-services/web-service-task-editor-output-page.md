---
title: Web サービス タスク エディター ([出力] ページ) |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.webservicestask.output.f1
helpviewer_keywords:
- Web Service Task Editor
ms.assetid: 73c83969-7b0e-479d-a436-0a46b2068d01
caps.latest.revision: 26
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 00d7676916ac06cb82f384202cd2c6f024ffdb65
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/02/2018
ms.locfileid: "37281548"
---
# <a name="web-service-task-editor-output-page"></a>[Web サービス タスク エディター] ([出力] ページ)
  **[Web サービス タスク エディター]** ダイアログ ボックスの **[出力]** ページを使用すると、Web メソッドから返された結果を格納する場所を指定できます。  
  
 このタスクの詳細については、「 [Web サービス タスク](control-flow/web-service-task.md)」を参照してください。  
  
## <a name="static-options"></a>静的オプション  
 **[OutputType]**  
 結果を格納するときに使用するストレージ型を選択します。 このプロパティのオプションを次の表に示します。  
  
|ReplTest1|説明|  
|-----------|-----------------|  
|**[ファイル接続]**|結果をファイルに格納します。 この値を選択すると、動的オプションの **[ファイル]** が表示されます。|  
|**変数**|結果を変数に格納します。 この値を選択すると、動的オプションの **[変数]** が表示されます。|  
  
## <a name="outputtype-dynamic-options"></a>[OutputType] の動的オプション  
  
### <a name="outputtype--file-connection"></a>[OutputType] = [ファイル接続]  
 **[最近使ったファイル]**  
 ファイル接続マネージャーを一覧から選択するか、[\<**新しい接続…**>] をクリックして新しい接続マネージャーを作成します。  
  
 **関連トピック:** [ファイル接続マネージャー](connection-manager/file-connection-manager.md)、 [ファイル接続マネージャー エディター](../../2014/integration-services/file-connection-manager-editor.md)  
  
### <a name="outputtype--variable"></a>[OutputType] = [変数]  
 **変数**  
 一覧で変数を選択するか、[\<**新しい変数…**>] をクリックして新しい変数を作成します。  
  
 **関連項目:** [Integration Services (SSIS) の変数](integration-services-ssis-variables.md)、[変数の追加](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Web サービス タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [Web サービス タスク エディター &#40;[入力] ページ&#41;](../../2014/integration-services/web-service-task-editor-input-page.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  

---
title: '[エラーメッセージ転送タスクエディター] ([メッセージ] ページ)Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7b551d60d36948cb4c950dfcd9a17e2c16229420
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85420699"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>[エラー メッセージ転送タスク エディター] ([メッセージ] ページ)
  **[エラー メッセージ転送タスク エディター]** ダイアログ ボックスの **[メッセージ]** ページを使用すると、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスからインスタンスへ、 [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー定義エラー メッセージをコピーする際のプロパティを指定できます。 このタスクの詳細については、「 [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[Sourceconnection]**  
 SMO 接続マネージャーを一覧から選択するか、をクリックし **\<New connection...>** て、移行元サーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、をクリックし **\<New connection...>** て、移行先サーバーへの新しい接続を作成します。  
  
 **[IfObjectExists]**  
 転送先サーバーに同じ名前のエラー メッセージが既に存在していた場合に、既存のユーザー定義エラー メッセージを上書きするか、既存のメッセージをスキップするか、タスクを失敗させるかを選択します。  
  
 **[TransferAllErrorMessages]**  
 転送元サーバーから転送先サーバーにすべてのユーザー定義メッセージをコピーするか、指定したユーザー定義メッセージだけをコピーするかを選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|[値]|説明|  
|-----------|-----------------|  
|**True**|すべてのユーザー定義メッセージをコピーします。|  
|**False**|指定されたユーザー定義メッセージのみをコピーします。|  
  
 **[ErrorMessagesList]**  
 **[...]** ボタンをクリックして、コピーするエラー メッセージを選択します。  
  
> [!NOTE]  
>  コピーするエラー メッセージを選択する前に **[SourceConnection]** を指定する必要があります。  
  
 **[ErrorMessageLanguagesList]**  
 **[...]** ボタンをクリックして、転送先サーバーにコピーするユーザー定義エラー メッセージの言語を選択します。 us_english (コード ページ 1033) バージョンのメッセージが、他言語バージョンのメッセージを転送先サーバーに転送する前に、そのサーバーに既に存在している必要があります。  
  
> [!NOTE]  
>  コピーするエラー メッセージを選択する前に **[SourceConnection]** を指定する必要があります。  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [[エラーメッセージ転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)   
 [[エラーメッセージ転送タスクエディター] &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)  
  
  

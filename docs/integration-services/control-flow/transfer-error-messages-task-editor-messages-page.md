---
title: "エラー メッセージ転送タスク エディター (メッセージ ページ) |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 22
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 8051e89dc6c319d13f51d086d702145548ea7e48
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="transfer-error-messages-task-editor-messages-page"></a>[エラー メッセージ転送タスク エディター] ([メッセージ] ページ)
  **[エラー メッセージ転送タスク エディター]** ダイアログ ボックスの **[メッセージ]** ページを使用すると、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] のインスタンスからインスタンスへ、[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ユーザー定義エラー メッセージをコピーする際のプロパティを指定できます。 このタスクの詳細については、「 [Transfer Error Messages Task](../../integration-services/control-flow/transfer-error-messages-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **SourceConnection**  
 一覧で、SMO 接続マネージャーを選択するかクリックして**\<新しい接続 >**移行元サーバーに新しい接続を作成します。  
  
 **DestinationConnection**  
 一覧で、SMO 接続マネージャーを選択するかクリックして**\<新しい接続 >**移行先サーバーに新しい接続を作成します。  
  
 **[IfObjectExists]**  
 転送先サーバーに同じ名前のエラー メッセージが既に存在していた場合に、既存のユーザー定義エラー メッセージを上書きするか、既存のメッセージをスキップするか、タスクを失敗させるかを選択します。  
  
 **[TransferAllErrorMessages]**  
 転送元サーバーから転送先サーバーにすべてのユーザー定義メッセージをコピーするか、指定したユーザー定義メッセージだけをコピーするかを選択します。  
  
 このプロパティには、次の表に示すオプションがあります。  
  
|値|Description|  
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
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](../../integration-services/control-flow/integration-services-tasks.md)   
 [エラー メッセージ タスク エディター &#40; を転送します。[全般] ページ &#41;](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)   
 [エラー メッセージ タスク エディター &#40; を転送します。[全般] ページ &#41;](../../integration-services/control-flow/transfer-error-messages-task-editor-general-page.md)   
 [SMO 接続マネージャー](../../integration-services/connection-manager/smo-connection-manager.md)  
  
  

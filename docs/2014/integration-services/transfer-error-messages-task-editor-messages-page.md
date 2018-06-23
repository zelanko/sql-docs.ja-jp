---
title: エラー メッセージ転送タスク エディター (メッセージ ページ) |Microsoft ドキュメント
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.transfererrormessagestask.errormessages.F1
helpviewer_keywords:
- Transfer Error Messages Task Editor
ms.assetid: cb2226a0-3037-4fdf-966f-81eabc0da9cf
caps.latest.revision: 20
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 833f092574c85ab83f6a384b77e7f8c99c91b2c3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36084129"
---
# <a name="transfer-error-messages-task-editor-messages-page"></a>[エラー メッセージ転送タスク エディター] ([メッセージ] ページ)
  **[エラー メッセージ転送タスク エディター]** ダイアログ ボックスの **[メッセージ]** ページを使用すると、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] のインスタンスからインスタンスへ、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] ユーザー定義エラー メッセージをコピーする際のプロパティを指定できます。 このタスクの詳細については、「 [Transfer Error Messages Task](control-flow/transfer-error-messages-task.md)」を参照してください。  
  
## <a name="options"></a>および  
 **SourceConnection**  
 SMO 接続マネージャーを一覧から選択するか、**\<[新しい接続...]>** をクリックしてコピー元のサーバーへの新しい接続を作成します。  
  
 **DestinationConnection**  
 SMO 接続マネージャーを一覧から選択するか、**\<[新しい接続...]>** をクリックしてコピー先のサーバーへの新しい接続を作成します。  
  
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
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Integration Services タスク](control-flow/integration-services-tasks.md)   
 [エラー メッセージ転送タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)   
 [エラー メッセージ転送タスク エディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [SMO 接続マネージャー](connection-manager/smo-connection-manager.md)  
  
  
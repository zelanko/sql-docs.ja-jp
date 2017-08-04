---
title: "メッセージ キュー タスク エディター (ページが表示される) |Microsoft ドキュメント"
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
- sql13.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
caps.latest.revision: 29
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1f51937fa402accf4e18fefdcec5763987241de4
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="message-queue-task-editor-receive-page"></a>[メッセージ キュー タスク エディター] ([受信] ページ)
  **[メッセージ キュー タスク エディター]** ダイアログ ボックスの **[受信]** ページを使用して、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] Message Queuing (MSMQ) メッセージを受信するためのメッセージ キュー タスクを構成します。  
  
 このタスクの詳細については、「 [Message Queue Task](../../integration-services/control-flow/message-queue-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[RemoveFromMessageQueue]**  
 メッセージが受信された後にキューからメッセージを削除するかどうかを示します。 既定では、この値は **False**に設定されます。  
  
 **[ErrorIfMessageTimeOut]**  
 メッセージがタイムアウトになったときに、エラー メッセージを表示してタスクを中止するかどうかを示します。 既定値は **False**です。  
  
 **[TimeoutAfter]**  
 タスクが失敗したときにエラー メッセージを表示するように指定した場合、タイムアウト メッセージが表示されるまでの待機時間を秒数で指定します。  
  
 **[MessageType]**  
 メッセージ型を指定します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[データ ファイル メッセージ]**|メッセージはファイルに格納されます。 この値を選択すると、動的オプションの **[DataFileMessage]**が表示されます。|  
|**[変数メッセージ]**|メッセージは変数に格納されます。 この値を選択すると、動的オプションの **[VariableMessage]**が表示されます。|  
|**[文字列メッセージ]**|メッセージはメッセージ キュー タスクに格納されます。 この値を選択すると、動的オプションの **[StringMessage]**が表示されます。|  
|**[文字列メッセージを変数に指定]**|メッセージです。<br /><br /> この値を選択すると、動的オプションの **[StringMessage]**が表示されます。|  
  
## <a name="messagetype-dynamic-options"></a>[MessageType] の動的オプション  
  
### <a name="messagetype--data-file-message"></a>[MessageType] = [データ ファイル メッセージ]  
 **[SaveFileAs]**  
 使用するファイルのパスを入力します。または、省略記号ボタン ( **[...]** ) をクリックし、ファイルを指定します。  
  
 **Overwrite**  
 データ ファイル メッセージの内容を保存するとき、既存のファイルのデータを上書きするかどうかを示します。 既定値は **False**です。  
  
 **[フィルター]**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[フィルターなし]**|メッセージにフィルターは適用されません。 この値を選択すると、動的オプションの **[IdentifierReadOnly]**が表示されます。|  
|**[パッケージから]**|指定したパッケージからのメッセージのみが受信されます。 この値を選択すると、動的オプションの **[Identifier]**が表示されます。|  
  
### <a name="filter-dynamic-options"></a>[Filter] の動的オプション  
  
#### <a name="filter--no-filter"></a>[Filter] = [フィルターなし]  
 **[IdentifierReadOnly]**  
 このオプションは読み取り専用です。 [Filter] プロパティが以前に設定された場合、パッケージの GUID が表示されます。それ以外の場合は空です。  
  
#### <a name="filter--from-package"></a>[Filter] = [パッケージから]  
 **[Identifier]**  
 フィルターの適用を選択した場合、メッセージの受信元のパッケージを表す固有の識別子を入力するか、省略記号ボタン ( **[...]** ) をクリックしてパッケージを指定します。  
  
 **関連項目:** [パッケージの選択](../../integration-services/control-flow/select-a-package.md)  
  
### <a name="messagetype--variable-message"></a>[MessageType] = [変数メッセージ]  
 **[フィルター]**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**[フィルターなし]**|メッセージにフィルターは適用されません。 この値を選択すると、動的オプションの **[IdentifierReadOnly]**が表示されます。|  
|**[パッケージから]**|指定したパッケージからのメッセージのみが受信されます。 この値を選択すると、動的オプションの **[Identifier]**が表示されます。|  
  
 **変数**  
 変数の名前を入力またはクリックして\<**新しい変数しています.**> し、新しい変数を構成します。  
  
 **関連項目:** [変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
### <a name="filter-dynamic-options"></a>[Filter] の動的オプション  
  
#### <a name="filter--no-filter"></a>[Filter] = [フィルターなし]  
 **[IdentifierReadOnly]**  
 このオプションは空白です。  
  
#### <a name="filter--from-package"></a>[Filter] = [パッケージから]  
 **[Identifier]**  
 フィルターの適用を選択した場合、メッセージの受信元のパッケージを表す固有の識別子を入力するか、省略記号ボタン ( **[...]** ) をクリックしてパッケージを指定します。  
  
 **関連項目:** [パッケージの選択](../../integration-services/control-flow/select-a-package.md)  
  
### <a name="messagetype--string-message"></a>[MessageType] = [文字列メッセージ]  
 **[Compare]**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**なし**|メッセージは比較されません。|  
|**完全一致**|メッセージは **[CompareString]** オプションで指定した文字列と完全に一致する必要があります。|  
|**大文字と小文字を区別しない**|メッセージは **[CompareString]** オプションで指定した文字列と一致する必要がありますが、大文字と小文字は区別されません。|  
|**[含まれる文字列]**|メッセージに **[CompareString]** オプションで指定した文字列が含まれている必要があります。|  
  
 **[CompareString]**  
 **[Compare]** オプションが **[なし]**に設定されていない場合、メッセージと比較する文字列を入力します。  
  
### <a name="messagetype--string-message-to-variable"></a>[MessageType] = [文字列メッセージを変数に指定]  
 **[Compare]**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|値|Description|  
|-----------|-----------------|  
|**なし**|メッセージは比較されません。|  
|**完全一致**|メッセージは **[CompareString]** オプションで指定した文字列と完全に一致する必要があります。|  
|**大文字と小文字を区別しない**|メッセージは **[CompareString]** オプションで指定した文字列と一致する必要がありますが、大文字と小文字は区別されません。|  
|**[含まれる文字列]**|メッセージに **[CompareString]** オプションで指定した文字列が含まれている必要があります。|  
  
 **[CompareString]**  
 **[Compare]** オプションが **[なし]**に設定されていない場合、メッセージと比較する文字列を入力します。  
  
 **変数**  
 受信したメッセージを保持する変数の名前を入力\<**新しい変数しています.**> し、新しい変数を構成します。  
  
 **関連項目:** [変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [メッセージ キュー タスク エディター & #40 です。[全般] ページ &#41;](../../integration-services/control-flow/message-queue-task-editor-general-page.md)   
 [メッセージ キュー タスク エディター & #40 です。送信する ページ &#41;](../../integration-services/control-flow/message-queue-task-editor-send-page.md)   
 [「 式」 ページ](../../integration-services/expressions/expressions-page.md)   
 [メッセージ キュー タスク](../../integration-services/control-flow/message-queue-task.md)  
  
  

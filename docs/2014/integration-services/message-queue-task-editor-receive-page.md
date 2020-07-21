---
title: '[メッセージキュータスクエディター] ([受信] ページ) |Microsoft Docs'
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.msgqueuetask.receive.f1
helpviewer_keywords:
- Message Queue Task Editor
ms.assetid: 7028756d-1dcc-480c-bbcd-e9654f0772a0
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 53a392a09e2120c08c43b1e373c942ff9c60e148
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85424589"
---
# <a name="message-queue-task-editor-receive-page"></a>[メッセージ キュー タスク エディター] ([受信] ページ)
  **[メッセージ キュー タスク エディター]** ダイアログ ボックスの **[受信]** ページを使用して、 [!INCLUDE[msCoName](../includes/msconame-md.md)] Message Queuing (MSMQ) メッセージを受信するためのメッセージ キュー タスクを構成します。  
  
 このタスクの詳細については、「 [Message Queue Task](control-flow/message-queue-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[RemoveFromMessageQueue]**  
 メッセージが受信された後にキューからメッセージを削除するかどうかを示します。 既定では、この値は `False` に設定されます。  
  
 **[ErrorIfMessageTimeOut]**  
 メッセージがタイムアウトになったときに、エラー メッセージを表示してタスクを中止するかどうかを示します。 既定値は、`False` です。  
  
 **[TimeoutAfter]**  
 タスクが失敗したときにエラー メッセージを表示するように指定した場合、タイムアウト メッセージが表示されるまでの待機時間を秒数で指定します。  
  
 **MessageType**  
 メッセージ型を指定します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**[データ ファイル メッセージ]**|メッセージはファイルに格納されます。 この値を選択すると、動的オプションの **[DataFileMessage]** が表示されます。|  
|**[変数メッセージ]**|メッセージは変数に格納されます。 この値を選択すると、動的オプションの **[VariableMessage]** が表示されます。|  
|**[文字列メッセージ]**|メッセージはメッセージ キュー タスクに格納されます。 この値を選択すると、動的オプションの **[StringMessage]** が表示されます。|  
|**[文字列メッセージを変数に指定]**|メッセージです。<br /><br /> この値を選択すると、動的オプションの **[StringMessage]** が表示されます。|  
  
## <a name="messagetype-dynamic-options"></a>[MessageType] の動的オプション  
  
### <a name="messagetype--data-file-message"></a>[MessageType] = [データ ファイル メッセージ]  
 **[SaveFileAs]**  
 使用するファイルのパスを入力します。または、省略記号ボタン ( **[...]** ) をクリックし、ファイルを指定します。  
  
 **Overwrite**  
 データ ファイル メッセージの内容を保存するとき、既存のファイルのデータを上書きするかどうかを示します。 既定値は、`False` です。  
  
 **Assert**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**フィルターなし**|メッセージにフィルターは適用されません。 この値を選択すると、動的オプションの **[IdentifierReadOnly]** が表示されます。|  
|**[パッケージから]**|指定したパッケージからのメッセージのみが受信されます。 この値を選択すると、動的オプションの **[Identifier]** が表示されます。|  
  
### <a name="filter-dynamic-options"></a>[Filter] の動的オプション  
  
#### <a name="filter--no-filter"></a>[Filter] = [フィルターなし]  
 **[IdentifierReadOnly]**  
 このオプションは読み取り専用です。 [Filter] プロパティが以前に設定された場合、パッケージの GUID が表示されます。それ以外の場合は空です。  
  
#### <a name="filter--from-package"></a>[Filter] = [パッケージから]  
 **識別子**  
 フィルターの適用を選択した場合、メッセージの受信元のパッケージを表す固有の識別子を入力するか、省略記号ボタン ( **[...]** ) をクリックしてパッケージを指定します。  
  
 **関連項目:** [パッケージの選択](control-flow/select-a-package.md)  
  
### <a name="messagetype--variable-message"></a>[MessageType] = [変数メッセージ]  
 **Assert**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**フィルターなし**|メッセージにフィルターは適用されません。 この値を選択すると、動的オプションの **[IdentifierReadOnly]** が表示されます。|  
|**[パッケージから]**|指定したパッケージからのメッセージのみが受信されます。 この値を選択すると、動的オプションの **[Identifier]** が表示されます。|  
  
 **Variable**  
 変数名を入力するか、[] をクリックし \<**New variable...**> て新しい変数を構成します。  
  
 **関連項目:** [変数の追加](../../2014/integration-services/add-variable.md)  
  
### <a name="filter-dynamic-options"></a>[Filter] の動的オプション  
  
#### <a name="filter--no-filter"></a>[Filter] = [フィルターなし]  
 **[IdentifierReadOnly]**  
 このオプションは空白です。  
  
#### <a name="filter--from-package"></a>[Filter] = [パッケージから]  
 **識別子**  
 フィルターの適用を選択した場合、メッセージの受信元のパッケージを表す固有の識別子を入力するか、省略記号ボタン ( **[...]** ) をクリックしてパッケージを指定します。  
  
 **関連項目:** [パッケージの選択](control-flow/select-a-package.md)  
  
### <a name="messagetype--string-message"></a>[MessageType] = [文字列メッセージ]  
 **比較**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**なし**|メッセージは比較されません。|  
|**完全一致**|メッセージは **[CompareString]** オプションで指定した文字列と完全に一致する必要があります。|  
|**大文字と小文字を区別しない**|メッセージは **[CompareString]** オプションで指定した文字列と一致する必要がありますが、大文字と小文字は区別されません。|  
|**[含まれる文字列]**|メッセージに **[CompareString]** オプションで指定した文字列が含まれている必要があります。|  
  
 **[CompareString]**  
 **[Compare]** オプションが **[なし]** に設定されていない場合、メッセージと比較する文字列を入力します。  
  
### <a name="messagetype--string-message-to-variable"></a>[MessageType] = [文字列メッセージを変数に指定]  
 **比較**  
 メッセージにフィルターを適用するかどうかを指定します。 このプロパティのオプションを次の表に示します。  
  
|[値]|説明|  
|-----------|-----------------|  
|**なし**|メッセージは比較されません。|  
|**完全一致**|メッセージは **[CompareString]** オプションで指定した文字列と完全に一致する必要があります。|  
|**大文字と小文字を区別しない**|メッセージは **[CompareString]** オプションで指定した文字列と一致する必要がありますが、大文字と小文字は区別されません。|  
|**[含まれる文字列]**|メッセージに **[CompareString]** オプションで指定した文字列が含まれている必要があります。|  
  
 **[CompareString]**  
 **[Compare]** オプションが **[なし]** に設定されていない場合、メッセージと比較する文字列を入力します。  
  
 **Variable**  
 受信したメッセージを保持する変数の名前を入力するか、[] をクリックし \<**New variable...**> て新しい変数を構成します。  
  
 **関連項目:** [変数の追加](../../2014/integration-services/add-variable.md)  
  
## <a name="see-also"></a>関連項目  
 [Integration Services のエラーとメッセージの参照](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [メッセージキュータスクエディター &#40;[全般] ページ&#41;](general-page-of-integration-services-designers-options.md)   
 [メッセージキュータスクエディター &#40;送信ページ&#41;](../../2014/integration-services/message-queue-task-editor-send-page.md)   
 [[式] ページ](expressions/expressions-page.md)   
 [メッセージ キュー タスク](control-flow/message-queue-task.md)  
  
  

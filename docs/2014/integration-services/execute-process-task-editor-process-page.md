---
title: プロセス実行タスク エディター ([プロセス] ページ) |Microsoft ドキュメント
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
- sql12.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 9257d82ea948a8f5561d62af2db8f28ce1bdcdfc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36072567"
---
# <a name="execute-process-task-editor-process-page"></a>Execute Process Task Editor (Process Page)
  **[プロセス実行タスク エディター]** ダイアログ ボックスの **[処理]** ページを使用すると、プロセスを実行する際のオプションを構成できます。 オプションには、実行する実行可能ファイル、そのファイルの場所、コマンド プロンプト引数、入力するための変数、出力をキャプチャする変数などが含まれます。  
  
 このタスクの詳細については、「 [Execute Process Task](control-flow/execute-process-task.md)」を参照してください。  
  
## <a name="options"></a>および  
 **[RequireFullFileName]**  
 指定した場所に実行可能ファイルが見つからなかった場合に、タスクを中止するかどうかを指定します。  
  
 **[実行可能ファイル]**  
 実行する実行可能ファイルの名前を入力します。  
  
 **引数**  
 コマンド プロンプト引数を指定します。  
  
 **[WorkingDirectory]**  
 実行可能ファイルが置かれているフォルダーのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてフォルダーを指定します。  
  
 **[StandardInputVariable]**  
 プロセスへの入力を指定する変数を選択するか、\<[**新しい変数>]** をクリックして新しい変数を作成します。  
  
 **関連項目:**[変数の追加  ](../../2014/integration-services/add-variable.md)  
  
 **[StandardOutputVariable]**  
 プロセスの出力をキャプチャする変数を選択するか、\<[**新しい変数]** をクリックして新しい変数を作成します。  
  
 **[StandardErrorVariable]**  
 プロセッサのエラー出力をキャプチャする変数を選択するか、\<[**新しい変数>]** をクリックして新しい変数を作成します。  
  
 **[FailTaskIfReturnCodeIsNotSuccessValue]**  
 プロセス終了コードが **[SuccessValue]** で指定されている値と異なった場合、タスクを終了するかどうかを指定します。  
  
 **[SuccessValue]**  
 実行可能ファイルが正常に終了した場合に返される値を指定します。 既定では、この値は **0**に設定されます。  
  
 **[TimeOut]**  
 プロセスを実行できる秒数を指定します。 値を **0** に指定すると、タイムアウト値が使用されず、プロセスは完了するかエラーが発生するまで実行されます。  
  
 **[TerminateProcessAfterTimeOut]**  
 **[TimeOut]** オプションで指定されたタイムアウト時間の後に、プロセスを強制終了するかどうかを指定します。 このオプションは、 **[TimeOut]** が **0**以外の場合にのみ使用できます。  
  
 **[WindowStyle]**  
 プロセスを実行する際のウィンドウのスタイルを指定します。  
  
## <a name="see-also"></a>参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [[式] ページ](expressions/expressions-page.md)  
  
  
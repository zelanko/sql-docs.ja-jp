---
title: "プロセス実行タスク エディター ([プロセス] ページ) |Microsoft ドキュメント"
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
- sql13.dts.designer.executeprocesstask.process.f1
helpviewer_keywords:
- Execute Process Task Editor
ms.assetid: 0fc22406-e79b-47a4-a7e4-108d4ce6202f
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: a67668d07ec12efde2009268e8d0a4dae13d2130
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="execute-process-task-editor-process-page"></a>Execute Process Task Editor (Process Page)
  **[プロセス実行タスク エディター]** ダイアログ ボックスの **[処理]** ページを使用すると、プロセスを実行する際のオプションを構成できます。 オプションには、実行する実行可能ファイル、そのファイルの場所、コマンド プロンプト引数、入力するための変数、出力をキャプチャする変数などが含まれます。  
  
 このタスクの詳細については、「 [Execute Process Task](../../integration-services/control-flow/execute-process-task.md)」を参照してください。  
  
## <a name="options"></a>オプション  
 **[RequireFullFileName]**  
 指定した場所に実行可能ファイルが見つからなかった場合に、タスクを中止するかどうかを指定します。  
  
 **[実行可能ファイル]**  
 実行する実行可能ファイルの名前を入力します。  
  
 **引数**  
 コマンド プロンプト引数を指定します。  
  
 **[WorkingDirectory]**  
 実行可能ファイルが置かれているフォルダーのパスを入力するか、参照ボタン ( **[...]** ) をクリックしてフォルダーを指定します。  
  
 **[StandardInputVariable]**  
 変数を選択して、プロセスへの入力を指定するか、をクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **関連項目:** [変数の追加](http://msdn.microsoft.com/library/d09b5d31-433f-4f7c-8c68-9df3a97785d5)  
  
 **[StandardOutputVariable]**  
 変数を選択して、プロセスの出力をキャプチャするかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **[StandardErrorVariable]**  
 変数を選択して、プロセッサのエラー出力をキャプチャするかをクリックして\<**新しい変数しています.**> 新しい変数を作成します。  
  
 **[FailTaskIfReturnCodeIsNotSuccessValue]**  
 プロセス終了コードが **[SuccessValue]**で指定されている値と異なった場合、タスクを終了するかどうかを指定します。  
  
 **[SuccessValue]**  
 実行可能ファイルが正常に終了した場合に返される値を指定します。 既定では、この値は **0**に設定されます。  
  
 **[TimeOut]**  
 プロセスを実行できる秒数を指定します。 値を **0** に指定すると、タイムアウト値が使用されず、プロセスは完了するかエラーが発生するまで実行されます。  
  
 **[TerminateProcessAfterTimeOut]**  
 **[TimeOut]** オプションで指定されたタイムアウト時間の後に、プロセスを強制終了するかどうかを指定します。 このオプションは、 **[TimeOut]** が **0**以外の場合にのみ使用できます。  
  
 **[WindowStyle]**  
 プロセスを実行する際のウィンドウのスタイルを指定します。  
  
## <a name="see-also"></a>「  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[式] ページ](../../integration-services/expressions/expressions-page.md)  
  
  

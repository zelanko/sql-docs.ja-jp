---
title: "スクリプトのデバッグ | Microsoft Docs"
ms.custom: ""
ms.date: "03/17/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "スクリプト タスク [Integration Services]、デバッグ"
  - "デバッグ [Integration Services]、スクリプト"
  - "スクリプト [Integration Services]、デバッグ"
ms.assetid: fddf57d8-8607-4f88-85a0-1b683087b491
caps.latest.revision: 57
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 57
---
# スクリプトのデバッグ
  スクリプト タスクやスクリプト コンポーネントで使うスクリプトは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) で作成します。  
  
 VSTA では、ブレークポイントを設定してスクリプト化します。 ブレークポイントは VSTA で管理できますが、[!INCLUDE[ssIS](../../includes/ssis-md.md)] デザイナーで用意されている **[ブレークポイントの設定]** ダイアログ ボックスを使用しても管理できます。 詳細については、「[制御フローのデバッグ](../../integration-services/troubleshooting/debugging-control-flow.md)」を参照してください。  
  
 **[ブレークポイントの設定]** ダイアログ ボックスには、スクリプト ブレークポイントが含まれています。 スクリプト ブレークポイントは、ブレークポイントの一覧の一番下に表示され、ブレークポイントが設定されている行番号と関数の名前を表示します。 スクリプト ブレークポイントは、**[ブレークポイントの設定]** ダイアログ ボックスで削除できます。  
  
 実行時に、スクリプトのコード行に設定されたブレークポイントは、パッケージ、またはパッケージ内のタスクやコンテナーに設定されたブレークポイントと統合されます。 デバッガーは、スクリプト内のブレークポイントから、パッケージ、タスク、またはコンテナーに設定されたブレークポイントまで実行できます。また、その逆の実行も可能です。 たとえば、**OnPreExecute** イベントまたは **OnPostExecute** イベントを受け取ったときに発生するブレークの条件で、設定されたブレークポイントがパッケージにあり、スクリプト行にブレークポイントが設定されたスクリプト タスクがあるとします。 この場合、パッケージは **OnPreExecute** イベントに関連付けられたブレークの条件で実行を中断し、スクリプト内のブレークポイントまで実行して、最終的に **OnPostExecute** イベントに関連付けられたブレークの条件まで実行できます。  
  
 スクリプト タスクとスクリプト コンポーネントのデバッグの詳細については、「[スクリプト タスクのコーディングおよびデバッグ](../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)」および「[スクリプト コンポーネントのコーディングおよびデバッグ](../../integration-services/extending-packages-scripting/data-flow-script-component/coding-and-debugging-the-script-component.md)」を参照してください。  
  
### Visual Studio for Applications でブレークポイントを設定するには  
  
-   [スクリプト タスクとスクリプト コンポーネントにブレークポイントを設定してスクリプトをデバッグする](../../integration-services/extending-packages-scripting/debug-a-script-by-setting-breakpoints-in-a-script-task-and-script-component.md)  
  
## 参照  
 [パッケージ開発のトラブルシューティング ツール](../../integration-services/troubleshooting/troubleshooting-tools-for-package-development.md)  
  
  
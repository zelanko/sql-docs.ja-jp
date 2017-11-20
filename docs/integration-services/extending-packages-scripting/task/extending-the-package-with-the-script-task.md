---
title: "スクリプト タスクを使用してパッケージを拡張 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-non-specified
ms.prod_service: integration-services
ms.service: 
ms.component: extending-packages-scripting
ms.reviewer: 
ms.suite: sql
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- scripts [Integration Services]
- SSIS Script task
- tasks [Integration Services], scripts
- Script task [Integration Services], about Script task
- scripts [Integration Services], about Script task with packages
- SSIS Script task, about Script task
ms.assetid: 911e6d26-a6fd-4fc3-a111-bf5f048e9bff
caps.latest.revision: 57
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: b2e0b0a933568f8313cefd2f1d6dbdd02f5d3cbc
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="extending-the-package-with-the-script-task"></a>スクリプト タスクによるパッケージの拡張
  スクリプト タスクの実行時の機能を拡張[!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]で記述されたカスタム コードを持つパッケージ[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual Basic または[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual C# でコンパイルおよび実行される、パッケージの実行時にします。 スクリプト タスクは、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] に含まれているタスクが十分に要件を満たしていない場合に、カスタム ランタイム タスクの開発を単純化します。 必要なすべてのインフラストラクチャ コードがスクリプト タスクによって自動生成されるため、カスタム処理を実行するために必要なコードの記述に集中できます。  
  
 スクリプト タスクはグローバルを使用して、親パッケージと対話**Dts**オブジェクトのインスタンス、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel>スクリプト環境で公開されているクラスです。 スクリプト タスク内でコードを記述して、[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] 変数に格納された値を変更できます。その後、更新した変数の値をパッケージで使用して、ワークフローのパスを決定できます。 また、カスタム アセンブリだけでなく、[!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] 名前空間および [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] クラス ライブラリを使用して、スクリプト タスクに独自の機能を実装することもできます。  
  
 スクリプト タスクおよびそれによって生成されるインフラストラクチャ コードを活用すれば、カスタム タスクを開発するための手順を大幅に簡略化できます。 ただし、スクリプト タスクのしくみを理解することがあります方が便利なセクションを参照する[カスタム タスクの開発](../../../integration-services/extending-packages-custom-objects/task/developing-a-custom-task.md)カスタム タスクの開発に必要な手順について説明します。  
  
 作成したタスクを複数のパッケージで再利用する予定がある場合は、スクリプト タスクではなく、カスタム タスクを開発することを検討してください。 詳細については、次を参照してください。[スクリプト ソリューションの比較およびカスタム オブジェクト](../../../integration-services/extending-packages-scripting/comparing-scripting-solutions-and-custom-objects.md)です。  
  
## <a name="in-this-section"></a>このセクションの内容  
 次のトピックでは、スクリプト タスクの詳細について説明します。  
  
 [スクリプト タスク エディターで、スクリプト タスクを構成します。](../../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)  
 について説明する方法で構成するプロパティ、**スクリプト タスク エディター**機能や、スクリプト タスク内のコードのパフォーマンスに影響します。  
  
 [コーディングおよびスクリプト タスクのデバッグ](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
 使用する方法について説明します[!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) スクリプト タスクに含まれているスクリプトを作成します。  
  
 [スクリプト タスクで変数の使用](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> プロパティを介して変数を使用する方法について説明します。  
  
 [スクリプト タスク内のデータ ソースに接続します。](../../../integration-services/extending-packages-scripting/task/connecting-to-data-sources-in-the-script-task.md)  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Connections%2A> プロパティを介して接続を使用する方法について説明します。  
  
 [スクリプト タスクでイベントを発生させる](../../../integration-services/extending-packages-scripting/task/raising-events-in-the-script-task.md)  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Events%2A> プロパティを介してイベントを発生させる方法について説明します。  
  
 [スクリプト タスクでログ記録](../../../integration-services/extending-packages-scripting/task/logging-in-the-script-task.md)  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Log%2A> メソッドを介して情報をログに記録する方法について説明します。  
  
 [スクリプト タスクから結果を返す](../../../integration-services/extending-packages-scripting/task/returning-results-from-the-script-task.md)  
 <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.TaskResult%2A> および <xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.ExecutionValue%2A> プロパティを介して結果を返す方法について説明します。  
  
 [スクリプト タスクの例](../../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)  
 スクリプト タスクの使用方法を示す簡単な例をいくつか提供します。  
  
## <a name="see-also"></a>参照  
 [スクリプト タスク](../../../integration-services/control-flow/script-task.md)   
 [スクリプト タスクおよびスクリプト コンポーネントの比較](../../../integration-services/extending-packages-scripting/comparing-the-script-task-and-the-script-component.md)  
  
  


---
title: "スクリプト タスク エディターでスクリプト タスクの構成 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/15/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- dbe-xml
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
caps.latest.revision: 35
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: 182a7b8f04c2339a8f3d3b986c978a7998c8a9c3
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a>スクリプト タスク エディターでのスクリプト タスクの構成
  3 つのページで、主要なプロパティを構成するスクリプト タスクでカスタム コードを記述する前に、**スクリプト タスク エディター**です。 スクリプト タスクに対して一意でない追加のタスク プロパティは、[プロパティ] ウィンドウを使用して設定できます。  
  
> [!NOTE]  
>  スクリプトをプリコンパイルするかどうかを指定できた以前のバージョンとは異なり、[!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 以降ではすべてのスクリプトがプリコンパイルされます。  
  
## <a name="general-page-of-the-script-task-editor"></a>[スクリプト タスク エディター] の [全般] ページ  
 **全般**のページ、**スクリプト タスク エディター**、一意の名前と、スクリプト タスクの説明を割り当てます。  
  
## <a name="script-page-of-the-script-task-editor"></a>[スクリプト タスク エディター] の [スクリプト] ページ  
 **スクリプト**のページ、**スクリプト タスク エディター**スクリプト タスクのカスタム プロパティが表示されます。  
  
### <a name="scriptlanguage-property"></a>ScriptLanguage プロパティ  
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)][!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) をサポートしている、 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または[!INCLUDE[msCoName](../../../includes/msconame-md.md)]Visual c# のプログラミング言語です。 値を変更することはできません、スクリプト タスクでスクリプトを作成した後、 **[scriptlanguage]**プロパティです。  
  
 スクリプト タスクおよびスクリプト コンポーネントの既定のスクリプト言語を設定するには、使用、 **scriptlanguage**プロパティを**全般**のページ、**オプション** ダイアログ ボックス。 詳細については、「 [General Page](https://msdn.microsoft.com/library/ms189436(v=sql.110).aspx)」を参照してください。  
  
### <a name="entrypoint-property"></a>EntryPoint プロパティ  
 **EntryPoint**プロパティのメソッドを指定する、 **ScriptMain**クラス、vsta プロジェクトを[!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)]ランタイムが呼び出す、スクリプト タスク コードへのエントリ ポイントとして。 **ScriptMain**クラスは、スクリプト テンプレートによって生成される既定のクラスです。  
  
 VSTA プロジェクトでメソッドの名前を変更する場合は、 **EntryPoint** プロパティの値を変更する必要があります。  
  
### <a name="readonlyvariables-and-readwritevariables-properties"></a>ReadOnlyVariables プロパティおよび ReadWriteVariables プロパティ  
 既存の変数をコンマ区切りリストとして、これらのプロパティの値に入力すると、スクリプト タスクのコード内で、その変数に読み取り専用アクセスまたは読み取り/書き込みアクセスできるようになります。 両方の種類の変数には使用してコードにアクセス、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A>のプロパティ、 **Dts**オブジェクト。 詳細については、「 [スクリプト タスクでの変数の使用](../../../integration-services/extending-packages-scripting/task/using-variables-in-the-script-task.md)」を参照してください。  
  
> [!NOTE]  
>  変数名の大文字と小文字は区別されます。  
  
 変数を選択するには、省略記号をクリックします (**.**)、プロパティ フィールドの横にあるボタンをクリックします。 詳細については、次を参照してください。[変数 ページの選択](../../../integration-services/control-flow/select-variables-page.md)です。  
  
### <a name="edit-script-button"></a>[スクリプトの編集] ボタン  
 **スクリプトの編集**ボタンは、カスタム スクリプトを記述する VSTA 開発環境を起動します。 詳細については、次を参照してください。[コーディングし、スクリプト タスクのデバッグ](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)です。  
  
## <a name="expressions-page-of-the-script-task-editor"></a>[スクリプト タスク エディター] の [式] ページ  
 **式**のページ、**スクリプト タスク エディター**、上記のスクリプト タスクのプロパティおよびその他の多くのタスクのプロパティの値を指定する式を使用することができます。 詳細については、「[Integration Services &#40;SSIS&#41; の式](../../../integration-services/expressions/integration-services-ssis-expressions.md)」を参照してください。  
  
## <a name="see-also"></a>参照  
 [コーディングおよびスクリプト タスクのデバッグ](../../../integration-services/extending-packages-scripting/task/coding-and-debugging-the-script-task.md)  
  
  


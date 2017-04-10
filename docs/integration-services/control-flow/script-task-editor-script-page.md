---
title: "[スクリプト タスク エディター] ([スクリプト] ページ) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.scripttask.script.f1"
helpviewer_keywords: 
  - "スクリプト タスク エディター"
ms.assetid: 93da0e0d-83f5-406d-b144-4cce216571cb
caps.latest.revision: 42
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 40
---
# [スクリプト タスク エディター] ([スクリプト] ページ)
  **[スクリプト タスク エディター]** ダイアログ ボックスの **[スクリプト]** ページを使用すると、スクリプト プロパティを設定し、スクリプトによってアクセスできる変数を指定できます。  
  
> [!NOTE]  
>  [!INCLUDE[ssISversion10](../../includes/ssisversion10-md.md)] およびそれ以降のバージョンでは、すべてのスクリプトがプリコンパイル済みです。 以前のバージョンでは、**PrecompileScriptIntoBinaryCode** プロパティを設定して、スクリプトを事前コンパイルするかどうかを指定していました。  
  
 スクリプト タスクの詳細については、「 [Script Task](../../integration-services/control-flow/script-task.md) 」および「 [Configuring the Script Task in the Script Task Editor](../../integration-services/extending-packages-scripting/task/configuring-the-script-task-in-the-script-task-editor.md)」を参照してください。 スクリプト タスクのプログラミングの詳細については、「 [Extending the Package with the Script Task](../../integration-services/extending-packages-scripting/task/extending-the-package-with-the-script-task.md)」を参照してください。  
  
## オプション  
 **[ScriptLanguage]**  
 タスクのスクリプト言語を選択します。[!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../includes/msconame-md.md)] Visual C# のいずれかです。  
  
 タスクのスクリプトを作成した後に、**[ScriptLanguage]** プロパティの値を変更することはできません。  
  
 スクリプト タスクの既定のスクリプト言語を設定するには、**[オプション]** ダイアログ ボックスの **[全般]** ページにある **[スクリプト言語]** オプションを使用します。 詳細については、「 [General Page](../Topic/General%20Page.md)」を参照してください。  
  
 **[EntryPoint]**  
 スクリプト タスクのコードのエントリ ポイントとして [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] ランタイムが呼び出すメソッドを指定します。 指定するメソッドは、[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] Tools for Applications (VSTA) プロジェクトの ScriptMain クラスに存在する必要があります。ScriptMain クラスは、スクリプト テンプレートによって生成される既定のクラスです。  
  
 VSTA プロジェクトでメソッドの名前を変更する場合は、**EntryPoint** プロパティの値を変更する必要があります。  
  
 **[ReadOnlyVariables]**  
 スクリプトに使用できる読み取り専用の変数の一覧をコンマ区切りで入力するか、省略記号ボタン (**[...]**) をクリックして **[変数の選択]** ダイアログ ボックスで変数を選択します。  
  
> [!NOTE]  
>  変数名では大文字と小文字が区別されます。  
  
 **[ReadWriteVariables]**  
 スクリプトに使用できる読み取り/書き込み用の変数の一覧をコンマ区切りで入力するか、省略記号ボタン (**[...]**) をクリックして **[変数の選択]** ダイアログ ボックスで変数を選択します。  
  
> [!NOTE]  
>  変数名では大文字と小文字が区別されます。  
  
 **[スクリプトの編集]**  
 スクリプトを作成または変更できる VSTA IDE が開きます。  
  
## 参照  
 [Integration Services のエラーおよびメッセージのリファレンス](../../integration-services/integration-services-error-and-message-reference.md)   
 [[全般] ページ](../Topic/General%20Page.md)   
 [[スクリプト タスク エディター] &#40;[全般] ページ&#41;](../Topic/Script%20Task%20Editor%20\(General%20Page\).md)   
 [[式] ページ](../Topic/Expressions%20Page.md)   
 [スクリプト タスクの例](../../integration-services/extending-packages-scripting-task-examples/script-task-examples.md)   
 [Integration Services &#40;SSIS&#41; の変数](../../integration-services/integration-services-ssis-variables.md)   
 [パッケージ内のユーザー定義変数のスコープの追加、削除、変更](../Topic/Add,%20Delete,%20Change%20Scope%20of%20User-Defined%20Variable%20in%20a%20Package.md)  
  
  
---
title: スクリプト タスク エディターでのスクリプト タスクの構成 | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script task [Integration Services], configuring
- Script Task Editor
- SSIS Script task, configuring
ms.assetid: 232de0c9-b24d-4c38-861d-6c1f4a75bdf3
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 7060990b409773abd4f574e46dd0671c71f1374f
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78176151"
---
# <a name="configuring-the-script-task-in-the-script-task-editor"></a>スクリプト タスク エディターでのスクリプト タスクの構成
  スクリプト タスクにカスタム コードを記述する前に、 **[スクリプト タスク エディター]** の 3 つのページで、主要なプロパティを設定します。 スクリプト タスクに対して一意でない追加のタスク プロパティは、[プロパティ] ウィンドウを使用して設定できます。

> [!NOTE]
>  スクリプトをプリコンパイルするかどうかを指定できた以前のバージョンとは異なり、[!INCLUDE[ssISversion10](../../../includes/ssisversion10-md.md)] 以降ではすべてのスクリプトがプリコンパイルされます。

## <a name="general-page-of-the-script-task-editor"></a>[スクリプト タスク エディター] の [全般] ページ
 **[スクリプト タスク エディター]** の **[全般]** ページでは、スクリプト タスクに一意の名前および説明を割り当てます。

## <a name="script-page-of-the-script-task-editor"></a>[スクリプト タスク エディター] の [スクリプト] ページ
 **[スクリプト タスク エディター]** の **[スクリプト]** ページには、スクリプト タスクのカスタム プロパティが表示されます。

### <a name="scriptlanguage-property"></a>ScriptLanguage プロパティ
 [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)] Tools for Applications (VSTA) では、[!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual Basic または [!INCLUDE[msCoName](../../../includes/msconame-md.md)] Visual C# のプログラミング言語がサポートされます。 スクリプト タスクにスクリプトを作成した後で、 **[ScriptLanguage]** プロパティの値を変更することはできません。

 スクリプト タスクとスクリプト コンポーネントの既定のスクリプト言語を設定するには、 **[オプション]** ダイアログ ボックスの **[全般]** ページにある **[ScriptLanguage]** プロパティを使用します。 詳細については、「 [General Page](../../general-page-of-integration-services-designers-options.md)」を参照してください。

### <a name="entrypoint-property"></a>EntryPoint プロパティ
 
  `EntryPoint` プロパティは、スクリプト タスク コードのエントリ ポイントとして `ScriptMain` ランタイムが呼び出す、VSTA プロジェクトの [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] クラスのメソッドを指定します。 
  `ScriptMain` クラスは、スクリプト テンプレートによって生成される既定のクラスです。

 VSTA プロジェクトでメソッドの名前を変更する場合は、`EntryPoint` プロパティの値を変更する必要があります。

### <a name="readonlyvariables-and-readwritevariables-properties"></a>ReadOnlyVariables プロパティおよび ReadWriteVariables プロパティ
 既存の変数をコンマ区切りリストとして、これらのプロパティの値に入力すると、スクリプト タスクのコード内で、その変数に読み取り専用アクセスまたは読み取り/書き込みアクセスできるようになります。 どちらの種類の変数にも、<xref:Microsoft.SqlServer.Dts.Tasks.ScriptTask.ScriptObjectModel.Variables%2A> オブジェクトの `Dts` プロパティを介して、コード内でアクセスします。 詳細については、「 [スクリプト タスクでの変数の使用](../../extending-packages-scripting/task/using-variables-in-the-script-task.md)」を参照してください。

> [!NOTE]
>  変数名の大文字と小文字は区別されます。

 変数を選択するには、プロパティ フィールドの横にある参照ボタン **[...]** をクリックします。 詳細については、「[[変数の選択] ページ](../../control-flow/select-variables-page.md)」を参照してください。

### <a name="edit-script-button"></a>[スクリプトの編集] ボタン
 **[スクリプトの編集]** ボタンをクリックすると VSTA 開発環境が起動し、カスタム スクリプトを記述できるようになります。 詳細については、「[スクリプト タスクのコーディングおよびデバッグ](coding-and-debugging-the-script-task.md)」を参照してください。

## <a name="expressions-page-of-the-script-task-editor"></a>[スクリプト タスク エディター] の [式] ページ
 **[スクリプト タスク エディター]** の **[式]** ページでは、式を使用して、上に挙げたスクリプト タスクのプロパティ、およびそれ以外の多くのプロパティに値を指定できます。 詳細については、「 [Integration Services (SSIS) 式](../../expressions/integration-services-ssis-expressions.md)に評価されるまでそのワークフローを繰り返します。

![Integration Services アイコン (小)](../../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> 
  [!INCLUDE[msCoName](../../../includes/msconame-md.md)] が提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services に関するページを参照してください。](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。

## <a name="see-also"></a>参照
 [スクリプト タスクのコーディングおよびデバッグ](coding-and-debugging-the-script-task.md)



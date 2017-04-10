---
title: "[変数] ウィンドウ | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.variables.f1"
  - "sql13.dts.designer.variableoptionswindow.f1"
helpviewer_keywords: 
  - "[変数] ウィンドウ"
ms.assetid: f405e5ce-ef69-4c58-8c7d-a3d44dfe9ab0
caps.latest.revision: 53
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 52
---
# [変数] ウィンドウ
  **[変数]** ウィンドウを使用すると、ユーザー定義変数を作成、変更し、システム変数を表示できます。  
  
 既定では、**[変数]** ウィンドウは [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)] の SSIS デザイナーの **[接続マネージャー]** 領域の下にあります。 **[変数]** ウィンドウが表示されない場合は、**[SSIS]** メニューの **[変数]** をクリックして、ウィンドウを表示します。  
  
 必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、**[変数]** ウィンドウを表示することもできます。  
  
> [!NOTE]  
>  **Name** プロパティと **Namespace** プロパティの値の最初の文字は、Unicode Standard 2.0 に定義されているアルファベット文字か、アンダースコア (_) にする必要があります。 2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (\_) を使用できます。  
  
## オプション  
 **[変数の追加]**  
 ユーザー定義変数を追加します。  
  
 **変数の移動**  
 一覧で変数をクリックし、**[変数の移動]** をクリックして変数のスコープを変更します。 **[新しいスコープの選択]** ダイアログ ボックスで、パッケージまたはパッケージ内のコンテナー、タスク、またはイベント ハンドラーを選択して、変数のスコープを変更します。  
  
 変数のスコープの詳細については、「[Integration Services &#40;SSIS&#41; の変数](../integration-services/integration-services-ssis-variables.md)」を参照してください。  
  
 **変数の削除**  
 変数を一覧から選択し、**[変数の削除]** をクリックします。  
  
 **グリッドのオプション**  
 クリックすると **[可変グリッドのオプション]** ダイアログ ボックスが開きます。このダイアログ ボックスで、列の選択を変更したり、**[変数]** ウィンドウにフィルターを適用したりできます。 詳細については、「[可変グリッドのオプション](../integration-services/variable-grid-options.md)」を参照してください。  
  
 **名前**  
 変数名を表示します。 ユーザー定義変数の名前を更新できます。  
  
 **スコープ**  
 変数のスコープを表示します。 変数には、パッケージ全体のスコープまたはコンテナーやタスクのスコープがあります。 変数のスコープは、変数の値の読み取りや設定を必要とする他のタスクやコンポーネントからアクセスできるように十分な範囲を指定する必要があります。  
  
 スコープを変更するには、変数をクリックして **[変数]** ウィンドウの **[変数の移動]** をクリックします。  
  
 **データ型**  
 変数のデータ型が表示されます。 一覧からユーザー定義変数のデータ型を選択できます。  
  
> [!NOTE]  
>  変数に式を割り当てる場合は、データ型を変更できません。  
  
 **値**  
 変数の値を表示します。 ユーザー定義変数の値を更新できます。 この値は、リテラルまたは式にすることができます。また、複数行の文字列にすることもできます。 変数に式を割り当てるには、**[変数]** ウィンドウの **[式]** 列の横にある参照ボタンをクリックします。  
  
 **名前空間**  
 名前空間名を表示します。 ユーザー定義変数は、最初に**ユーザー**名前空間で作成されますが、**[名前空間]** フィールドで名前空間名を変更できます。 この列を表示するには、**[グリッドのオプション]** をクリックします。  
  
 **[Raise Change Event]**  
 値を変更した場合に **OnVariableValueChanged** イベントを発生させるかどうかを示します。 ユーザー定義変数およびシステム変数の値を更新できます。 既定では、**[変数]** ウィンドウにこの列は表示されません。 この列を表示するには、**[グリッドのオプション]** をクリックします。  
  
 **Description**  
 変数の説明を表示します。 ユーザー定義変数の説明を変更できます。 既定では、**[変数]** ウィンドウにこの列は表示されません。 この列を表示するには、**[グリッドのオプション]** をクリックします。  
  
 **式**  
 変数に割り当てられた式を表示します。 式を割り当てるには、参照ボタンをクリックします。  
  
 変数に式を割り当てると、変数の横に特別なアイコン マーカーが表示されます。 この特別なアイコン マーカーは、式が設定されている接続マネージャーおよびタスクの横にも表示されます。  
  
## 参照  
 [Integration Services &#40;SSIS&#41; の変数](../integration-services/integration-services-ssis-variables.md)   
 [パッケージで変数を使用する](../Topic/Use%20Variables%20in%20Packages.md)   
 [Integration Services &#40;SSIS&#41; の式](../integration-services/expressions/integration-services-ssis-expressions.md)   
 [パッケージ実行用のダンプ ファイルを生成する](../integration-services/troubleshooting/generating-dump-files-for-package-execution.md)  
  
  
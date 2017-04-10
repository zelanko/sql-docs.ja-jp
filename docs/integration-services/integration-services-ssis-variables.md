---
title: "Integration Services (SSIS) の変数 | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "変数 [Integration Services], パッケージ間での受け渡し"
  - "ユーザー定義変数 [Integration Services]"
  - "スコープ [Integration Services]"
  - "システム変数 [Integration Services]"
  - "変数 [Integration Services]"
  - "変数 [Integration Services], 変数について"
  - "値 [Integration Services]"
ms.assetid: c1e81ad6-628b-46d4-9b09-d2866517b6ca
caps.latest.revision: 60
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 59
---
# Integration Services (SSIS) の変数
  変数には、[!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージと、パッケージに含まれるコンテナー、タスク、およびイベント ハンドラーで、実行時に使用できる値が格納されます。 スクリプト タスクおよびスクリプト コンポーネント内のスクリプトも、変数を使用できます。 タスクとコンテナーにワークフロー内での順位を付ける優先順位制約では、制約の定義に式を含める場合に変数を使用できます。  
  
 変数は、次の目的で [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] パッケージ内で使用できます。  
  
-   実行時に、パッケージ要素のプロパティを更新します。 たとえば、1 つの Foreach ループ コンテナーで許可できる実行可能ファイルの数を動的に設定できます。  
  
-   メモリ内に参照テーブルを組み込みます。 たとえば、パッケージは、データ値を持つ変数を読み込む SQL 実行タスクを実行できます。  
  
-   データ値を持つ変数を読み込み、それらを使用して WHERE 句の検索条件を指定します。 たとえば、SQL 実行タスク内の Transact-SQL ステートメントによって使用される変数の値をスクリプト タスク内のスクリプトで更新できます。  
  
-   整数値を持つ変数を読み込み、その値を使用してパッケージ制御フロー内のループを制御します。 たとえば、For ループ コンテナーの評価式内の変数を使用して繰り返しを制御できます。  
  
-   実行時に Transact-SQL ステートメントのパラメーター値を作成します。 たとえば、パッケージは SQL 実行タスクを実行し、変数を使用して Transact-SQL ステートメント内のパラメーターを動的に設定できます。  
  
-   変数値が含まれる式を構築します。 たとえば、派生列の変換は、変数値に列の値を乗算することによって取得した結果を使用して、列の値を設定できます。  
  
## システム変数とユーザー定義変数  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、ユーザー定義変数とシステム変数の、2 種類の変数がサポートされています。 ユーザー定義変数とはパッケージの開発者によって定義された変数で、システム変数とは [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] によって定義された変数です。 ユーザー定義変数は、パッケージで必要な数だけ作成できますが、システム変数は追加作成できません。  
  
 変数 (システム変数とユーザー定義変数) はすべて、SQL 実行タスクが使用するパラメーター バインドで使用して、SQL ステートメントのパラメーターに変数をマップできます。 詳細については、「[SQL 実行タスク](../integration-services/control-flow/execute-sql-task.md)」と「[SQL 実行タスクのパラメーターとリターン コード](../Topic/Parameters%20and%20Return%20Codes%20in%20the%20Execute%20SQL%20Task.md)」を参照してください。  
  
> [!NOTE]  
>  ユーザー定義変数とシステム変数の名前では、大文字と小文字が区別されます。  
  
 パッケージ、Foreach ループ コンテナー、For ループ コンテナー、シーケンス コンテナー、タスク、およびイベント ハンドラーの、すべての種類の [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] コンテナーに対してユーザー定義変数を作成できます。 ユーザー定義変数は、コンテナーの変数のコレクションのメンバーです。  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーを使用してパッケージを作成すると、変数のコレクションのメンバーは、[!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーの **[パッケージ エクスプローラー]** タブ上の **[変数]** フォルダー内に表示されます。 このフォルダーには、ユーザー定義変数とシステム変数が一覧表示されます。  
  
 ユーザー定義変数は、次の方法で構成できます。  
  
-   変数の名前と説明を指定します。  
  
-   変数の名前空間を指定します。  
  
-   変数値が変更されたときに、変数がイベントを起動するかどうかを示します。  
  
-   変数は読み取り専用か、読み取り/書き込み可能かを示します。  
  
-   式の評価結果を使用して、変数値を設定します。  
  
-   パッケージ、またはタスクなどのパッケージ オブジェクトのスコープ内に、変数を作成します。  
  
-   変数の値とデータ型を指定します。  
  
 システム変数で構成可能なオプションは、変数値が変更されたときにイベントを起動するかどうかを指定するオプションのみです。  
  
 コンテナーの種類ごとに、異なるセットのシステム変数を使用できます。 パッケージとパッケージ要素が使用するシステム変数の詳細については、「[システム変数](../integration-services/system-variables.md)」を参照してください。  
  
 変数の実際的な使用シナリオの詳細については、「[パッケージで変数を使用する](../Topic/Use%20Variables%20in%20Packages.md)」を参照してください。  
  
## 変数のプロパティ  
 **[変数]** ウィンドウまたは **[プロパティ]** ウィンドウで、次のプロパティを設定してユーザー定義変数を構成できます。 一部のプロパティは [プロパティ] ウィンドウでのみ使用できます。  
  
> [!NOTE]  
>  システム変数で構成可能なオプションは、変数値が変更されたときにイベントを起動するかどうかを指定するオプションのみです。  
  
 Description  
 変数の説明を指定します。  
  
 EvaluateAsExpression  
 このプロパティを **True** に設定すると、指定された式を使用して変数の値が設定されます。  
  
 式  
 変数に割り当てられる式を指定します。  
  
 名前  
 変数名を指定します。  
  
 名前空間  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] では、**User** および **System** という 2 つの名前空間が用意されています。 既定では、カスタム変数は **User** 名前空間に属し、システム変数は **System** 名前空間に属します。 ユーザー定義変数用に追加の名前空間を作成し、**User** 名前空間の名前を変更することはできますが、**System** 名前空間の名前を変更したり、変数を **System** 名前空間に追加したり、システム変数を別の名前空間に割り当てたりすることはできません。  
  
 RaiseChangedEvent  
 このプロパティを **True** に設定すると、変数の値が変更された場合に **OnVariableValueChanged** イベントが発生します。  
  
 ReadOnly  
 このプロパティを **False** に設定すると、変数は読み取り/書き込み用となります。  
  
 スコープ  
 > [!NOTE]  
>  **[変数]** ウィンドウの **[変数の移動]** をクリックすることによってしか、このプロパティの設定は変更できません。  
  
 変数は、パッケージのスコープ内、またはパッケージ内のコンテナー、タスク、またはイベント ハンドラーのスコープ内で作成されます。 パッケージ コンテナーは、コンテナー階層の最上層にあるため、パッケージ スコープを持つ変数はグローバル変数と同じように機能し、パッケージ内のすべてのコンテナーで使用できます。 同様に、For ループ コンテナーなどのコンテナーのスコープ内で定義された変数は、For ループ コンテナー内のすべてのタスクまたはコンテナーで使用できます。  
  
 パッケージでパッケージ実行タスクを使用して他のパッケージを実行する場合、呼び出し元のパッケージのスコープまたはパッケージ実行タスクで定義された変数は、構成の種類で親パッケージ変数を使用することにより、呼び出し先のパッケージで使用できます。 詳細については、「[パッケージ構成](../integration-services/packages/package-configurations.md)」を参照してください。  
  
 [IncludeInDebugDump]  
 変数値がデバッグ ダンプ ファイルに含まれるかどうかを示します。  
  
 ユーザー定義変数およびシステム変数の場合、**[InclueInDebugDump]** オプションの既定値は **true** です。  
  
 ただし、ユーザー定義変数に関しては、次の条件に該当する場合、システムによって **[IncludeInDebugDump]** オプションが **false** にリセットされます。  
  
-   **EvaluateAsExpression** 変数のプロパティが **true** に設定されている場合は、**IncludeInDebugDump** オプションが **false** にリセットされます。  
  
     式のテキストを変数値としてデバッグ ダンプ ファイルに含めるには、**[IncludeInDebugDump]** オプションを **true** に設定します。  
  
-   変数のデータ型が文字列に変更された場合は、**[IncludeInDebugDump]** オプションが **false** にリセットされます。  
  
 **[IncludeInDebugDump]** オプションが **false** にリセットされると、ユーザーが選択した値を上書きする場合があります。  
  
 値  
 ユーザー定義変数の値には、リテラルまたは式を設定できます。 変数には、変数値および変数のデータ型を設定するオプションが含まれています。 この 2 つのプロパティには互換性が必要です。たとえば、文字列の値を整数データ型に使用することはできません。  
  
 変数を式として評価するように構成した場合は、式を指定する必要があります。 式は実行時に評価され、変数は評価結果に設定されます。 たとえば、変数が式 `DATEPART("month", GETDATE())` を使用している場合、変数の値は、現在の日付の月と等しい数値になります。 式は、[!INCLUDE[ssIS](../includes/ssis-md.md)] 式の構文文法を使用する、有効な式である必要があります。 変数に式を使用する場合、リテラルおよび式文法が提供する演算子と関数も使用できますが、パッケージ内のデータ フローの列は参照できません。 式の最大長は 4,000 文字です。 詳細については、「[Integration Services &#40;SSIS&#41; の式](../integration-services/expressions/integration-services-ssis-expressions.md)」を参照してください。  
  
 ValueType  
 > [!NOTE]  
>  このプロパティの値は **[変数]** ウィンドウの **[データ型]** 列に表示されます。  
  
 変数の値のデータ型を指定します。  
  
## 変数の構成  
 プロパティを設定するには [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーから行うか、またはプログラムによって設定します。  
  
 [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで設定できるプロパティの詳細については、「[[変数] ウィンドウ](../Topic/Variables%20Window.md)」を参照してください。  
  
 変数のプロパティ、およびプログラムによるこれらのプロパティの設定方法の詳細については、「<xref:Microsoft.SqlServer.Dts.Runtime.Variable>」を参照してください。  
  
## 関連タスク  
 [パッケージ内のユーザー定義変数のスコープの追加、削除、変更](../Topic/Add,%20Delete,%20Change%20Scope%20of%20User-Defined%20Variable%20in%20a%20Package.md)  
  
 [ユーザー定義変数のプロパティを設定する](../Topic/Set%20the%20Properties%20of%20a%20User-Defined%20Variable.md)  
  
 [子パッケージでの変数およびパラメーターの値の使用](../integration-services/packages/use-the-values-of-variables-and-parameters-in-a-child-package.md)  
  
 [クエリ パラメーターをデータ フロー コンポーネントの変数にマップする](../integration-services/data-flow/map-query-parameters-to-variables-in-a-data-flow-component.md)  
  
  
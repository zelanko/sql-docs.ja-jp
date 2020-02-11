---
title: ユーザー定義変数 | のプロパティを設定します。Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- modifying variables
- variables [Integration Services], properties
ms.assetid: f98ddbec-f668-4dba-a768-44ac3ae0536f
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: aadfb7b53d22a00bf14699f611f20ce508a7ab5e
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055652"
---
# <a name="set-the-properties-of-a-user-defined-variable"></a>ユーザー定義変数のプロパティを設定する
  
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]でユーザー定義変数のプロパティを設定するには、次の機能のいずれかを使用します。  
  
-   [変数] ウィンドウ。  
  
-   [プロパティ] ウィンドウ。 
  **[プロパティ]** ウィンドウには、 **[変数]** ウィンドウでは使用できない変数 (Description、EvaluateAsExpression、Expression、ReadOnly、ValueType、および IncludeInDebugDump) を構成するためのプロパティが一覧表示されています。  
  
> [!NOTE]  
>  
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] には、RaiseChangedEvent プロパティを除き、更新できないプロパティを持つ一連のシステム変数もあります。  
  
 **変数への式の設定**  
  
 
  **[プロパティ]** ウィンドウを使用してユーザー定義変数に式を設定する場合:  
  
-   変数の値は、Value プロパティまたは Expression プロパティによって設定できます。 既定では、EvaluateAsExpression プロパティはに`False`設定され、変数の値は value プロパティによって設定されます。 式を使用して値を設定するには、最初に EvaluateAsExpression `True`をに設定してから、[式] プロパティに式を指定する必要があります。 Value プロパティには、自動的に式の評価結果が設定されます。  
  
-   ValueType プロパティには、Value プロパティの値のデータ型が含まれます。 Value が式によって設定される場合、ValueType は、式の評価結果と互換性があるデータ型に自動的に更新されます。 たとえば、値に0が含まれ、ValueType プロパティに**Int32**が含まれている場合、EXPRESSION を GETDATE () に設定すると、value には現在`DateTime`の日付と時刻が含まれ、ValueType はに設定されます。  
  
-   変数の **[プロパティ]** ウィンドウからは **[式ビルダー]** ダイアログ ボックスを開くことができます。 このツールを使用すると、式の作成、検証、および評価を行うことができます。 詳しくは、「[式ビルダー](expressions/expression-builder.md)」と「[Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)」をご覧ください。  
  
 
  **[変数]** ウィンドウを使用してユーザー定義変数に式を設定する場合:  
  
-   式を使用して変数の値を設定するには、まず、変数のデータ型が式の評価結果と互換性があることを確認し`Expression`てから、[**変数**] ウィンドウの列に式を指定します。 [**プロパティ**] ウィンドウの EvaluateAsExpression プロパティが自動的にに`True`設定されます。  
  
-   変数に式を割り当てると、変数の横に特別なアイコン マーカーが表示されます。 この特別なアイコン マーカーは、式が設定されている接続マネージャーおよびタスクの横にも表示されます。  
  
-   変数の **[変数]** ウィンドウからは **[式ビルダー]** ダイアログ ボックスを開くことができます。 このツールを使用すると、式の作成、検証、および評価を行うことができます。 詳しくは、「[式ビルダー](expressions/expression-builder.md)」と「[Integration Services &#40;SSIS&#41; の式](expressions/integration-services-ssis-expressions.md)」をご覧ください。  
  
 [**変数**] ウィンドウと [**プロパティ**] ウィンドウの両方で、変数に式を割り当て`EvaluateAsExpression` 、がに`True`設定されている場合は、変数のデータ型を変更することはできません。  
  
 **Namespace プロパティと Name プロパティの設定**  
  
 
  `Name` プロパティと `Namespace` プロパティの値の最初の文字は、Unicode Standard 2.0 に定義されているアルファベット文字か、アンダースコア (_) にする必要があります。 2 番目以降の文字では、Unicode Standard 2.0 に定義されている文字または数字と、アンダースコア (\_) を使用できます。  
  
## <a name="using-the-variables-window-to-set-properties"></a>[変数] ウィンドウを使用したプロパティの設定  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-variables-window"></a>[変数] ウィンドウを使用して変数のプロパティを設定するには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージを右クリックして開きます。  
  
3.  
  **SSIS** メニューの **[変数]** をクリックします。  
  
     必要に応じて、View.Variables コマンドを **[オプション]** ダイアログ ボックスの **[キーボード]** ページで選択したキーの組み合わせにマップすることによって、 **[変数]** ウィンドウを表示することもできます。  
  
4.  必要に応じて、 **[変数]** ウィンドウで **[グリッドのオプション]** をクリックして、 **[変数]** ウィンドウに表示する列を選択したり、変数の一覧に適用するフィルターを選択したりします。  
  
5.  一覧で変数を選択し、、、**データ型**、 `Value` `Namespace`、 `Name`、 **Raise Change イベント**、 **Description、** および`Expression` columns の値を更新します。  
  
6.  一覧で変数を選択し、 **[変数の移動]** をクリックしてスコープを変更します。  
  
7.  更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="using-the-properties-window-to-set-properties"></a>[プロパティ] ウィンドウを使用したプロパティの設定  
  
#### <a name="to-set-the-properties-of-a-variable-by-using-the-properties-window"></a>[プロパティ] ウィンドウを使用して変数のプロパティを設定するには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージを右クリックして開きます。  
  
3.  **[表示]** メニューの **[プロパティ ウィンドウ]** をクリックします。  
  
4.  
  [!INCLUDE[ssIS](../includes/ssis-md.md)] デザイナーで、 **[パッケージ エクスプローラー]** タブをクリックし、[パッケージ] ノードを展開します。  
  
5.  パッケージの適用範囲の変数を変更するには、[変数] ノードを展開します。それ以外の場合は、変更する変数が含まれている [変数] ノードが表示されるまで、[イベント ハンドラー] または [実行可能ファイル] ノードを展開します。  
  
6.  変更するプロパティの変数をクリックします。  
  
7.  
  **[プロパティ]** ウィンドウで、読み取り/書き込みの変数プロパティを更新します。 ユーザー定義変数の場合は読み取り/読み取りのみのプロパティもあります。  
  
     プロパティの詳細については、「[Integration Services &#40;SSIS&#41; の変数](integration-services-ssis-variables.md)」を参照してください。  
  
8.  更新されたパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [SSIS&#41; 変数の Integration Services &#40;](integration-services-ssis-variables.md)   
 [パッケージで変数を使用する](../../2014/integration-services/use-variables-in-packages.md)   
 [パッケージ内のユーザー定義変数のスコープの追加、削除、変更](../../2014/integration-services/add-delete-change-scope-of-user-defined-variable-in-a-package.md)  
  
  

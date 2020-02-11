---
title: 優先順位制約のプロパティを設定する |Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- Precedence Constraint Editor dialog box
- precedence constraints [Integration Services], properties
ms.assetid: d990f600-5c09-4cd5-8528-0a58d79dc9f2
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: bc83e1b636aa03e37717ac62de1a44e9c6f1cfd2
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "66055736"
---
# <a name="set-the-properties-of-a-precedence-constraint"></a>優先順位制約のプロパティを設定する
  優先順位制約のプロパティを設定するには、次のいずれかのツールを使用します。  
  
-   
  **[優先順位制約エディター]** ダイアログ ボックスを使用します。  
  
-   [プロパティ] ウィンドウを使用します。 [プロパティ] ウィンドウには、 **[優先順位制約エディター]** ダイアログ ボックスでは使用できない優先順位制約を構成するためのプロパティが一覧表示されます。 [プロパティ] ウィンドウでは、優先順位制約の説明と名前を指定し、デザイン画面に表示する優先順位制約の注釈を構成することができます。  
  
 次の手順では、これらの各ツールを使用して優先順位制約のプロパティを設定する方法について説明します。  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-precedence-constraint-editor"></a>[優先順位制約エディター] を使用して優先順位制約のプロパティを設定するには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、目的のパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  
  **[制御フロー]** タブをクリックします。  
  
4.  優先順位制約をダブルクリックします。  
  
     
  **[優先順位制約エディター]** が開きます。  
  
5.  
  **[評価操作]** ドロップダウン リストで、評価操作を選択します。  
  
6.  `Value`ドロップダウンリストで、優先順位付き実行可能ファイルの実行結果を選択します。  
  
7.  評価操作で式を使用する場合は、 `Expression`ボックスに式を入力し、[**テスト**] をクリックして式を評価します。  
  
    > [!NOTE]  
    >  変数名の大文字と小文字は区別されます。  
  
8.  複数のタスクまたはコンテナーが制約付き実行可能ファイルに接続されている場合は、[**論理 AND** ] を選択し`true`て、上記のすべての実行可能ファイルの実行結果をに評価する必要があることを指定します。 [**論理 OR** ] を選択して、1つの実行`true`結果のみをに評価する必要があることを指定します。  
  
9. 
  **[OK]** をクリックし、 **[優先順位制約エディター]** を閉じます。  
  
10. 更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
### <a name="to-set-the-properties-of-a-precedence-constraint-by-using-the-properties-window"></a>[プロパティ] ウィンドウを使用して優先順位制約のプロパティを設定するには  
  
1.  
  [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]で、変更するパッケージが含まれている [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] プロジェクトを開きます。  
  
2.  ソリューション エクスプローラーで、パッケージをダブルクリックして開きます。  
  
3.  [**制御フロー** ] タブをクリックします。[**制御フロー** ] タブのデザイン画面で、優先順位制約を右クリックし、[**プロパティ**] をクリックします。 [プロパティ] ウィンドウで、プロパティの値を変更します。  
  
4.  
  **[プロパティ]** ウィンドウで、優先順位制約の次の読み取り/書き込みプロパティを設定します。  
  
    |読み取り/書き込みプロパティ|構成アクション|  
    |--------------------------|--------------------------|  
    |[説明]|説明を指定します。|  
    |EvalOp|評価操作を選択します。 、式`Expression`、および**定数**または式のいずれかの操作が選択されている**場合は、** 式を指定できます。|  
    |式|評価操作に and 式が含まれる場合は、式を指定します。 式はブール値に評価される必要があります。 式言語の詳細については、「[Integration Services &#40;SSIS&#41; 式](expressions/integration-services-ssis-expressions.md)」をご覧ください。|  
    |LogicalAnd|優先`LogicalAnd`順位制約を他の優先順位制約と共に評価するかどうかを指定するには、複数の実行可能ファイルの前に、制約付き実行可能ファイルにリンクします。|  
    |Name|優先順位制約の名前を更新します。|  
    |ShowAnnotation|使用する注釈の種類を指定します。 注釈を無効にするには **[Never]** 、要求時に注釈を有効にするには **[AsNeeded]** 、Name プロパティの値を使用して注釈を自動的に設定するには **[ConstraintName]** 、Description プロパティの値を使用して注釈を自動的に設定するには **[ConstraintDescription]** 、Value プロパティと Expression プロパティの値を使用して注釈を自動的に設定するには **[ConstraintOptions]** をそれぞれ選択します。|  
    |Value|EvalOP プロパティで指定された評価操作に制約が含まれる場合は、制約付き実行可能ファイルの実行結果を選択します。|  
  
5.  [プロパティ] ウィンドウを閉じます。  
  
6.  更新したパッケージを保存するには、 **[ファイル]** メニューの **[選択されたファイルを上書き保存]** をクリックします。  
  
## <a name="see-also"></a>参照  
 [優先順位制約](control-flow/precedence-constraints.md)   
 [既定の優先順位制約を使用してタスクとコンテナーを連結する](../../2014/integration-services/connect-tasks-and-containers-by-using-a-default-precedence-constraint.md)   
 [ショートカットメニューを使用して優先順位制約の値を設定する](../../2014/integration-services/set-the-value-of-a-precedence-constraint-by-using-the-shortcut-menu.md)   
 [優先順位制約で式を使用する](../../2014/integration-services/use-an-expression-in-a-precedence-constraint.md)  
  
  

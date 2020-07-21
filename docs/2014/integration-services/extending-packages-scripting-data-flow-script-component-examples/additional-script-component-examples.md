---
title: その他のスクリプト コンポーネントの例 | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: reference
dev_langs:
- VB
helpviewer_keywords:
- Script component [Integration Services], examples
ms.assetid: 849dd38a-abb5-4702-a413-882aae3980a5
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 897ca075674f5c3dbaf355390fe8346580bf638a
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/26/2020
ms.locfileid: "85426999"
---
# <a name="additional-script-component-examples"></a>その他のスクリプト コンポーネントの例
  スクリプト コンポーネントは構成可能なツールです。パッケージのデータ フローで使用すると、[!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] に備わっている変換元、変換、および変換先では満たせないほとんどすべての要件に対応できます。 ここでは、使用できるさまざまな種類の機能を説明する、スクリプト コンポーネントのコード例を示します。  
  
 スクリプト コンポーネントを基本の変換元、変換、または変換先として構成する方法の例については、「[特定の種類のスクリプト コンポーネントの開発](../extending-packages-scripting-data-flow-script-component-types/developing-specific-types-of-script-components.md)」を参照してください。  
  
> [!NOTE]  
>  複数のデータ フロー タスクおよび複数のパッケージでより簡単に再利用できるコンポーネントを作成する場合は、これらのスクリプト コンポーネント サンプルのコードを基にした、カスタム データ フロー コンポーネントの作成を検討してください。 詳細については、「 [カスタム データ フロー コンポーネントの開発](../extending-packages-custom-objects/data-flow/developing-a-custom-data-flow-component.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [スクリプト コンポーネントに対するエラー出力のシミュレート](../extending-packages-scripting-data-flow-script-component-examples/simulating-an-error-output-for-the-script-component.md)  
 スクリプト コンポーネントは標準エラー出力をサポートしませんが、若干の追加構成とコーディングを行うだけで標準エラー出力をシミュレートできます。  
  
 [スクリプト コンポーネントによるエラー出力の強化](../extending-packages-scripting-data-flow-script-component-examples/enhancing-an-error-output-with-the-script-component.md)  
 スクリプト コンポーネントを使用して標準エラー出力に追加情報を追加する方法を、説明および例示します。  
  
 [スクリプト コンポーネントによる ODBC 変換先の作成](../extending-packages-scripting-data-flow-script-component-examples/creating-an-odbc-destination-with-the-script-component.md)  
 スクリプト コンポーネントを使用して ODBC データ フローの変換先を作成する方法を、説明および例示します。  
  
 [スクリプト コンポーネントを使用した標準以外のテキスト ファイル形式の解析](../extending-packages-scripting-data-flow-script-component-examples/parsing-non-standard-text-file-formats-with-the-script-component.md)  
 2 つの標準以外のテキスト ファイル形式を変換先のテーブルに解析する方法を、説明および例示します。  
  
![Integration Services アイコン (小)](../media/dts-16.gif "Integration Services のアイコン (小)")**は Integration Services で最新の**状態を維持  <br /> マイクロソフトが提供する最新のダウンロード、アーティクル、サンプル、ビデオ、およびコミュニティで選択されたソリューションについては、MSDN の [!INCLUDE[ssISnoversion](../../includes/ssisnoversion-md.md)] のページを参照してください。<br /><br /> [MSDN の Integration Services のページを参照する](https://go.microsoft.com/fwlink/?LinkId=136655)<br /><br /> これらの更新が自動で通知されるようにするには、ページの RSS フィードを定期受信します。  
  
  

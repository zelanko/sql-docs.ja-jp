---
title: パス式 (XQuery) |マイクロソフトドキュメント
description: XQuery パス式がドキュメント内の要素、属性、テキスト ノードなどのノードを検索する方法について説明します。
ms.custom: ''
ms.date: 03/17/2017
ms.prod: sql
ms.prod_service: sql
ms.reviewer: ''
ms.technology: xml
ms.topic: language-reference
dev_langs:
- XML
helpviewer_keywords:
- axis step [XQuery]
- path expressions [XQuery]
- expressions [XQuery], path
ms.assetid: b93fa36c-bf69-46b9-b137-f597d66fd0c0
author: rothja
ms.author: jroth
ms.openlocfilehash: 0e4c87a0695c57461f444c8be4318bcd06cfdefe
ms.sourcegitcommit: a3f5c3742d85d21f6bde7c6ae133060dcf1ddd44
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/15/2020
ms.locfileid: "81388065"
---
# <a name="path-expressions-xquery"></a>パス式 (XQuery)
[!INCLUDE[tsql-appliesto-ss2012-xxxx-xxxx-xxx-md](../includes/tsql-appliesto-ss2012-xxxx-xxxx-xxx-md.md)]

  XQuery パス式は、ドキュメント内の要素、属性、テキスト ノードなどのノードを検索します。 パス式の結果は常に、結果シーケンス内でノードが重複することなく、ドキュメント順で生成されます。 パスを指定する場合は、省略された構文または省略構文を使用できます。 以下の説明では、主に省略しない構文を取り上げます。 省略構文については、このトピックで後述します。  
  
> [!NOTE]  
>  このトピックのサンプル クエリは **、ProductModel**テーブルの**xml**型列の**CatalogDescription**および**命令**に対して指定されているので、これらの列に格納されている XML ドキュメントの内容と構造について理解しておく必要があります。  
  
 パス式は、相対式または絶対式にすることができます。 次に、これら両方について説明します。  
  
-   相対パス式は、1 つまたは 2 つのスラッシュ (/ または //) で区切られた 1 つまたは複数のステップで構成されます。 たとえば、`child::Features`相対パス式で`Child`、コンテキスト ノードの子ノードのみを参照します。 これは、現在処理されているノードです。 この式は、コンテキスト\<ノードの要素ノードの子ノード>フィーチャーを取得します。  
  
-   絶対パス式は、1 つまたは 2 つのスラッシュ記号 (/または //) で始まり、その後にオプションの相対パスが続きます。 たとえば、式 `/child::ProductDescription` の先頭のスラッシュ記号は、この式が絶対パス式であることを示しています。 式の先頭にスラッシュ記号が付いている場合、コンテキスト ノードのドキュメント ルート ノードが返されるため、この\<式はドキュメント ルートの要素ノードの子> ProductDescription をすべて返します。  
  
     絶対パスが単一のスラッシュ記号で始まる場合、その後に相対パスが続く場合と、その後に続かない場合があります。 スラッシュ記号を 1 つだけ指定した場合、式はコンテキスト ノードのルート ノードを返します。 XML データ型の場合、これはドキュメント ノードになります。  
  
 パス式は、通常、ステップで構成されます。 たとえば、絶対パス式は、`/child::ProductDescription/child::Summary`スラッシュ記号で区切られた 2 つのステップを含みます。  
  
-   最初の手順では、ドキュメント\<ルートの要素ノードの子> ProductDescription を取得します。  
  
-   2 番目の手順では\<、取得した\<ProductDescription>要素ノードごとに、概要>要素ノードの子ノードを取得します。  
  
 パス式のステップは、軸ステップまたは一般的なステップです。  
  
## <a name="axis-step"></a>軸ステップ  
 パス式の軸ステップは、次の部分で構成されます。  
  
 [軸](../xquery/path-expressions-specifying-axis.md)  
 移動方向を定義します。 コンテキスト ノードから始まり、軸で指定された方向に到達可能なノードに移動するパス式の軸ステップ。  
  
 [ノード テスト](../xquery/path-expressions-specifying-node-test.md)  
 選択するノードの型またはノード名を指定します。  
  
 0 個以上の省略可能な述部  
 一部を選択して他のノードを破棄して、ノードをフィルター処理します。  
  
 次の例では、パス式で**軸ステップ**を使用します。  
  
-   絶対パス式は、1`/child::ProductDescription`つのステップのみを含みます。 これは、軸 (`child`) とノード テスト (`ProductDescription`) を指定しています。  
  
-   相対パス式 `child::ProductDescription/child::Features` には、1 つのスラッシュ記号で区切られた 2 つのステップがあります。 どちらの手順でも子軸を指定します。 製品説明と機能はノード テストです。  
  
-   相対パス式は、`child::root/child::Location[attribute::LocationID=10]`スラッシュ記号で区切られた 2 つのステップを含みます。 最初のステップでは、軸`child`( ) とノード`root`テスト ( ) を指定します。 2 番目のステップは、軸ステップの 3 種類のコンポーネントをすべて指定しています。つまり、軸 (child)、ノード テスト (`Location`)、および述語 (`[attribute::LocationID=10]`) です。  
  
 軸ステップのコンポーネントの詳細については、「[パス式ステップでの軸の指定](../xquery/path-expressions-specifying-axis.md)」、[パス式ステップでのノード・テストの指定](../xquery/path-expressions-specifying-node-test.md)、および[パス式ステップでの述部の指定 を参照](../xquery/path-expressions-specifying-predicates.md)してください。  
  
## <a name="general-step"></a>一般的なステップ  
 汎用ステップは、評価結果がノードのシーケンスになる必要のある式です。  
  
 SQL Server の XQuery 実装では、パス式の最初の手順として一般的な手順がサポートされています。 一般的な手順を使用するパス式の例を次に示します。  
  
```  
(/a, /b)/c  
id(/a/b)  
```  
  
 id 関数の詳細については、「 [id 関数 &#40;XQuery&#41;](../xquery/functions-on-sequences-id.md)」を参照してください。  
  
## <a name="in-this-section"></a>このセクションの内容  
 [パス式のステップでの軸の指定](../xquery/path-expressions-specifying-axis.md)  
 パス式の軸ステップの操作について説明します。  
  
 [パス式ステップでのノード・テストの指定](../xquery/path-expressions-specifying-node-test.md)  
 パス式でのノード テストの操作について説明します。  
  
 [パス式ステップで述部を指定する](../xquery/path-expressions-specifying-predicates.md)  
 パス式で述語を操作する方法について説明します。  
  
 [パス式での省略構文の使用](../xquery/path-expressions-using-abbreviated-syntax.md)  
 パス式での省略構文の使い方について説明します。  
  
  

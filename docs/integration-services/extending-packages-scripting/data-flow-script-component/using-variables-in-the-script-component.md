---
title: "スクリプト コンポーネントで変数の使用 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/06/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
helpviewer_keywords:
- Script component [Integration Services], using variables
ms.assetid: 92d1881a-1ef1-43ae-b1ca-48d0536bdbc2
caps.latest.revision: 13
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: 1419847dd47435cef775a2c55c0578ff4406cddc
ms.openlocfilehash: bac1e6d96e872be0355282c3e12fc81054ca41cd
ms.contentlocale: ja-jp
ms.lasthandoff: 08/03/2017

---
# <a name="using-variables-in-the-script-component"></a>スクリプト コンポーネントでの変数の使用
  変数には、パッケージとそのコンテナー、タスク、およびイベント ハンドラーが実行時に使用できる値が格納されます。 詳細については、「[Integration Services (SSIS) の変数](../../../integration-services/integration-services-ssis-variables.md)」を参照してください。  
  
 既存の変数を使用できる、読み取り専用か読み取り/書き込みアクセス、カスタム スクリプトで変数のコンマ区切りのリストを入力して、 **ReadOnlyVariables**と**ReadWriteVariables**フィールド、**スクリプト**のページ、**スクリプト変換エディター**です。 変数名の大文字と小文字は区別されることに注意してください。 使用して、**値**プロパティを個別に変数を読み書きします。 スクリプトが実行時に変数を処理すると、スクリプト コンポーネントは状況に応じて自動的に必要なロックを処理します。  
  
> [!IMPORTANT]  
>  コレクション**ReadWriteVariables**はのみで使用できます、 **PostExecute**してパフォーマンスを最大化し、ロックによる競合のリスクを最小限に抑える方法です。 したがって、データ行を処理するたびにパッケージ変数の値を直接増やすことはできません。 代わりに、ローカル変数の値をインクリメントし、内のローカル変数の値にパッケージ変数の値を設定、 **PostExecute**メソッドのすべてのデータの処理が完了します。 また、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> プロパティを使用してこの制限を回避できます。この方法については、このトピックの後半で説明します。 ただし、各行が処理されているときにパッケージ変数に直接書き込みを行うと、パフォーマンスに悪影響を与え、ロックによる競合のリスクが増えます。  
  
 詳細については、**スクリプト**のページ、**スクリプト変換エディター**を参照してください[スクリプト コンポーネント エディターで、スクリプト コンポーネントを構成する](../../../integration-services/extending-packages-scripting/data-flow-script-component/configuring-the-script-component-in-the-script-component-editor.md)と[スクリプト変換エディター & #40 です。[スクリプト] ページ &#41;](../../../integration-services/data-flow/transformations/script-transformation-editor-script-page.md).  
  
 スクリプト コンポーネントを作成、**変数**コレクション クラスに、 **ComponentWrapper**プロパティが、変数自体と同じ名前を事前に構成された各変数の値の厳密に型指定されたアクセサー プロパティを使用してプロジェクト項目です。 このコレクションは、によって公開される、**変数**のプロパティ、 **ScriptMain**クラスです。 アクセサー プロパティにより、変数の値が読み取り専用か読み取り/書き込み用かが決まります。 たとえば、名前付き整数の変数を追加している場合`MyIntegerVariable`を**ReadOnlyVariables**一覧で、値を取得できます、スクリプトで次のコードを使用しています。  
  
 `Dim myIntegerVariableValue As Integer = Me.Variables.MyIntegerVariable`  
  
 スクリプト コンポーネントで変数を扱うには、`Me.VariableDispenser` を呼び出してアクセスする <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> プロパティを使用することもできます。 この場合には、変数の型指定された名前付きのアクセサー プロパティを使用せずに、直接的に変数にアクセスします。 <xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> を使用する場合は、コード内で、ロック セマンティクスと、変数値のデータ型のキャストの両方を処理する必要があります。 デザイン時には使用できないが、実行時にプログラムによって生成される変数を扱う必要がある場合は、名前付きの型指定されたアクセサー プロパティではなく、<xref:Microsoft.SqlServer.Dts.Pipeline.ScriptComponent.VariableDispenser%2A> プロパティを使用する必要があります。  
  
## <a name="see-also"></a>参照  
 [Integration Services & #40 です。SSIS &#41;変数](../../../integration-services/integration-services-ssis-variables.md)   
 [パッケージの変数を使用します。](http://msdn.microsoft.com/library/7742e92d-46c5-4cc4-b9a3-45b688ddb787)  
  
  

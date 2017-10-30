---
title: "同期および非同期変換を理解する |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/17/2017
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
- transformations [Integration Services], synchronous and asynchronous
- asynchronous transformations [Integration Services]
- data flow components [Integration Services], synchronous and asynchronous
- synchronous transformations [Integration Services]
ms.assetid: 0bc2bda5-3f8a-49c2-aaf1-01dbe4c3ebba
caps.latest.revision: 17
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.workload: On Demand
ms.translationtype: MT
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: 9cc38505042dadb1b057a737279be82bb7923432
ms.contentlocale: ja-jp
ms.lasthandoff: 09/26/2017

---
# <a name="understanding-synchronous-and-asynchronous-transformations"></a>同期および非同期変換について
  [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] の同期変換と非同期変換の相違点を理解するには、まず同期変換を理解するのが最も簡単な方法です。 同期変換がニーズに合わない場合は、デザインに非同期変換が必要になることがあります。  
  
## <a name="synchronous-transformations"></a>同期変換  
 同期変換では、受信した行が処理され、一度に 1 行ずつデータ フローに渡されます。 出力は入力と同期しています。つまり、出力は入力と同時に発生します。 したがって、特定の行を処理するために、変換でデータ セット内の他の行の情報が必要になることはありません。 実際の実装では、行はコンポーネント間で渡されるときにバッファーにグループ化されますが、これらのバッファーはユーザーに対して透過的であるため、各行が個別に処理されると見なすことができます。  
  
 同期変換の例としては、データ変換の変換があります。 受信した各行について、指定した列の値を変換し、その過程で行を送信します。 不連続の各変換操作は、データ セット内の他のすべての行とは無関係です。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]コンポーネントの入力の ID を検索してに割り当てることによって、同期変換を指定するスクリプトとプログラミングで、 **SynchronousInputID**コンポーネントの出力のプロパティです。 これにより、入力内の各行を処理し、各行を指定された出力に自動的に送信するように、データ フロー エンジンに指示します。 各行を各出力に送信する場合、データを出力するための追加のコードを記述する必要はありません。 使用する場合、 **ExclusionGroup**プロパティを呼び出す必要があります、条件分割変換で、行が 1 つまたは別の出力グループに移動する必要がありますのみことを指定する、 **DirectRow**メソッドを選択するには行ごとに適切な変換先です。 エラー出力がある場合は、ときに呼び出す必要があります**DirectErrorRow**問題のある行を既定の出力ではなくエラー出力に送信します。  
  
## <a name="asynchronous-transformations"></a>非同期変換  
 各行を他のすべての行と無関係に処理できない場合、デザインに非同期変換が必要になることがあります。 つまり、各行を処理するときにデータ フローに各行を渡すことはできませんが、データを非同期で、つまり入力とは異なるタイミングで出力する必要がある場合です。 たとえば、次のシナリオでは非同期変換が必要です。  
  
-   コンポーネントが、処理を実行する前にデータの複数のバッファーを取得する必要がある場合。 たとえば、並べ替え変換です。この変換では、コンポーネントは 1 つの操作ですべての行を処理する必要があります。  
  
-   コンポーネントが、複数の入力の行を結合する必要がある場合。 たとえば、マージ変換です。この変換では、コンポーネントは各入力の複数の行を調べてから、並べ替えた順序でマージする必要があります。  
  
-   入力行と出力行の間に 1 対 1 の対応がない場合。 たとえば、集計変換です。この変換では、コンポーネントは出力に行を追加し、計算された集計値を保持する必要があります。  
  
 [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] 0 の値を割り当てることによって、非同期変換を指定するスクリプトとプログラミングで、 **SynchronousInputID**コンポーネントの出力のプロパティです。 のインスタンスにアクセスするたびに SQL Server ログインを指定する必要はありません。 これにより、出力に各行を自動的に送信しないようにデータ フロー エンジンに指示します。 次に、非同期変換の出力用に作成される新しい出力バッファーに各行を追加することによって、各行を適切な出力に明示的に送信するためのコードを記述する必要があります。  
  
> [!NOTE]  
>  変換元コンポーネントはデータ ソースから読み取った各行を出力バッファーに明示的に追加する必要もあるため、変換元では変換を非同期出力のように表示します。  
  
 各入力行を出力に明示的にコピーすることによって、同期変換をエミュレートする非同期変換を作成することもできます。 この方法では、列の名前を変更したり、データ タイプやフォーマットを変換したりできます。 ただし、この方法を使用するとパフォーマンスは低下します。 Copy Column や Data Conversion などの組み込みの Integration Services コンポーネントを使用することによって、より高いパフォーマンスで同じ結果を得ることができます。  
  
## <a name="see-also"></a>参照  
 [スクリプト コンポーネントによる同期変換の作成](../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-a-synchronous-transformation-with-the-script-component.md)   
 [スクリプト コンポーネントによる非同期変換の作成](../integration-services/extending-packages-scripting-data-flow-script-component-types/creating-an-asynchronous-transformation-with-the-script-component.md)   
 [同期出力型のカスタム変換コンポーネントの開発](../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-synchronous-outputs.md)   
 [非同期出力型のカスタム変換コンポーネントの開発](../integration-services/extending-packages-custom-objects-data-flow-types/developing-a-custom-transformation-component-with-asynchronous-outputs.md)  
  
  


---
title: バッチ操作 (XMLA) の実行 |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multiple projects
- XML for Analysis, batches
- parallel batch execution [XMLA]
- transactional batches
- serial batch execution [XMLA]
- XMLA, batches
- batches [XML for Analysis]
- nontransactional batches
ms.assetid: 731c70e5-ed51-46de-bb69-cbf5aea18dda
caps.latest.revision: 12
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: 7f164ca12c1de105bcd73f9b371ff4bfe2e00182
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36071989"
---
# <a name="performing-batch-operations-xmla"></a>バッチ操作の実行 (XMLA)
  使用することができます、[バッチ](../xmla/xml-elements-commands/batch-element-xmla.md)XML for Analysis (XMLA) を単一の XMLA を使用して複数の XMLA コマンドを実行するコマンド[Execute](../xmla/xml-elements-methods-execute.md)メソッドです。 `Batch` コマンドに含まれる複数のコマンドは、単一のトランザクションとして実行することも、あるいはコマンドごとに別個のトランザクションとして直列または並列で実行することもできます。 アウトオブ ライン バインドおよびその他のプロパティを指定することも、`Batch`の複数の処理コマンド[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト。  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>トランザクションおよび非トランザクション バッチ コマンドの実行  
 `Batch` コマンドは、コマンドを以下の 2 つのいずれかの方法で実行します。  
  
 **トランザクション**  
 場合、`Transaction`の属性、`Batch`コマンドが設定されているを true に、`Batch`コマンドのコマンドを実行に含まれるコマンドはすべて、`Batch`コマンドを単一のトランザクションで —、*トランザクション*バッチ。  
  
 トランザクション バッチでいずれかのコマンドが失敗した場合は[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のいずれかのコマンドはロールバック、`Batch`失敗したコマンドの前に実行されたコマンドを`Batch`コマンドを直ちに終了します。 `Batch` コマンド内でまだ実行されていないコマンドはいずれも実行されません。 `Batch` コマンドが終了した後、`Batch` コマンドは失敗したコマンドについて発生したすべてのエラーを報告します。  
  
 **非トランザクション**  
 場合、`Transaction`属性が false に設定されている、`Batch`コマンドに含まれる各コマンドを実行、`Batch`コマンドを個別のトランザクションで —、*非トランザクション*バッチ。 非トランザクション バッチ内のいずれかのコマンドが失敗した場合、`Batch` コマンドは、失敗したコマンドの後にあるコマンドの実行を続行します。 `Batch` コマンドが、`Batch` コマンドに含まれるすべてのコマンドの実行を試みた後、`Batch` コマンドは発生したすべてのエラーを報告します。  
  
 `Batch` コマンドに含まれるコマンドが返す結果はすべて、それらのコマンドが `Batch` コマンド内に含まれている順序と同じ順序で返されます。 `Batch` コマンドによって返される結果は、`Batch` コマンドがトランザクション バッチまたは非トランザクション バッチのいずれであるかによって異なります。  
  
> [!NOTE]  
>  場合、`Batch`コマンドにはなどの出力を返さないコマンドが含まれています、[ロック](../xmla/xml-elements-commands/lock-element-xmla.md)コマンド、およびコマンドが正常に実行される、`Batch`コマンドは、空白を返します[ルート](../xmla/xml-elements-properties/root-element-xmla.md)要素要素内部の結果。 空の `root` 要素があることにより、`Batch` コマンドに含まれるそれぞれのコマンドが、そのコマンドの結果の適切な `root` 要素と確実に対応します。  
  
### <a name="returning-results-from-transactional-batch-results"></a>トランザクション バッチの結果から結果を返す処理  
 トランザクション バッチ内で実行されたコマンドの結果は、`Batch` コマンド全体が完了するまで返されません。 それぞれのコマンドが実行された後に結果が返されないのは、トランザクション バッチ内のいずれかのコマンドが失敗すれば、`Batch` コマンド全体、および含まれるすべてのコマンドがロールバックされるためです。 すべてのコマンドが起動し、正常に実行する場合、[返す](../xmla/xml-elements-properties/return-element-xmla.md)の要素、 [ExecuteResponse](../xmla/xml-elements-objects-executeresponse.md)によって返される要素、`Execute`のメソッド、`Batch`コマンドを 1 つ[結果](../xmla/xml-elements-properties/results-element-xmla.md)要素は、さらに 1 つを含む`root`要素に含まれる正常に実行コマンドごとに、`Batch`コマンド。 `Batch` コマンド内のいずれかのコマンドが起動できない場合、または完了に失敗した場合、`Execute` メソッドは、失敗したコマンドのエラーを含む SOAP エラーを `Batch` コマンドについて返します。  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>非トランザクション バッチの結果から結果を返す処理  
 非トランザクション バッチ内のコマンドによる結果は、それらのコマンドが `Batch` コマンド内に含まれている順序で、各コマンドごとに返されます。 `Batch` コマンド内のいずれのコマンドも正常に起動できなかった場合、`Execute` メソッドは、その `Batch` コマンドについてのエラーを含む SOAP エラーを返します。 少なくとも 1 つのコマンドが正常に起動された場合、その `return` コマンドに対する `ExecuteResponse` メソッドによって返される `Execute` 要素の `Batch` 要素には、1 つの `results` 要素が含まれます。この要素には、`root` コマンドに含まれる各コマンドに対して 1 つの `Batch` 要素が含まれています。 非トランザクション バッチ内の 1 つまたは複数のコマンドが開始することはできませんまたは完了するには失敗した場合、`root`その失敗したコマンドの要素が含まれています、[エラー](../xmla/xml-elements-properties/error-element-xmla.md)エラーを説明する要素。  
  
> [!NOTE]  
>  非トランザクション バッチ内の少なくとも 1 つのコマンドが起動できれば、その非トランザクション バッチに含まれるすべてのコマンドが `Batch` コマンドの結果にエラーを返した場合であっても、その非トランザクション バッチは正常に実行されたものと見なされます。  
  
## <a name="using-serial-and-parallel-execution"></a>直列および並列実行の使用  
 `Batch` コマンドでは、含まれるコマンドを直列または並列で実行することができます。 コマンドが直列に実行される場合、`Batch` コマンド内に含まれる次のコマンドは、`Batch` コマンド内で現在実行中のコマンドが完了するまで起動できません。 コマンドが並列で実行される場合、`Batch` によって複数のコマンドを同時に実行することができます。  
  
 コマンドを並列に実行、並列に実行するコマンドを追加する、[並列](../xmla/xml-elements-properties/parallel-element-xmla.md)のプロパティ、`Batch`コマンド。 現在、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、連続のみ実行できる[プロセス](../xmla/xml-elements-commands/process-element-xmla.md)コマンドを並列でします。 その他の任意の XMLA コマンドなど、[作成](../xmla/xml-elements-commands/create-element-xmla.md)または[Alter](../xmla/xml-elements-commands/alter-element-xmla.md)に含まれていて、`Parallel`プロパティが直列に実行されます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、`Process` プロパティに含まれるすべての `Parallel` コマンドの並列実行を試みますが、すべての `Process` コマンドが並列で実行されるとは限りません。 各 `Process` コマンドはインスタンスによって分析され、並列で実行できないとインスタンスが判断した `Process` コマンドは直列に実行されます。  
  
> [!NOTE]  
>  コマンドを並行で実行する場合は、`Transaction` コマンドの `Batch` 属性を true に設定する必要があります。これは、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] によってサポートされるアクティブなトランザクションは接続ごとに 1 つだけであるのに対し、非トランザクション バッチは各コマンドを個別のトランザクションで実行するためです。 非トランザクション バッチに `Parallel` プロパティを含めると、エラーが発生します。  
  
### <a name="limiting-parallel-execution"></a>並列実行の制限  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、インスタンスが実行されているコンピューターの制限範囲で、可能な限り多くの `Process` コマンドを並列で実行しようとします。 同時に実行する `Process` コマンドの数は、`maxParallel` プロパティの `Parallel` 属性を、並列で実行できる `Process` コマンドの最大数を示す値に設定することにより制限できます。  
  
 たとえば、`Parallel` プロパティに以下の順序でコマンドが含まれているとします。  
  
1.  `Create`  
  
2.  `Process`  
  
3.  `Alter`  
  
4.  `Process`  
  
5.  `Process`  
  
6.  `Process`  
  
7.  `Delete`  
  
8.  `Process`  
  
9. `Process`  
  
 この `maxParalle` プロパティの `Parallel` 属性は 2 に設定されています。 そのため、インスタンスは上のコマンドの一覧を以下の説明のとおりに実行します。  
  
-   コマンド 1 は直列に実行されます。コマンド 1 は `Create` コマンドであり、並列で実行できるのは `Process` コマンドだけであるためです。  
  
-   コマンド 1 が完了した後、2 のコマンドは直列に実行されます。  
  
-   コマンド 2 が完了した後、3 のコマンドは直列に実行されます。  
  
-   コマンド 4 と 5 は、3 のコマンドが完了した後、並列で実行します。 コマンド 6 も `Process` コマンドですが、`maxParallel` プロパティが 2 に設定されているため、コマンド 6 がコマンド 4 と 5 と共に並行で実行されることはありません。  
  
-   コマンド 6 は、コマンド 4 とコマンド 5 の両方が完了した後に直列に実行されます。  
  
-   コマンド 7 はコマンド 6 の完了後に直列に実行されます。  
  
-   コマンド 8 と 9 はコマンド 7 の完了後に並列で実行されます。  
  
## <a name="using-the-batch-command-to-process-objects"></a>バッチ コマンドを使用したオブジェクトの処理  
 `Batch` コマンドには、複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理をサポートするために特に用意された、以下の省略可能なプロパティおよび属性が含まれています。  
  
-   `ProcessAffectedObjects` コマンドの `Batch` 属性は、指定したオブジェクトを処理する `Process` コマンドに含まれる `Batch` コマンドの結果、再処理が必要になったオブジェクトがある場合に、インスタンスがそれらのオブジェクトも処理するかどうかを示します。  
  
-   [バインド](../xmla/xml-elements-properties/bindings-element-xmla.md)プロパティには、すべてのによって使用される行外のバインディングのコレクションが含まれています、 `Process`  コマンドを`Batch`コマンド。  
  
-   [データソース](../xmla/xml-elements-properties/source-element-xmla.md)プロパティが使用するすべてのデータ ソースの行外のバインディングが含まれています、 `Process`  コマンドを`Batch`コマンド。  
  
-   [DataSourceView](../xmla/xml-elements-properties/datasourceview-element-xmla.md)プロパティがすべての設定を使ってデータ ソース ビューの行外のバインディングが含まれています、 `Process`  コマンドを`Batch`コマンド。  
  
-   [ErrorConfiguration](../xmla/xml-elements-properties/errorconfiguration-element-xmla.md)プロパティでは、方法を指定する、`Batch`コマンドがすべてで発生したエラーを処理`Process`に含まれるコマンド、`Batch`コマンド。  
  
    > [!IMPORTANT]  
    >  `Process` コマンドが `Bindings` コマンドに含まれている場合、その `DataSource` コマンドには `DataSourceView`、`ErrorConfiguration`、`Process`、および `Batch` プロパティを含めることができません。 `Process` コマンドにこれらのプロパティを含める必要がある場合、その `Batch` コマンドを含む `Process` の対応するプロパティに、必要な情報を指定してください。  
  
## <a name="see-also"></a>参照  
 [要素をバッチ&#40;XMLA&#41;](../xmla/xml-elements-commands/batch-element-xmla.md)   
 [要素を処理&#40;XMLA&#41;](../xmla/xml-elements-commands/process-element-xmla.md)   
 [多次元モデル オブジェクトの処理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  
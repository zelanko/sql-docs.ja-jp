---
title: バッチ操作の実行 (XMLA) |Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
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
author: minewiskan
ms.author: owend
ms.openlocfilehash: 69899077cf534482879accbf10640f6295e3866a
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/09/2020
ms.locfileid: "84544924"
---
# <a name="performing-batch-operations-xmla"></a>バッチ操作の実行 (XMLA)
  XML for Analysis (XMLA) の[Batch](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)コマンドを使用して、1つの xmla [Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッドを使用して複数の xmla コマンドを実行できます。 `Batch` コマンドに含まれる複数のコマンドは、単一のトランザクションとして実行することも、あるいはコマンドごとに別個のトランザクションとして直列または並列で実行することもできます。 また、不一致バインドや、複数のオブジェクトを処理するためのその他のプロパティをコマンドで指定することもでき `Batch` [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ます。  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>トランザクションおよび非トランザクション バッチ コマンドの実行  
 `Batch` コマンドは、コマンドを以下の 2 つのいずれかの方法で実行します。  
  
 **トランザクション**  
 `Transaction`コマンドの属性が true に設定されている場合、コマンドは、コマンド `Batch` `Batch` に含まれるすべてのコマンドを `Batch` 1 つのトランザクション (*トランザクション*バッチ) で実行します。  
  
 トランザクションバッチ内のいずれかのコマンドが失敗した場合、は、失敗したコマンドの前に実行されたコマンド [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] 内のすべてのコマンドをロールバックし、 `Batch` `Batch` コマンドはすぐに終了します。 `Batch` コマンド内でまだ実行されていないコマンドはいずれも実行されません。 `Batch` コマンドが終了した後、`Batch` コマンドは失敗したコマンドについて発生したすべてのエラーを報告します。  
  
 **非トランザクション**  
 `Transaction`属性が false に設定されている場合、コマンドはコマンド `Batch` に含まれる各コマンドを `Batch` 別のトランザクション (*非トランザクション*バッチ) で実行します。 非トランザクション バッチ内のいずれかのコマンドが失敗した場合、`Batch` コマンドは、失敗したコマンドの後にあるコマンドの実行を続行します。 `Batch` コマンドが、`Batch` コマンドに含まれるすべてのコマンドの実行を試みた後、`Batch` コマンドは発生したすべてのエラーを報告します。  
  
 `Batch` コマンドに含まれるコマンドが返す結果はすべて、それらのコマンドが `Batch` コマンド内に含まれている順序と同じ順序で返されます。 `Batch` コマンドによって返される結果は、`Batch` コマンドがトランザクション バッチまたは非トランザクション バッチのいずれであるかによって異なります。  
  
> [!NOTE]  
>  コマンドに `Batch` [Lock](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)コマンドなどの出力を返さないコマンドが含まれており、そのコマンドが正常に実行された場合、 `Batch` コマンドは結果要素内の空の[ルート](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)要素を返します。 空の `root` 要素があることにより、`Batch` コマンドに含まれるそれぞれのコマンドが、そのコマンドの結果の適切な `root` 要素と確実に対応します。  
  
### <a name="returning-results-from-transactional-batch-results"></a>トランザクション バッチの結果から結果を返す処理  
 トランザクション バッチ内で実行されたコマンドの結果は、`Batch` コマンド全体が完了するまで返されません。 それぞれのコマンドが実行された後に結果が返されないのは、トランザクション バッチ内のいずれかのコマンドが失敗すれば、`Batch` コマンド全体、および含まれるすべてのコマンドがロールバックされるためです。 すべてのコマンドが開始され、正常に実行されると、コマンドのメソッドによって返される[ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse)要素の[return](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla)要素には `Execute` `Batch` 1 つの[結果](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla)要素が含まれます。この要素には `root` 、コマンドに含まれる正常に実行されたコマンドごとに1つの要素が含まれ `Batch` ます。 `Batch` コマンド内のいずれかのコマンドが起動できない場合、または完了に失敗した場合、`Execute` メソッドは、失敗したコマンドのエラーを含む SOAP エラーを `Batch` コマンドについて返します。  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>非トランザクション バッチの結果から結果を返す処理  
 非トランザクション バッチ内のコマンドによる結果は、それらのコマンドが `Batch` コマンド内に含まれている順序で、各コマンドごとに返されます。 `Batch` コマンド内のいずれのコマンドも正常に起動できなかった場合、`Execute` メソッドは、その `Batch` コマンドについてのエラーを含む SOAP エラーを返します。 少なくとも 1 つのコマンドが正常に起動された場合、その `return` コマンドに対する `ExecuteResponse` メソッドによって返される `Execute` 要素の `Batch` 要素には、1 つの `results` 要素が含まれます。この要素には、`root` コマンドに含まれる各コマンドに対して 1 つの `Batch` 要素が含まれています。 非トランザクションバッチ内の1つ以上のコマンドを開始できない場合、または完了できなかった場合、 `root` その失敗したコマンドの要素にはエラーを説明する[error](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)要素が含まれます。  
  
> [!NOTE]  
>  非トランザクション バッチ内の少なくとも 1 つのコマンドが起動できれば、その非トランザクション バッチに含まれるすべてのコマンドが `Batch` コマンドの結果にエラーを返した場合であっても、その非トランザクション バッチは正常に実行されたものと見なされます。  
  
## <a name="using-serial-and-parallel-execution"></a>直列および並列実行の使用  
 `Batch` コマンドでは、含まれるコマンドを直列または並列で実行することができます。 コマンドが直列に実行される場合、`Batch` コマンド内に含まれる次のコマンドは、`Batch` コマンド内で現在実行中のコマンドが完了するまで起動できません。 コマンドが並列で実行される場合、`Batch` によって複数のコマンドを同時に実行することができます。  
  
 コマンドを並列実行するには、コマンドの[parallel](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla)プロパティに並列で実行されるコマンドを追加し `Batch` ます。 現在、で [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、連続したシーケンシャル[プロセス](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンドのみ並列実行できます。 [Create](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)や[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)など、プロパティに含まれるその他の XMLA コマンド `Parallel` は、順次実行されます。  
  
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
  
-   コマンド1が完了すると、コマンド2は順次実行されます。  
  
-   コマンド3は、コマンド2が完了した後に順次実行されます。  
  
-   コマンド3が完了した後、コマンド4および5が並列で実行されます。 コマンド 6 も `Process` コマンドですが、`maxParallel` プロパティが 2 に設定されているため、コマンド 6 がコマンド 4 と 5 と共に並行で実行されることはありません。  
  
-   コマンド 6 は、コマンド 4 とコマンド 5 の両方が完了した後に直列に実行されます。  
  
-   コマンド 7 はコマンド 6 の完了後に直列に実行されます。  
  
-   コマンド 8 と 9 はコマンド 7 の完了後に並列で実行されます。  
  
## <a name="using-the-batch-command-to-process-objects"></a>バッチ コマンドを使用したオブジェクトの処理  
 `Batch` コマンドには、複数の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトの処理をサポートするために特に用意された、以下の省略可能なプロパティおよび属性が含まれています。  
  
-   `ProcessAffectedObjects` コマンドの `Batch` 属性は、指定したオブジェクトを処理する `Process` コマンドに含まれる `Batch` コマンドの結果、再処理が必要になったオブジェクトがある場合に、インスタンスがそれらのオブジェクトも処理するかどうかを示します。  
  
-   [Bindings](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)プロパティには、コマンド内のすべてのコマンドで使用される不一致バインドのコレクションが含まれてい `Process` `Batch` ます。  
  
-   [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/source-element-xmla)プロパティには、コマンド内のすべてのコマンドで使用されるデータソースの不一致バインドが含まれてい `Process` `Batch` ます。  
  
-   [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)プロパティには、コマンド内のすべてのコマンドで使用されるデータソースビューの不一致バインドが含まれてい `Process` `Batch` ます。  
  
-   [Errorconfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)プロパティは、コマンド `Batch` に含まれるすべてのコマンドで発生したエラーをコマンドが処理する方法を指定し `Process` `Batch` ます。  
  
    > [!IMPORTANT]  
    >  `Process` コマンドが `Bindings` コマンドに含まれている場合、その `DataSource` コマンドには `DataSourceView`、`ErrorConfiguration`、`Process`、および `Batch` プロパティを含めることができません。 `Process` コマンドにこれらのプロパティを含める必要がある場合、その `Batch` コマンドを含む `Process` の対応するプロパティに、必要な情報を指定してください。  
  
## <a name="see-also"></a>参照  
 [XMLA&#41;&#40;のバッチ要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [XMLA&#41;&#40;プロセス要素](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [多次元モデルオブジェクトの処理](../multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Analysis Services での XMLA による開発](developing-with-xmla-in-analysis-services.md)  
  
  

---
title: バッチ操作 (XMLA) の実行 |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: f34454f292e7efc92c960930b6a9218edae6a70f
ms.sourcegitcommit: 7fe14c61083684dc576d88377e32e2fc315b7107
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/26/2018
ms.locfileid: "50148317"
---
# <a name="performing-batch-operations-xmla"></a>バッチ操作の実行 (XMLA)
  使用することができます、[バッチ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)XML for Analysis (XMLA) 単一の XMLA を使用して複数の XMLA コマンドを実行するコマンド[Execute](https://docs.microsoft.com/bi-reference/xmla/xml-elements-methods-execute)メソッド。 含まれる複数のコマンドを実行することができます、**バッチ**単一のトランザクションとしてまたはコマンドごとに個別のトランザクションで、直列または並列コマンド。 アウトオブ ライン バインドおよびその他のプロパティを指定することも、**バッチ**の複数の処理コマンド[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト。  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>トランザクションおよび非トランザクション バッチ コマンドの実行  
 **バッチ**コマンドは、2 つの方法のいずれかのコマンドを実行します。  
  
 **トランザクション**  
 場合、**トランザクション**の属性、**バッチ**コマンドの設定を true に、**バッチ**コマンド実行コマンドのすべてのコマンドに含まれる、**バッチ**コマンド 1 つのトランザクションを:、*トランザクション*バッチ。  
  
 トランザクション バッチで任意のコマンドが失敗した場合[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のいずれかのコマンドはロールバック、**バッチ**失敗したコマンドの前に実行されたコマンドに対して、**バッチ**コマンドを直ちに終了します。 任意のコマンドで、**バッチ**まだ実行されていないコマンドは実行されません。 後に、**バッチ**コマンドが終了、**バッチ**コマンドが失敗したコマンドで発生したエラーを報告します。  
  
 **非トランザクション**  
 場合、**トランザクション**属性が false に設定、**バッチ**コマンドに含まれる各コマンドを実行、**バッチ**別個のトランザクションでコマンドなど、 *非トランザクション*バッチ。 非トランザクション バッチで任意のコマンドが失敗した場合、**バッチ**コマンドが失敗したコマンドの後のコマンドを実行し続けます。 後に、**バッチ**コマンドが、すべてのコマンドを実行しようとしています。 を、**バッチ**コマンドが含まれています、**バッチ**コマンドが発生したエラーを報告します。  
  
 含まれるコマンドによって返されるすべての結果、**バッチ**でコマンドが格納されて、同じ順序で返されます、**バッチ**コマンド。 によって返される結果を**バッチ**コマンドが異なるかどうかに基づいて、**バッチ**コマンドがトランザクションか非トランザクションです。  
  
> [!NOTE]  
>  場合、**バッチ**コマンドにはなどの出力を返さないコマンドが含まれています、[ロック](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/lock-element-xmla)コマンドと、コマンドが正常に実行を**バッチ**コマンドは、空白を返します[ルート](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/root-element-xmla)結果要素内の要素。 空の**ルート**要素により各コマンドに含まれている、**バッチ**コマンドは、適切なと照合できる**ルート**そのコマンドの結果の要素。  
  
### <a name="returning-results-from-transactional-batch-results"></a>トランザクション バッチの結果から結果を返す処理  
 トランザクション バッチ内で実行されたコマンドの結果は、全体まで返されません**バッチ**コマンドが完了します。 いずれかのコマンドが失敗したトランザクション バッチ内でが全体を引き起こすため、各コマンドの実行後、結果は返されません**バッチ**コマンドおよびロールバックされるすべての包含コマンド。 すべてのコマンドを開始して正常に実行すると、[返す](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/return-element-xmla)の要素、 [ExecuteResponse](https://docs.microsoft.com/bi-reference/xmla/xml-elements-objects-executeresponse)要素によって返される、 **Execute**のメソッド、**バッチ**コマンドでは、1 つ含まれる[結果](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/results-element-xmla)要素、1 つを格納する**ルート**正常に実行コマンド内の各要素、**バッチ**コマンド。 いずれかのコマンドの場合、**バッチ**コマンドが起動できない場合、またはを完了できない、 **Execute**メソッドの SOAP エラーを返します、**バッチ**のエラーが含まれるコマンド、失敗したコマンド。  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>非トランザクション バッチの結果から結果を返す処理  
 内にコマンドが含まれている順序で非トランザクション バッチ内で実行されたコマンドの結果が返されます、**バッチ**コマンドと各コマンドによって返されたときにします。 含まれていないコマンドの場合、**バッチ**コマンドが正常に開始することができます、 **Execute**メソッドのエラーを含む SOAP エラーを返します、**バッチ**コマンド。 少なくとも 1 つのコマンドが正常に開始する場合、**返す**の要素、 **ExecuteResponse**によって返される要素、 **Execute**のメソッド、**バッチ**コマンドでは、1 つ含まれる**結果**要素、1 つを格納する**ルート**コマンド内の各要素、**バッチ**コマンド. 非トランザクション バッチ内の 1 つまたは複数のコマンドが開始することはできませんまたは完了するには失敗した場合、**ルート**その失敗したコマンドの要素が含まれています、[エラー](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/error-element-xmla)エラーを説明する要素。  
  
> [!NOTE]  
>  非トランザクション バッチ内の少なくとも 1 つのコマンドを開始する限り、非トランザクション バッチと見なされますが正常に実行する非トランザクション バッチに含まれているすべてのコマンドの結果にエラーを返した場合であっても、**バッチ**コマンド。  
  
## <a name="using-serial-and-parallel-execution"></a>直列および並列実行の使用  
 使用することができます、**バッチ**含まれる実行コマンドを直列または並列でのコマンドします。 コマンドが直列に実行に、次のコマンドが含まれます。、**バッチ**コマンドが起動して、現在実行中のコマンドで、**バッチ**コマンドが完了します。 複数のコマンドをにより同時に実行できるコマンドが並列で実行時に、**バッチ**コマンド。  
  
 並行して実行するコマンドを追加するコマンドを並列で実行する、[並列](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/parallel-element-xmla)のプロパティ、**バッチ**コマンド。 現時点では、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]だけなは、シーケンシャルに実行できる[プロセス](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)コマンドを並列でします。 などの他の任意の XMLA コマンド[作成](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/create-element-xmla)または[Alter](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/alter-element-xmla)に含まれる、**並列**プロパティが連続して実行します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] すべてを実行しようとしています。**プロセス**に含まれるコマンド、**並列**を並列にプロパティができないことは保証に含まれるすべて**プロセス**コマンドを並列で実行できます。 インスタンスを分析して各**プロセス**コマンドと、インスタンスは、コマンドを並列で実行できないことを決定します。、**プロセス**コマンドが直列に実行します。  
  
> [!NOTE]  
>  コマンドが並列で実行する、**トランザクション**の属性、**バッチ**コマンドは、ためにを true に設定する必要があります[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]接続と非トランザクションごとの 1 つだけのアクティブなトランザクションをサポートしていますバッチは、別のトランザクションで各コマンドを実行します。 含める場合は、**並列**非トランザクション バッチでプロパティは、エラーが発生します。  
  
### <a name="limiting-parallel-execution"></a>並列実行の制限  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンス数を実行しようとする**プロセス**インスタンスが実行されているコンピューターの上限まで、可能な並列コマンド。 同時実行の数を制限する**プロセス**コマンドを設定して、 **maxParallel**の属性、**並列**プロパティを示す値を最大数**プロセス**コマンドを並列で実行できます。  
  
 たとえば、**並列**プロパティには記載されている順序で次のコマンドが含まれています。  
  
1.  **作成**  
  
2.  **[処理]**  
  
3.  **Alter**  
  
4.  **[処理]**  
  
5.  **[処理]**  
  
6.  **[処理]**  
  
7.  **削除**  
  
8.  **[処理]**  
  
9. **[処理]**  
  
 **MaxParalle**これの l 属性**並列**プロパティが 2 に設定します。 そのため、インスタンスは上のコマンドの一覧を以下の説明のとおりに実行します。  
  
-   コマンド 1 順番に実行されるため、コマンド 1 は、**作成**コマンドとのみ**プロセス**コマンドを並列で実行できます。  
  
-   コマンド 1 が完了した後、コマンド 2 は直列に実行されます。  
  
-   コマンド 2 が完了した後、コマンド 3 は直列に実行されます。  
  
-   3 のコマンドが完了した後、コマンド 4 と 5 は並列で実行します。 コマンド 6 も、**プロセス**コマンドのため、コマンド 6 がコマンド 4 と 5 を使用して並列で実行できません、 **maxParallel**プロパティが 2 に設定します。  
  
-   コマンド 6 は、コマンド 4 とコマンド 5 の両方が完了した後に直列に実行されます。  
  
-   コマンド 7 はコマンド 6 の完了後に直列に実行されます。  
  
-   コマンド 8 と 9 はコマンド 7 の完了後に並列で実行されます。  
  
## <a name="using-the-batch-command-to-process-objects"></a>バッチ コマンドを使用したオブジェクトの処理  
 **バッチ**コマンドには、いくつかの省略可能なプロパティとサポートするために具体的には含まれている属性が含まれます。 複数の処理[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。  
  
-   **ProcessAffectedObjects**の属性、**バッチ**コマンドでは、インスタンスがの結果として再処理を必要とする任意のオブジェクトを処理する必要がありますもかどうかを示す、 **プロセス**コマンドに含まれる、**バッチ**コマンド、指定したオブジェクトを処理します。  
  
-   [バインド](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/bindings-element-xmla)プロパティにはにより、すべての使用の不一致バインドのコレクションが含まれています、**プロセス**コマンド、**バッチ**コマンド。  
  
-   [DataSource](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasource-element-xmla)プロパティには、すべてのによって使用されるデータ ソースのアウトオブ ライン バインドにはが含まれています、**プロセス**コマンド、**バッチ**コマンド。  
  
-   [DataSourceView](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/datasourceview-element-xmla)プロパティにはすべてで使用されるデータ ソース ビューのアウトオブ ライン バインドが含まれています、**プロセス**コマンド、**バッチ**コマンド。  
  
-   [ErrorConfiguration](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/errorconfiguration-element-xmla)プロパティでは、方法を指定する、**バッチ**コマンドがすべてで発生したエラーを処理**プロセス**に含まれるコマンド**バッチ**コマンド。  
  
    > [!IMPORTANT]  
    >  A**プロセス**コマンドを含めることはできません、**バインド**、 **DataSource**、 **DataSourceView**、または**ErrorConfiguration**プロパティ場合、**プロセス**にコマンドが含まれている、**バッチ**コマンド。 これらのプロパティを指定する必要があります場合、**プロセス**コマンドで、対応するプロパティのために必要な情報を提供、**バッチ**コマンドが含まれている**プロセス**コマンド。  
  
## <a name="see-also"></a>参照  
 [要素をバッチ&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/batch-element-xmla)   
 [要素を処理&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/process-element-xmla)   
 [多次元モデルの処理 (Analysis Services)](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

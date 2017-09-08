---
title: "バッチ操作 (XMLA) の実行 |Microsoft ドキュメント"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- docset-sql-devref
ms.tgt_pltfrm: 
ms.topic: reference
applies_to:
- SQL Server 2016 Preview
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
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 3e2673091cfba456834da77049036591e4591891
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="performing-batch-operations-xmla"></a>バッチ操作の実行 (XMLA)
  使用することができます、[バッチ](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)XML for Analysis (XMLA) を単一の XMLA を使用して複数の XMLA コマンドを実行するコマンド[Execute](../../analysis-services/xmla/xml-elements-methods-execute.md)メソッドです。 含まれる複数のコマンドを実行することができます、**バッチ**コマンドを単一のトランザクションとしてまたはコマンドごとに個別のトランザクションで、直列または並列でします。 アウトオブ ライン バインドおよびその他のプロパティを指定することも、**バッチ**の複数の処理コマンド[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]オブジェクト。  
  
## <a name="running-transactional-and-nontransactional-batch-commands"></a>トランザクションおよび非トランザクション バッチ コマンドの実行  
 **バッチ**コマンドは、2 つの方法でコマンドを実行します。  
  
 **トランザクション**  
 場合、**トランザクション**の属性、**バッチ**コマンドの設定を true に、**バッチ**コマンドのコマンドを実行に含まれるコマンドはすべて、**バッチ**コマンドを単一のトランザクションで —、*トランザクション*バッチ。  
  
 トランザクション バッチでいずれかのコマンドが失敗した場合は[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]のいずれかのコマンドはロールバック、**バッチ**失敗したコマンドの前に実行されたコマンドを**バッチ**コマンドを直ちに終了します。 どのようなコマンドで、**バッチ**まだ実行されていないコマンドは実行されません。 後に、**バッチ**コマンドが終了、**バッチ**コマンドが失敗したコマンドで発生したエラーを報告します。  
  
 **非トランザクション**  
 場合、**トランザクション**属性が false に設定されている、**バッチ**コマンドに含まれる各コマンドを実行、**バッチ**コマンドを個別のトランザクションで —、 *非トランザクション*バッチ。 非トランザクション バッチでいずれかのコマンドが失敗した場合、**バッチ**コマンドが失敗したコマンドの後にコマンドを実行し続けます。 後に、**バッチ**コマンドが、すべてのコマンドを実行しようとしています。 を、**バッチ**がコマンドに含まれている、**バッチ**コマンドが発生したエラーを報告します。  
  
 含まれるコマンドによって返されるすべての結果、**バッチ**コマンドは、コマンドに含まれる同じ順序で返される、**バッチ**コマンド。 によって返される結果は**バッチ**かどうかに基づき、異なるコマンド、**バッチ**コマンドはトランザクションまたは非トランザクションです。  
  
> [!NOTE]  
>  場合、**バッチ**コマンドにはなどの出力を返さないコマンドが含まれています、[ロック](../../analysis-services/xmla/xml-elements-commands/lock-element-xmla.md)コマンド、およびコマンドが正常に実行される、**バッチ**コマンドは、空白を返します[ルート](../../analysis-services/xmla/xml-elements-properties/root-element-xmla.md)結果要素内の要素。 空の**ルート**要素により各コマンドに含まれている、**バッチ**コマンドは、適切なと一致するが**ルート**そのコマンドの結果の要素。  
  
### <a name="returning-results-from-transactional-batch-results"></a>トランザクション バッチの結果から結果を返す処理  
 全体まで、トランザクション バッチ内で実行されたコマンドの結果は返されません**バッチ**コマンドが完了します。 各コマンドを実行するため、いずれかのコマンドが失敗したトランザクション バッチ内では、全体で発生すると、結果は返されません**バッチ**コマンドおよびすべての含まれるコマンドをロールバックできます。 すべてのコマンドが起動し、正常に実行する場合、[返す](../../analysis-services/xmla/xml-elements-properties/return-element-xmla.md)の要素、 [ExecuteResponse](../../analysis-services/xmla/xml-elements-objects-executeresponse.md)要素によって返される、 **Execute**のメソッド、**バッチ**コマンドでは、1 つ含まれています[結果](../../analysis-services/xmla/xml-elements-properties/results-element-xmla.md)要素は、さらに 1 つを含む**ルート**要素に含まれる正常に実行コマンドごとに、**バッチ**コマンド。 いずれかのコマンドの場合、**バッチ**コマンドが起動できない、またはを完了できない、 **Execute**の SOAP エラーを返します、**バッチ**のエラーが含まれるコマンド、失敗したコマンド。  
  
### <a name="returning-results-from-nontransactional-batch-results"></a>非トランザクション バッチの結果から結果を返す処理  
 内で、コマンドが含まれている順序で非トランザクション バッチ内で実行されたコマンドの結果が返されます、**バッチ**コマンドと各コマンドによって返されます。 含まれるコマンドがない場合、**バッチ**コマンドが正常に開始することができます、 **Execute**のエラーを含む SOAP エラーを返します、**バッチ**コマンド。 少なくとも 1 つのコマンドは正常に開始されている場合、**返す**の要素、 **ExecuteResponse**要素によって返される、 **Execute**のメソッド、**バッチ**コマンドでは、1 つ含まれています**結果**要素は、さらに 1 つを含む**ルート**要素に含まれる各コマンドを**バッチ**コマンド. 非トランザクション バッチ内の 1 つまたは複数のコマンドが開始することはできませんまたは完了するには失敗した場合、**ルート**その失敗したコマンドの要素が含まれています、[エラー](../../analysis-services/xmla/xml-elements-properties/error-element-xmla.md)エラーを説明する要素。  
  
> [!NOTE]  
>  非トランザクション バッチ内に少なくとも 1 つのコマンドを開始する限り、非トランザクション バッチと見なされますが正常に実行するには、非トランザクション バッチに含まれているすべてのコマンドの結果にエラーが返されます場合でも、**バッチ**コマンド。  
  
## <a name="using-serial-and-parallel-execution"></a>直列および並列実行の使用  
 使用することができます、**バッチ**含まれる実行するコマンドを直列または並列でのコマンドします。 コマンドが直列に実行に、次のコマンドが含まれます。、**バッチ**コマンドが起動して、現在実行中のコマンドで、**バッチ**コマンドが完了します。 複数のコマンドをにより同時に実行できるコマンドは、並列で実行されて、ときに、**バッチ**コマンド。  
  
 コマンドを並列に実行、並列に実行するコマンドを追加する、[並列](../../analysis-services/xmla/xml-elements-properties/parallel-element-xmla.md)のプロパティ、**バッチ**コマンド。 現在、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]は、連続のみ実行できる[プロセス](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)コマンドを並列でします。 その他の任意の XMLA コマンドなど、[作成](../../analysis-services/xmla/xml-elements-commands/create-element-xmla.md)または[Alter](../../analysis-services/xmla/xml-elements-commands/alter-element-xmla.md)に含まれていて、**並列**プロパティが直列に実行されます。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]すべてを実行しようとしています。**プロセス**に含まれるコマンド、**並列**並列でプロパティがことはできませんが、保証を含まれているすべて**プロセス**コマンドを並列で実行することができます。 インスタンスを分析の各**プロセス**コマンドと、インスタンスは、コマンドを並列で実行できないことを決定する場合、**プロセス**コマンドが直列に実行します。  
  
> [!NOTE]  
>  コマンドが並列で実行する、**トランザクション**の属性、**バッチ**コマンドをためには、true に設定する必要があります[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]接続および非トランザクションごとの 1 つだけのアクティブなトランザクションをサポートしていますバッチは、別のトランザクションで各コマンドを実行します。 含める場合は、**並列**非トランザクション バッチでプロパティは、エラーが発生します。  
  
### <a name="limiting-parallel-execution"></a>並列実行の制限  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスだけを実行しようとしました。**プロセス**インスタンスが実行されているコンピューターの上限まで、可能な並列コマンド。 同時実行の数を制限する**プロセス**設定で、コマンド、 **maxParallel**の属性、**並列**プロパティを示す値を最大数**プロセス**コマンドを並列で実行することができます。  
  
 たとえば、**並列**プロパティには、記載されている順序で次のコマンドが含まれています。  
  
1.  **作成**  
  
2.  **[処理]**  
  
3.  **Alter**  
  
4.  **[処理]**  
  
5.  **[処理]**  
  
6.  **[処理]**  
  
7.  **Del**  
  
8.  **[処理]**  
  
9. **[処理]**  
  
 **MaxParalle**この l 属性**並列**プロパティが 2 に設定します。 そのため、インスタンスは上のコマンドの一覧を以下の説明のとおりに実行します。  
  
-   コマンド 1 はために、1 のコマンドが直列に実行されます、**作成**コマンドとのみ**プロセス**コマンドを並列で実行することができます。  
  
-   コマンド 1 が完了した後、2 のコマンドは直列に実行されます。  
  
-   コマンド 2 が完了した後、3 のコマンドは直列に実行されます。  
  
-   コマンド 4 と 5 は、3 のコマンドが完了した後、並列で実行します。 コマンド 6 も、**プロセス**コマンドのため、コマンド 6 がコマンド 4 と 5 と共に並行で実行できません、 **maxParallel**プロパティが 2 に設定します。  
  
-   コマンド 6 は、コマンド 4 とコマンド 5 の両方が完了した後に直列に実行されます。  
  
-   コマンド 7 はコマンド 6 の完了後に直列に実行されます。  
  
-   コマンド 8 と 9 はコマンド 7 の完了後に並列で実行されます。  
  
## <a name="using-the-batch-command-to-process-objects"></a>バッチ コマンドを使用したオブジェクトの処理  
 **バッチ**コマンドには、いくつかの省略可能なプロパティおよびサポートするために明示的に含まれている属性が含まれます。 複数の処理[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]プロジェクト。  
  
-   **ProcessAffectedObjects**の属性、**バッチ**コマンドは、インスタンスがの結果として再処理を必要とする任意のオブジェクトを処理する必要がありますもかどうかを示す、**プロセス**に含まれるコマンド、**バッチ**コマンド指定のオブジェクトを処理します。  
  
-   [バインド](../../analysis-services/xmla/xml-elements-properties/bindings-element-xmla.md)プロパティには、すべてのによって使用される行外のバインディングのコレクションが含まれています、**プロセス** コマンドを**バッチ**コマンド。  
  
-   [データソース](../../analysis-services/xmla/xml-elements-properties/datasource-element-xmla.md)プロパティが使用するすべてのデータ ソースの行外のバインディングが含まれています、**プロセス** コマンドを**バッチ**コマンド。  
  
-   [DataSourceView](../../analysis-services/xmla/xml-elements-properties/datasourceview-element-xmla.md)プロパティがすべての設定を使ってデータ ソース ビューの行外のバインディングが含まれています、**プロセス** コマンドを**バッチ**コマンド。  
  
-   [ErrorConfiguration](../../analysis-services/xmla/xml-elements-properties/errorconfiguration-element-xmla.md)プロパティでは、方法を指定する、**バッチ**コマンドがすべてで発生したエラーを処理**プロセス**に含まれるコマンド**バッチ**コマンド。  
  
    > [!IMPORTANT]  
    >  A**プロセス**コマンドを含めることはできません、**バインド**、**データソース**、 **DataSourceView**、または**ErrorConfiguration**プロパティ場合、**プロセス**にコマンドが含まれている、**バッチ**コマンド。 これらのプロパティを指定する必要があります場合、**プロセス**コマンドでの対応するプロパティに必要な情報、**バッチ**コマンドを含む、**プロセス**コマンド。  
  
## <a name="see-also"></a>参照  
 [バッチ要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/batch-element-xmla.md)   
 [Process 要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-commands/process-element-xmla.md)   
 [多次元モデルの処理 &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/processing-a-multidimensional-model-analysis-services.md)   
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

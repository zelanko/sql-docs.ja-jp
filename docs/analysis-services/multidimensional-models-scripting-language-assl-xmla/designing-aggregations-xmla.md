---
title: "集計 (XMLA) のデザイン |Microsoft ドキュメント"
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
- statistical information [XML for Analysis]
- batches [XML for Analysis]
- aggregations [Analysis Services], XML for Analysis
- XMLA, aggregations
- queries [XMLA]
- XML for Analysis, aggregations
- iterative aggregation process [XMLA]
ms.assetid: 4dd27afa-10c7-408d-bc24-ca74217ddbcb
caps.latest.revision: 14
author: Minewiskan
ms.author: owend
manager: erikre
ms.translationtype: MT
ms.sourcegitcommit: 876522142756bca05416a1afff3cf10467f4c7f1
ms.openlocfilehash: 9a70f23c8d37218d50713de2f2c65d915ea5f496
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="designing-aggregations-xmla"></a>集計のデザイン (XMLA)
  集計デザインは、集計の格納時に複数のパーティションで同じ構造を確実に使用するようにするため、特定のメジャー グループのパーティションに関連付けられるものです。 使用して後でマージできるパーティションを簡単に定義することにより、パーティションに対して同じ記憶域の構造を使用して、 [MergePartitions](../../analysis-services/xmla/xml-elements-commands/mergepartitions-element-xmla.md)コマンド。 集計デザインの詳細については、次を参照してください。[集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)です。  
  
 使用することができます、集計デザインの集計を定義する、 [DesignAggregations](../../analysis-services/xmla/xml-elements-commands/designaggregations-element-xmla.md) XML for Analysis (XMLA) コマンド。 **DesignAggregations**コマンドには、参照とその参照に基づいたデザイン プロセスを制御する方法として使用する集計デザインを識別するプロパティです。 使用して、 **DesignAggregations**コマンドとそのプロパティを反復処理またはバッチ内の集計をデザインして、デザイン プロセスを評価する結果として得られるデザインの統計を表示します。  
  
## <a name="specifying-an-aggregation-design"></a>集計デザインの指定  
 [オブジェクト](../../analysis-services/xmla/xml-elements-properties/object-element-xmla.md)のプロパティ、 **DesignAggregations**コマンドは、既存の集計デザインへのオブジェクト参照を含める必要があります。 オブジェクト参照には、データベース識別子、キューブ識別子、メジャー グループ識別子、および集計デザイン識別子が含まれます。 既存の集計デザインがない場合、エラーが発生します。  
  
## <a name="controlling-the-design-process"></a>デザイン プロセスの制御  
 次のプロパティを使用することができます、 **DesignAggregations**コマンド、集計デザインの集計を定義するために使用するアルゴリズムを制御します。  
  
-   [手順](../../analysis-services/xmla/xml-elements-properties/steps-element-xmla.md)反復回数を決定するプロパティ、 **DesignAggregations**コマンドは、クライアント アプリケーションに制御を返す前に受け取る必要があります。  
  
-   [時間](../../analysis-services/xmla/xml-elements-properties/time-element-xmla.md)プロパティ時間をミリ秒単位の決定、 **DesignAggregations**コマンドは、クライアント アプリケーションに制御を返す前に受け取る必要があります。  
  
-   [最適化](../../analysis-services/xmla/xml-elements-properties/optimization-element-xmla.md)プロパティ パフォーマンス向上の推定割合を決定し、 **DesignAggregations**コマンドが達成を図る必要があります。 集計を反復的にデザインする場合、このプロパティは最初のコマンドで送信するだけで十分です。  
  
-   [ストレージ](../../analysis-services/xmla/xml-elements-properties/storage-element-xmla.md)プロパティ (バイト単位) で使用される、ディスクの記憶域の予測サイズを決定する、 **DesignAggregations**コマンド。 集計を反復的にデザインする場合、このプロパティは最初のコマンドで送信するだけで十分です。  
  
-   [Materialize](../../analysis-services/xmla/xml-elements-properties/materialize-element-xmla.md)プロパティを決定するかどうか、 **DesignAggregations**コマンドは、デザイン プロセス中に定義された集計を作成する必要があります。 集計を反復的にデザインする場合、デザインした集計を保存する用意ができるまで、このプロパティは false に設定しておく必要があります。 true に設定した場合、現在のデザイン プロセスが終了し、定義された集計は指定した集計デザインに追加されます。  
  
## <a name="specifying-queries"></a>クエリの指定  
 DesignAggregations コマンドは、1 つまたは複数を含めることによって使用法に基づく最適化のコマンドをサポートしている**クエリ**内の要素、[クエリ](../../analysis-services/xmla/xml-elements-properties/queries-element-xmla.md)プロパティです。 **クエリ**プロパティは、1 つまたは複数を含めることができます[クエリ](../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md)要素。 場合、**クエリ**プロパティ含まない**クエリ**で指定された要素の集計のデザイン、**オブジェクト**要素を含む既定の構造を使用して、一般的な集計のセット。 この一般的な集計のセットで指定された条件に一致するものでは、**最適化**と**ストレージ**のプロパティ、 **DesignAggregations**コマンド。  
  
 各 **Query** 要素は、最もよく使用するクエリを対象とする集計を定義するためにデザイン プロセスが使用する、目標クエリを表します。 独自の目標クエリを指定するかのインスタンスで格納されている情報を使用することができます[!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]に関する、最も頻繁に情報を取得するクエリ ログ内のクエリを使用します。 使用法に基づく最適化ウィザードでは、クエリ ログを使用して、送信時に、時間、使用法、または指定されたユーザーに基づいて目標クエリを取得する、 **DesignAggregations**コマンド。 詳細については、次を参照してください。[使用法に基づく最適化ウィザードの F1 ヘルプ](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763)です。  
  
 繰り返しの集計をデザインする場合のみがある、最初に目標クエリを渡す**DesignAggregations**コマンドのため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]インスタンスがこれらの目標クエリを保存し、後続中にこれらのクエリを使用**DesignAggregations**コマンド。 反復処理の最初の **DesignAggregations** コマンドで目標クエリを渡した場合、後続の **DesignAggregations** コマンドの **Queries** プロパティに目標クエリが含まれていると、エラーが発生します。  
  
 **Query** 要素には、以下の引数を含むコンマ区切りの値が含まれます。  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *頻度*  
 クエリが以前に実行された回数に対応する重み係数です。 **Query** 要素が新しいクエリを表す場合、 *Frequency* の値はクエリを評価するためにデザイン プロセスによって使用される重み係数を表します。 この値が大きいほど、デザイン プロセスでクエリに対して付けられる重みが増加します。  
  
 *データセット*  
 ディメンション内のどの属性をクエリに含めるかを指定する数値文字列です。 この文字列の文字数は、ディメンション内の属性の数と一致している必要があります。 0 は、その位置にある属性が、指定されたディメンションのクエリに含まれないことを示します。1 は、その位置にある属性が、指定されたディメンションのクエリに含まれることを示します。  
  
 たとえば文字列 "011" は、3 つの属性を持つディメンションを処理するクエリの中に、2 番目と 3 番目の属性が含まれることを示しています。  
  
> [!NOTE]  
>  いくつかの属性は、データセットでの考慮の対象から除外されます。 除外される属性の詳細については、次を参照してください。 [Query 要素 & #40 です。XMLA &#41;](../../analysis-services/xmla/xml-elements-properties/query-element-xmla.md).  
  
 集計デザインを含むメジャー グループ内の各ディメンションは、 *Query* 要素の **Dataset** の値によって表されます。 *Dataset* の値の順序は、メジャー グループに含まれるディメンションの順序と一致している必要があります。  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>反復処理またはバッチ処理を使用した集計のデザイン  
 使用することができます、 **DesignAggregations**反復処理または、デザイン プロセスで必要な対話性に応じて、バッチ処理の一部としてコマンド。  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>反復処理を使用した集計のデザイン  
 集計を反復処理によってデザインするに送信する複数**DesignAggregations**デザイン プロセスをより細かく制御するためのコマンド。 集計のデザイン ウィザードでも、同じアプローチを使用してデザイン プロセスを細かく制御します。 詳細については、次を参照してください。[集計デザイン ウィザードの F1 ヘルプ](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d)です。  
  
> [!NOTE]  
>  集計を反復処理によってデザインするには、明示的なセッションが必要です。 明示的なセッションの詳細については、次を参照してください。[接続の管理とのセッションと #40 です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
 送信する最初の反復的なプロセスを開始する、 **DesignAggregations**コマンドを次の情報が含まれています。  
  
-   **ストレージ**と**最適化**プロパティの値で、デザイン プロセス全体が対象とします。  
  
-   **手順**と**時間**設計プロセスの最初のステップが制限されているプロパティの値。  
  
-   使用法に基づく最適化を行う場合、**クエリ**デザイン プロセス全体が対象となるでプロパティを含む、目標クエリが実行されます。  
  
-   **Materialize**プロパティを false に設定します。 このプロパティを false に設定することは、コマンドの完了時に、定義された集計がデザイン プロセスによって集計デザインに保存されないことを意味します。  
  
 ときに、まず**DesignAggregations**コマンドが完了すると、このコマンドは、デザインの統計情報を含む行セットを返します。 これらのデザインの統計を評価して、デザイン プロセスを継続するか、あるいは終了するかを判断することができます。 プロセスを続行する場合、送信する別**DesignAggregations**コマンドを含む、**手順**と**時間**デザインのこの手順を処理する値制限されています。 そして結果の統計を評価し、デザイン プロセスを継続すべきかどうかを判断します。 この反復処理を送信する**DesignAggregations**コマンドと、結果を評価するまでの目標を達成し、定義された集計の適切なセットがあります。  
  
 1 つの最終的なを送信する集計のセットに達した後**DesignAggregations**コマンド。 この最終的な**DesignAggregations**コマンドがあります、**手順**プロパティを 1 に設定とその**Materialize**プロパティが true に設定します。 この最終的なこれらの設定を使用して、 **DesignAggregations**コマンドは、デザイン プロセスを完了し、集計デザインに、定義された集計を保存します。  
  
### <a name="designing-aggregations-using-a-batch-process"></a>バッチ処理を使用した集計のデザイン  
 1 つを送信することによって、バッチ処理での集計をデザインすることも**DesignAggregations**コマンドを含む、**手順**、**時間**、**ストレージ**、および**最適化**デザイン プロセス全体を対象し、限られているプロパティの値。 使用法に基づく最適化を実行する場合に、デザイン プロセスが対象となる目標クエリも含める必要がありますで、**クエリ**プロパティです。 確認、 **Materialize**プロパティが true に設定は、デザイン プロセスでは、コマンドが終了したときに集計デザインに、定義された集計を保存できるようにします。  
  
 バッチ処理による集計のデザインは、暗黙のセッションまたは明示的なセッションのいずれでも行うことができます。 暗黙的および明示的なセッションの詳細については、次を参照してください。[接続の管理とのセッションと #40 です。XMLA &#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md).  
  
## <a name="returning-design-statistics"></a>デザインの統計を返す処理  
 ときに、 **DesignAggregations**コマンドは、クライアント アプリケーションに制御を返す、コマンドをコマンドのデザインの統計を表す 1 つの行を含む行セットが返されます。 行セットに含まれる列は、次の表のとおりです。  
  
|列|データ型|Description|  
|------------|---------------|-----------------|  
|手順|Integer|クライアント アプリケーションに制御を返すまでに、コマンドによって行われたステップの数です。|  
|[時刻]|Long integer|クライアント アプリケーションに制御を返すまでに、コマンドで経過したミリ秒単位の時間です。|  
|Optimization|Double|クライアント アプリケーションに制御を返すまでに、コマンドによって達成されたパフォーマンス向上率の予測値です。|  
|ストレージ|Long integer|クライアント アプリケーションに制御を返すまでに、コマンドによって使用されたバイト数の予測値です。|  
|集計|Long integer|クライアント アプリケーションに制御を返すまでに、コマンドによって定義された集計の数です。|  
|LastStep|ブール値|行セット内のデータがデザイン プロセス内の最後のステップを表しているかどうかを示します。 場合、 **Materialize**コマンドのプロパティに設定が true の場合、この列の値が設定を true にします。|  
  
 それぞれの後に返される行セットに含まれるデザインの統計を使用する**DesignAggregations**反復の両方でコマンドとバッチ設計します。 反復処理によるデザインの場合、進行状況の判別と表示を行うために、デザインの統計を使用できます。 集計をバッチ処理によってデザインする場合は、コマンドによって作成された集計の数を判断するために、デザインの統計を使用できます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services の XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

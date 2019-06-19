---
title: 集計のデザイン (XMLA) |Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: b9f681b3c99bd0e8351a844f28b16be6249de199
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63288502"
---
# <a name="designing-aggregations-xmla"></a>集計のデザイン (XMLA)
  集計デザインは、集計の格納時に複数のパーティションで同じ構造を確実に使用するようにするため、特定のメジャー グループのパーティションに関連付けられるものです。 使用して後でマージできるパーティションを簡単に定義することができるパーティションに対して同じストレージ構造を使用して、 [MergePartitions](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/mergepartitions-element-xmla)コマンド。 集計デザインの詳細については、次を参照してください。[集計と集計デザイン](../../analysis-services/multidimensional-models-olap-logical-cube-objects/aggregations-and-aggregation-designs.md)します。  
  
 使用することができます、集計デザインの集計を定義する、 [DesignAggregations](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/designaggregations-element-xmla) XML for Analysis (XMLA) コマンド。 **DesignAggregations**コマンドには、参照とその参照に基づいたデザイン プロセスを制御する方法として使用する集計デザインを識別するプロパティ。 使用して、 **DesignAggregations**コマンドとそのプロパティには、反復処理またはバッチでは、集計をデザインして、デザイン プロセスを評価する結果として得られるデザインの統計を表示できます。  
  
## <a name="specifying-an-aggregation-design"></a>集計デザインの指定  
 [オブジェクト](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla)のプロパティ、 **DesignAggregations**コマンドは、既存の集計デザインへのオブジェクト参照を含める必要があります。 オブジェクト参照には、データベース識別子、キューブ識別子、メジャー グループ識別子、および集計デザイン識別子が含まれます。 既存の集計デザインがない場合、エラーが発生します。  
  
## <a name="controlling-the-design-process"></a>デザイン プロセスの制御  
 次のプロパティを使用することができます、 **DesignAggregations**コマンドは、集計デザインの集計を定義するために使用するアルゴリズムを制御します。  
  
-   [手順](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/steps-element-xmla)プロパティは、反復回数を指定します、 **DesignAggregations**コントロールをクライアント アプリケーションに返す前にコマンドを実行する必要があります。  
  
-   [時間](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/time-element-xmla)プロパティは、ミリ秒数を決定します。、 **DesignAggregations**コントロールをクライアント アプリケーションに返す前にコマンドを実行する必要があります。  
  
-   [最適化](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/optimization-element-xmla)プロパティは、パフォーマンス向上の推定割合を決定します。、 **DesignAggregations**達成を図るコマンド。 集計を反復的にデザインする場合、このプロパティは最初のコマンドで送信するだけで十分です。  
  
-   [ストレージ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/storage-element-xmla)プロパティで使用されるバイト単位のディスク ストレージの推定量を決定する、 **DesignAggregations**コマンド。 集計を反復的にデザインする場合、このプロパティは最初のコマンドで送信するだけで十分です。  
  
-   [具体化](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/materialize-element-xmla)プロパティを決定するかどうか、 **DesignAggregations**コマンドは、デザイン プロセス中に定義されている集計を作成する必要があります。 集計を反復的にデザインする場合、デザインした集計を保存する用意ができるまで、このプロパティは false に設定しておく必要があります。 true に設定した場合、現在のデザイン プロセスが終了し、定義された集計は指定した集計デザインに追加されます。  
  
## <a name="specifying-queries"></a>クエリを指定します。  
 DesignAggregations コマンドは、1 つまたは複数を含めることによって最適化の使用量ベースのコマンドをサポートしている**クエリ**内の要素、[クエリ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/queries-element-xmla)プロパティ。 **クエリ**プロパティは、1 つまたは複数含めることができます[クエリ](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla)要素。 場合、**クエリ**プロパティが含まれない**クエリ**で指定された要素の集計のデザイン、**オブジェクト**要素を含む既定の構造を使用して、一般的な集計のセット。 この一般的な集計のセットがで指定された条件を満たすように設計、**最適化**と**ストレージ**のプロパティ、 **DesignAggregations**コマンド。  
  
 各 **Query** 要素は、最もよく使用するクエリを対象とする集計を定義するためにデザイン プロセスが使用する、目標クエリを表します。 ユーザー独自のクエリを指定することもできますが、 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のインスタンスによってクエリ ログに格納されている情報を使用して、最もよく使用されるクエリに関する情報を取得することもできます。 使用法に基づく最適化ウィザードでは、クエリ ログを使用して、送信するとき、時間、使用状況、または指定されたユーザーに基づいて目標クエリを取得する、 **DesignAggregations**コマンド。 詳細については、次を参照してください。[使用法に基づく最適化ウィザードの F1 ヘルプ](http://msdn.microsoft.com/library/e5f5a938-ae7c-4f4e-9416-a7f94ac82763)します。  
  
 集計を反復的にデザインする場合、目標クエリは最初の **DesignAggregations** コマンドで送信するだけで十分です。これは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスがこれらの目標クエリを保存し、後続の **DesignAggregations** コマンドでそれらのクエリを使用するためです。 反復処理の最初の **DesignAggregations** コマンドで目標クエリを渡した場合、後続の **DesignAggregations** コマンドの **Queries** プロパティに目標クエリが含まれていると、エラーが発生します。  
  
 **Query** 要素には、以下の引数を含むコンマ区切りの値が含まれます。  
  
 *Frequency*,*Dataset*[,*Dataset*...]  
  
 *頻度*  
 クエリが以前に実行された回数に対応する重み係数です。 **Query** 要素が新しいクエリを表す場合、 *Frequency* の値はクエリを評価するためにデザイン プロセスによって使用される重み係数を表します。 この値が大きいほど、デザイン プロセスでクエリに対して付けられる重みが増加します。  
  
 *データセット*  
 ディメンション内のどの属性をクエリに含めるかを指定する数値文字列です。 この文字列の文字数は、ディメンション内の属性の数と一致している必要があります。 0 は、その位置にある属性が、指定されたディメンションのクエリに含まれないことを示します。1 は、その位置にある属性が、指定されたディメンションのクエリに含まれることを示します。  
  
 たとえば文字列 "011" は、3 つの属性を持つディメンションを処理するクエリの中に、2 番目と 3 番目の属性が含まれることを示しています。  
  
> [!NOTE]  
>  いくつかの属性は、データセットでの考慮の対象から除外されます。 除外された属性の詳細については、次を参照してください。 [Query 要素&#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/query-element-xmla)します。  
  
 集計デザインを含むメジャー グループ内の各ディメンションは、 *Query* 要素の **Dataset** の値によって表されます。 *Dataset* の値の順序は、メジャー グループに含まれるディメンションの順序と一致している必要があります。  
  
## <a name="designing-aggregations-using-iterative-or-batch-processes"></a>反復処理またはバッチ処理を使用した集計のデザイン  
 使用することができます、 **DesignAggregations**反復処理または、デザイン プロセスで必要な対話性に応じて、バッチ処理の一部としてコマンド。  
  
### <a name="designing-aggregations-using-an-iterative-process"></a>反復処理を使用した集計のデザイン  
 集計を反復処理によってデザインするには、複数送信**DesignAggregations**デザイン プロセスを細かく制御するためのコマンド。 集計のデザイン ウィザードでも、同じアプローチを使用してデザイン プロセスを細かく制御します。 詳細については、次を参照してください。[集計デザイン ウィザードの F1 ヘルプ](http://msdn.microsoft.com/library/39e23cf1-6405-4fb6-bc14-ba103314362d)します。  
  
> [!NOTE]  
>  集計を反復処理によってデザインするには、明示的なセッションが必要です。 明示的なセッションの詳細については、次を参照してください。[接続の管理とセッション&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)します。  
  
 送信する最初の反復的なプロセスを開始する、 **DesignAggregations**コマンドを次の情報が含まれています。  
  
-   **ストレージ**と**最適化**デザイン プロセス全体が対象となるプロパティの値します。  
  
-   **手順**と**時間**プロパティ値が、デザイン プロセスの最初の手順は制限されています。  
  
-   使用法に基づく最適化する場合、**クエリ**デザイン プロセス全体が対象となるクエリによって、目標を格納するプロパティ。  
  
-   **具体化**プロパティを false に設定します。 このプロパティを false に設定することは、コマンドの完了時に、定義された集計がデザイン プロセスによって集計デザインに保存されないことを意味します。  
  
 ときに、まず**DesignAggregations**コマンドが完了すると、コマンドはデザインの統計を含む行セットを返します。 これらのデザインの統計を評価して、デザイン プロセスを継続するか、あるいは終了するかを判断することができます。 場合、処理を継続し送信する別**DesignAggregations**コマンドが含まれていますが、**手順**と**時間**値は、デザインのこの手順の処理制限されています。 そして結果の統計を評価し、デザイン プロセスを継続すべきかどうかを判断します。 この反復的なプロセスに送信する**DesignAggregations**コマンドと、結果を評価するまでの目標を達成し、定義された集計の適切なセットがあります。  
  
 最後の 1 つを送信する集計のセットに達した後**DesignAggregations**コマンド。 この最終的な**DesignAggregations**コマンドがあります、**手順**プロパティが 1 に設定とその**具体化**プロパティを true に設定します。 この最終的なこれらの設定を使用して**DesignAggregations**コマンドがデザイン プロセスを完了して、集計デザインに定義されている集計を保存します。  
  
### <a name="designing-aggregations-using-a-batch-process"></a>バッチ処理を使用した集計のデザイン  
 1 つを送信することによって、バッチ処理での集計をデザインすることも**DesignAggregations**コマンドが含まれていますが、**手順**、**時間**、**ストレージ**、および**最適化**デザイン プロセス全体を対象し、制限がプロパティの値。 デザイン プロセスが対象となる目標クエリを含めることも使用法に基づく最適化を実行する場合に、**クエリ**プロパティ。 確認、**具体化**プロパティが true に設定は、デザイン プロセスは、コマンドが完了すると集計デザインを定義された集計を保存できるようにします。  
  
 バッチ処理による集計のデザインは、暗黙のセッションまたは明示的なセッションのいずれでも行うことができます。 暗黙的および明示的なセッションの詳細については、次を参照してください。[接続の管理とセッション&#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/managing-connections-and-sessions-xmla.md)します。  
  
## <a name="returning-design-statistics"></a>デザインの統計を返す処理  
 ときに、 **DesignAggregations**コマンドは、クライアント アプリケーションに制御を返した場合、コマンドは、コマンドのデザインの統計を表す 1 つの行を含む行セットを返します。 行セットに含まれる列は、次の表のとおりです。  
  
|[列]|データ型|説明|  
|------------|---------------|-----------------|  
|手順|Integer|クライアント アプリケーションに制御を返すまでに、コマンドによって行われたステップの数です。|  
|Time|Long integer|クライアント アプリケーションに制御を返すまでに、コマンドで経過したミリ秒単位の時間です。|  
|Optimization|Double|クライアント アプリケーションに制御を返すまでに、コマンドによって達成されたパフォーマンス向上率の予測値です。|  
|ストレージ|Long integer|クライアント アプリケーションに制御を返すまでに、コマンドによって使用されたバイト数の予測値です。|  
|集計|Long integer|クライアント アプリケーションに制御を返すまでに、コマンドによって定義された集計の数です。|  
|LastStep|ブール値|行セット内のデータがデザイン プロセス内の最後のステップを表しているかどうかを示します。 場合、**具体化**コマンドのプロパティに設定が true の場合、この列の値が設定を true にします。|  
  
 それぞれの後に返される行セットに含まれるデザインの統計を使用する**DesignAggregations**で両方の反復的なコマンドとバッチ設計します。 反復処理によるデザインの場合、進行状況の判別と表示を行うために、デザインの統計を使用できます。 集計をバッチ処理によってデザインする場合は、コマンドによって作成された集計の数を判断するために、デザインの統計を使用できます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services での XMLA による開発](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  

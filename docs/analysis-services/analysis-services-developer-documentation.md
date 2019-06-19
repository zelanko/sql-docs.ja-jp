---
title: Analysis Services の開発者向けドキュメント |Microsoft Docs
ms.date: 05/08/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: ''
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 44be6e7ab0bb3598b2478f1a5f94e64fee48d05a
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "65449982"
---
# <a name="analysis-services-developer-documentation"></a>Analysis Services の開発者向けドキュメント
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

Analysis Services ではほぼすべてのオブジェクトとワークロードがプログラミング可能なおよび多くの場合から選択する 1 つ以上のアプローチがあります。  マネージ コードの記述、スクリプト、または XMLA および MSOLAP などのオープン標準を使用する場合は、ソリューションの要件は、.NET framework を使用できないわけでは、オプションがあります。

## <a name="what-you-can-accomplish-in-code"></a>コードで行うことができます。
一般的なプログラミング シナリオには、サーバーとデータベースの配置、管理、モデルとデータベースの作成、およびカスタム アプリケーションと Analysis Services データを利用したレポートからのデータ アクセスが含まれます。 これらすべてのシナリオに共通するには固定アーキテクチャとオブジェクトの定義の階層データの定義、処理、およびクエリのワークロードにまたがるに汎用的な操作です。

オブジェクトとワークロードは、プログラミング可能なは、拡張可能ではありません。 具体的には、サポートされていないデータ ソースからデータを取得、カスタマイズまたは数式またはストレージ エンジンの動作を置き換えるカスタム データ カートリッジを作成することはできませんも、サーバー、データベース、またはモデルに新しい種類のオブジェクトのメタデータを作成することができます。

新しいオブジェクトの種類の作成の最後の点でさらに詳しく説明します。 実行時に式またはコードから構築された計算されるオブジェクトを作成するには新しい種類のオブジェクトを作成することはできません。 事前に定義し、既存のデータ構造にマップされて、モデル内のすべていない必要があります。 さらに、クライアント アプリケーションにオブジェクトに固有の情報を渡すには AMO で注釈を使用してスキーマを拡張することができます。

## <a name="choose-a-platform-or-approach-to-development"></a>プラットフォームまたは開発アプローチを選択します。
Analysis Services には、コードのソリューションをカスタマイズする多くの方法が用意されていますが、ほとんどの開発者は、マネージ Api またはスクリプトを使用します。

- マネージ Api が含まれて[AMO および TOM](http://msdn.microsoft.com/library/mt436122.aspx)データ定義と、管理タスクと[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx)でクライアント コードからクエリをサポートします。 SQL Server 2016 では、AMO は新しい表形式のメタデータを使用して、モデルの互換性レベル 1200 以上にアップグレードまたは作成に更新されます。

- スクリプトには、処理量が少ない可能性があると、実行可能プログラムと同じ結果が得られることができます。

  - AMO タイプを直接呼び出す Analysis Services PowerShell コンポーネントを使用して PowerShell スクリプトを記述することができます。 Powershell で、作成し、ASSL/XMLA または TMSL (JSON) でスクリプトを実行することもできます。

  - ASSL、TMSL で使用されるオブジェクトを提供するスクリプト言語を検出し、操作を実行します。 使用するスクリプトの種類は、基になるサーバー、データベース、またはモデルによって異なります。

  - 表形式モデルまたはデータベースの互換性レベル 1200 以上で、Tabular Model Scripting Language (TMSL)、JSON であるを使用します。

  - 多次元モデルとの互換性レベル 1050 ~ 1103 の表形式モデルは、Analysis Services スクリプト言語 (ASSL)、これは XMLA オープン スタンダードの Analysis Services の拡張機能を使用します。

  - Management Studio では、ASSL または TMSL スクリプトを生成できます。 使用することも**コードの表示**ASSL、TMSL のモデル定義を表示する SQL Server Data tools。

- XMLA や MDX のオープン スタンダードに基づくソリューションを構築することはできますが、これを行うにはきわめてまれですが。 .NET またはネイティブ (MSOLAP) テクノロジの経験から、およびほとんどのコミュニティとフォーラムをサポートするための MDX リファレンスを描画し、XMLA 以外のドキュメントはありません。

## <a name="programming-in-analysis-services"></a>Analysis Services でのプログラミング
[データ マイニングのプログラミング](../analysis-services/data-mining/data-mining-programming.md)データ マイニング オブジェクトを含むソリューションを構築する方法について説明します。

[多次元モデルのプログラミング](../analysis-services/multidimensional-models/multidimensional-model-programming.md)開発タスクと、カスタム ソリューションで多次元モデル オブジェクトを統合するための方法について説明します。

[表形式モデルのプログラミング互換性レベル 1200 以降](../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)
**SQL Server 2016 の新**します。  インターフェイスと表形式 1200 モデルと高いモデルをプログラムで操作するために使用されるスクリプト言語をまとめたものです。

[表形式モデルのプログラミングを 1103 互換性レベル 1050 に](../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)このドキュメントは、以前の互換性レベル表形式モデルをサポートする開発者向けです。 これには、XML 構文で表形式モデルを定義する CSDL 拡張機能について説明します。 表形式オブジェクト モデルの定義と構文に関する情報も含まれています。

[Analysis Services 管理オブジェクト (AMO)](https://msdn.microsoft.com/library/mt436122.aspx)用マネージ プロバイダー、Analysis Services 管理オブジェクト (AMO) データ定義と管理、処理などの開発者向けリファレンス ドキュメント。

[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx)プログラムによるデータ アクセスとクエリのワークロードに使用されるマネージ プロバイダー、ADOMD.NET、開発者向けリファレンス ドキュメント。

[Analysis Services のスキーマ行セット](https://docs.microsoft.com/bi-reference/schema-rowsets/analysis-services-schema-rowsets)サーバーの状態、サーバーの操作、およびデータベース オブジェクトに関する情報を提供するスキーマ行セットについて説明します。

[XML for Analysis &#40;XMLA&#41;参照](https://docs.microsoft.com/bi-reference/xmla/xml-for-analysis-xmla-reference)するのに役立つ XMLA の説明の概念は、XMLA は、カスタム ソリューションに貢献する方法を理解します。 XMLA 1.1 仕様への準拠のレベルについても説明します。

[Analysis Services スクリプト言語&#40;XMLA 用 ASSL&#41; ](https://docs.microsoft.com/bi-reference/assl/analysis-services-scripting-language-assl-for-xmla) XMLA に対する ASSL 拡張について説明します。 ASSL では、XMLA 仕様を補完する、Analysis Services 多次元モデルのデータ定義と操作言語を提供します。

[Tabular Model Scripting Language &#40;TMSL&#41;参照](https://docs.microsoft.com/bi-reference/tmsl/tabular-model-scripting-language-tmsl-reference)TMSL は表形式モデルの互換性レベル 1200 以上の JSON 表現。 オブジェクトの定義は、テーブル、列、およびリレーションシップではなく多次元のメタデータを表形式モードで Analysis Services データをモデリングする新しいがある場合は、使い慣れたできない可能性がありますのような表形式のメタデータ コンストラクトに基づいています。

[Analysis Services PowerShell Reference](../analysis-services/powershell/analysis-services-powershell-reference.md)ドキュメント管理機能に加えて、汎用的な使用するコマンドレット**Invoke ASCmd**を任意のスクリプトまたはクエリの入力として受け取るコマンドレット。

## <a name="see-also"></a>参照
[テクニカル リファレンス](../analysis-services/powershell/technical-reference-ssas.md)
[クエリと式言語のリファレンス&#40;Analysis Services&#41;](http://msdn.microsoft.com/library/gg492188.aspx)

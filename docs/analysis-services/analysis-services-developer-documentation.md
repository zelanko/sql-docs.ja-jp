---
title: Analysis Services の開発者向けドキュメント |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/24/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
helpviewer_keywords:
- multidimensional data [Analysis Services], developer's guide
- developer's guide [Analysis Services - multidimensional data]
ms.assetid: 0a6eda76-1c5e-487e-9c8b-1feb09f1a34c
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: e6feb651ac8a473bf717d86cdeccef6c16bc1a74
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="analysis-services-developer-documentation"></a>Analysis Services の開発者向けドキュメント
[!INCLUDE[ssas-appliesto-sqlas-aas](../includes/ssas-appliesto-sqlas-aas.md)]

Analysis Services ではほとんどすべてのオブジェクトとワークロードは、プログラミング、および多くの場合からを選択する 1 つ以上の方法もあります。  マネージ コードの記述、スクリプト、または場合は、ソリューションの要件は、.NET framework を使用できないわけでは、XMLA および MSOLAP などのオープン スタンダードを使用して、オプションが含まれます。

## <a name="what-you-can-accomplish-in-code"></a>コードで行うことができます。
一般的なプログラミング シナリオには、サーバーとデータベースの配置、管理、モデルとデータベースの作成、およびカスタム アプリケーションと Analysis Services データを使用するレポートのデータにアクセスが含まれます。 固定のアーキテクチャとオブジェクトの定義の階層、データ定義、処理、およびクエリのワークロードにまたがる周知の操作は、これらすべてのシナリオに一般的なのです。

オブジェクトとワークロードは、プログラミング可能なは、拡張可能ではありません。 具体的には、サポートされていないデータ ソースからデータを取得、カスタマイズ、または数式または記憶域のエンジンの動作を置き換えるカスタム データ カートリッジを作成することはできません。 またサーバー、データベース、またはモデルに新しい種類のオブジェクトのメタデータを作成することができます。

新しいオブジェクトの種類の作成の最後のポイントでさらに詳しく説明します。 新しい種類のオブジェクトを作成することはできません、実行時に式またはコードから作成された計算のオブジェクトを作成できます。 定義済みし、既存のデータ構造にマップできません、モデル内のすべて必要があります。 さらに、クライアント アプリケーションにオブジェクトに固有の情報を渡すには AMO での注釈を使用してスキーマを拡張することができます。

## <a name="choose-a-platform-or-approach-to-development"></a>プラットフォームまたは開発する方法を選択します。
Analysis Services には、コード内のソリューションをカスタマイズする多くの方法が用意されていますが、ほとんどの開発者は、マネージ Api またはスクリプトを使用します。

- マネージ Api が含まれて[AMO および TOM](http://msdn.microsoft.com/library/mt436122.aspx)データ定義と、管理タスクと[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx)でクライアント コードからクエリをサポートします。 SQL Server 2016 では、AMO は、新しい表形式メタデータを使用して、モデルの作成または互換性レベル 1200 以上にアップグレードに更新されます。

- スクリプトには、可能性のある処理量が少ないと、実行可能プログラムと同じ結果が得られることができます。

  - AMO タイプを直接呼び出す Analysis Services PowerShell コンポーネントを使用する PowerShell スクリプトを記述することができます。 PowerShell、内でも作成し、ASSL/XMLA または TMSL (JSON) でスクリプトを実行できます。

  - ASSL、TMSL で使用されるオブジェクトを提供するスクリプト言語の検出操作を実行します。 使用するスクリプトの種類は、基になるサーバー、データベース、またはモデルによって異なります。

  - 表形式モデルまたはデータベースの互換性レベル 1200 以上で、表形式モデル スクリプト言語 (TMSL)、JSON であるを使用します。

  - 多次元モデルとの互換性レベル 1050 ~ 1103 の表形式モデルは、Analysis Services スクリプト言語 (ASSL)、これは XMLA オープン スタンダードの Analysis Services の拡張機能を使用します。

  - ASSL または TMSL スクリプトは、Management Studio で生成できます。 使用することも**コードの表示**ASSL または TMSL で、モデル定義を表示する SQL Server Data Tools でします。

- XMLA や MDX のオープン スタンダードに基づくソリューションを構築することはできますは、そのためには非常にまれです。 XMLA 以外のドキュメントはありませんし、ユーザー、およびほとんどのコミュニティとサポート フォーラムできるように MDX リファレンスは、.NET またはネイティブ (MSOLAP) テクノロジでの経験から描画します。

## <a name="programming-in-analysis-services"></a>Analysis Services でのプログラミング
[データ マイニングのプログラミング](../analysis-services/data-mining-programming.md)データ マイニング オブジェクトを含むソリューションを構築する方法について説明します。

[多次元モデルのプログラミング](../analysis-services/multidimensional-models/multidimensional-model-programming.md)開発タスクと、カスタム ソリューションで多次元モデル オブジェクトを統合するための方法について説明します。

[互換性レベル 1200 以降、表形式のモデルにプログラミング](../analysis-services/tabular-model-programming-compatibility-level-1200/tabular-model-programming-for-compatibility-level-1200.md)
**SQL Server 2016 の**します。  インターフェイスと表形式 1200 と高いモデルの操作にプログラムで使用されるスクリプト言語をまとめたものです。

[表形式モデルのプログラミングを 1103 互換性レベル 1050 の](../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/tabular-model-programming-for-compatibility-levels-1050-through-1103.md)互換性レベルの表形式モデルをサポートしている開発者にとってこのドキュメントが対象としています。 これには、XML 構文で表形式モデルを定義する CSDL 拡張機能について説明します。 表形式オブジェクト モデルの定義と構文に関する情報も含まれています。

[Analysis Services 管理オブジェクト (AMO)](https://msdn.microsoft.com/library/mt436122.aspx)開発者向けリファレンス ドキュメントのマネージ プロバイダー、Analysis Services 管理オブジェクト (AMO) データ定義と、処理など、管理します。

[ADOMD.NET](http://msdn.microsoft.com/library/mt465769.aspx)のプログラムによるデータ アクセスおよびクエリのワークロードに使用されるマネージ プロバイダー、ADOMD.NET、開発者向けリファレンス ドキュメント。

[Analysis Services のスキーマ行セット](../analysis-services/schema-rowsets/analysis-services-schema-rowsets.md)サーバーの状態、サーバー操作、およびデータベース オブジェクトに関する情報を提供するスキーマ行セットについて説明します。

[XML for Analysis &#40;XMLA&#41;参照](../analysis-services/xmla/xml-for-analysis-xmla-reference.md)するのに役立つ XMLA の説明の概念は、XMLA が、カスタム ソリューションに貢献する方法を理解します。 XMLA 1.1 仕様への準拠のレベルについても説明します。

[Analysis Services スクリプト言語&#40;の ASSL を XMLA&#41; ](../analysis-services/scripting/analysis-services-scripting-language-assl-for-xmla.md) XMLA に対する ASSL 拡張について説明します。 ASSL では、XMLA 仕様を補完する、Analysis Services 多次元モデルのデータ定義と操作言語を提供します。

[表形式モデル スクリプト言語&#40;TMSL&#41;参照](../analysis-services/tabular-model-scripting-language-tmsl-reference.md)TMSL は、互換性レベル 1200 以上の表形式モデルの JSON 表現。 オブジェクトの定義は、テーブル、列、およびリレーションシップではなく Analysis Services データをモデリングする新しい表形式モードである場合に使い慣れたでない可能性のあるマルチ ディメンションのメタデータと同様に、表形式のメタデータ構造に基づいています。

[Analysis Services PowerShell Reference](../analysis-services/powershell/analysis-services-powershell-reference.md)ドキュメントの管理の機能に加えて、汎用的な使用されるコマンドレット**Invoke ASCmd**を任意のスクリプトまたはクエリの入力として受け取るコマンドレット。

## <a name="see-also"></a>参照
[テクニカル リファレンス](../analysis-services/powershell/technical-reference-ssas.md) 
[クエリと式言語リファレンス&#40;Analysis Services&#41;](http://msdn.microsoft.com/library/gg492188.aspx)

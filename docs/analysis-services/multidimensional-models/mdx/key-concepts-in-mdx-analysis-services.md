---
title: 重要な概念 (Analysis Services) の MDX の |Microsoft ドキュメント
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.component: mdx
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: a47a267c2947f59df57dc61bb821f4712b305b0b
ms.sourcegitcommit: 38f8824abb6760a9dc6953f10a6c91f97fa48432
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="key-concepts-in-mdx-analysis-services"></a>MDX の主な概念 (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../../includes/ssas-appliesto-sqlas.md)]
  多次元式 (MDX) を使用して多次元データを照会したり、キューブ内で MDX 式を作成したりするには、多次元の概念と用語を理解しておく必要があります。  
  
 既にご存じのデータ要約の例を足掛かりにして、それと MDX の関連性を確認することをお勧めします。 ここでは、Excel でピボットテーブルを作成し、それに Analysis Services サンプル キューブからのデータを設定します。  
  
 ![ピボット テーブルにメジャーとディメンションが呼び出された](../../../analysis-services/multidimensional-models/media/ssas-keyconcepts-pivot1-measures-dimensions.png "にメジャーとディメンションが呼び出されたピボット テーブル")  
  
## <a name="measures-and-dimensions"></a>メジャーとディメンション  
 Analysis Services キューブは、ピボットテーブルの例で示したメジャー、ディメンション、およびディメンション属性で構成されます。  
  
 **メジャー** は、合計、カウント、パーセンテージ、最小、最大、または平均として集計されるセル内の数値データ値です。 メジャー値は、動的で、ユーザーのナビゲーションやピボットテーブルとのやり取りに反応して、リアルタイムに計算されます。 この例では、各セルが軸の展開と折りたたみに基づいて増減する Reseller Sales Amounts を表しています。 Date (年、四半期、月、または日付) と Sales Territory (国のグループ、国、地域) の任意の組み合わせに対して、その特定のコンテキストで集計された Reseller Sales Amount を取得できます。 メジャーの同義語である他の用語としては、ファクト (データ ウェアハウス内) と計算フィールド (テーブルと Excel データ モデル内) があります。  
  
 **ディメンション** は、ピボットテーブルの列軸と行軸上に表示され、メジャーの背後にある意味を表します。 ディメンションは、リレーショナル データ モデル内のテーブルに似ています。 ディメンションの一般的な例として、Time、Geography、Products、Customers、Employees などが挙げられます。 この例は、各行の Sales Territory と最上部の Date の 2 つのディメンションで構成されていますが、Promotions や Products などの Reseller Sales に関連付けられた他のディメンションをドラッグ アンド ドロップして、簡単に、それらのディメンションに沿った販売実績を表示することができます。 データを効率的に探索できるかどうかは、作成するディメンションと、それがデータ ソース内のファクト テーブルと関連性があるかどうかに応じて異なります。  
  
 **ディメンション属性** は、テーブル内の列と同様の、ディメンション内の名前付きアイテムです。 この例では、Sales Territory ディメンション属性が、Country Group (Europe、North America、Pacific)、Country (Canada、United States)、および Region (Central、Northeast、Northwest、Southeast、Southwest) で構成されています。  
  
 各属性には、データ値のコレクション、または、それに関連付けられたメンバーが含まれています。 この例では、Country Group 属性のメンバーは、Europe、North America、および Pacific です。 **メンバー** は、属性に属している実際のデータ値を表します。  
  
> [!NOTE]  
>  データ モデリングの 1 つの側面は、データ自体に内在するパターンとリレーションシップを形式化することです。 国/地域/都市のような自然階層に分類されるデータを操作する場合は、 **属性リレーションシップ**を作成することによって、そのリレーションシップを形式化することができます。 属性リレーションシップは、属性間の一対多のリレーションシップです。たとえば、州と都市の間のリレーションシップでは、州には複数の都市がありますが、都市は 1 つの州にしか属しません。 モデル内で属性リレーションシップを作成すれば、クエリ パフォーマンスが向上するため、データでサポートされている場合は属性リレーションシップを作成することをお勧めします。 属性リレーションシップは、SQL Server Data Tools 内のディメンション デザイナーで作成できます。 「 [Define Attribute Relationships](../../../analysis-services/multidimensional-models/attribute-relationships-define.md)」を参照してください。  
  
 Excel 内部のピボットテーブル フィールド リストにモデル メタデータが表示されます。  上のピボットテーブルと下のフィールド リストを比較します。 フィールド リストには Sales Territory、Group、Country、Region (メタデータ) が含まれているのに対して、ピボットテーブルにはメンバー (データ値) しか含まれていないことに注意してください。 アイコンの外観を識別することによって、多次元モデルの部品を容易に Excel 内のピボットテーブルに関連付けることができます。  
  
 ![ピボット テーブル フィールド リスト](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-ptfieldlist.png "ピボット テーブル フィールド リスト")  
  
## <a name="attribute-hierarchies"></a>属性階層  
 深く考えなくても、各軸に沿ってレベルを展開したり、折りたたんだりするだけで、ピボットテーブル内の値が増減することがわかっていますが、どうしてこんなことができるのでしょうか。 答えは属性階層にあります。  
  
 すべてのレベルを折りたたむと、各 Country Group と Calendar Year の総合計が表示されます。 この値は、階層内の **(すべての) メンバー** と呼ばれるものから抽出されます。 (すべての) メンバーは、属性階層内のすべてのメンバーの値を計算したものです。  
  
-   すべての Country Groups と Dates の (すべての) メンバーを集計すると、$80,450,596.98 になります。  
  
-   CY2008 の (すべての) メンバーは $16,038,062.60 です。  
  
-   Pacific の (すべての) メンバーは $1,594,335.38 です。  
  
 このような集計は、事前に計算され、保存されます。これが、Analysis Services のクエリ パフォーマンスが優れている秘密の一部です。  
  
 ![すべてのメンバーが呼び出されたピボット テーブル](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot2-allmember.png "すべてのメンバーが呼び出されたピボット テーブル")  
  
 階層を展開すると、最終的に、最下位レベルに到達します。 これは **リーフ メンバー**と呼ばれます。 リーフ メンバーは、子が存在しない階層のメンバーです。 この例では、Australia がリーフ メンバーです。  
  
 ![リーフ メンバーが呼び出されたピボット テーブル](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot3-leafparent.PNG "リーフ メンバーが呼び出されたピボット テーブル")  
  
 上位にあるものは **親メンバー**と呼ばれます。 Pacific は Australia の親です。  
  
 **属性階層の構成要素**  
  
 総じて、これらの概念のすべてが **属性階層**という概念を作り上げています。 属性階層は、さまざまな属性メンバーからなる 1 つのツリー構造であり、それには以下のレベルが含まれています。  
  
-   リーフ レベル。個別の属性メンバーが含まれています。リーフ レベルの各メンバーを **リーフ メンバー**ともいいます。  
  
-   属性階層が親子階層の場合の中間レベル (詳細は後述)。  
  
-   すべての子属性の集計値を含む (すべての) メンバー。 オプションで、データの意味をなさない (すべての) レベルを非表示にする、または、オフにすることができます。 たとえば、Product Code は数字ですが、合計や平均は意味をなしませんし、それ以外の方法ですべての Product Codes を集計することもありません。  
  
> [!NOTE]  
>  BI 開発者の多くは、クライアント アプリケーションで特定の動作を実現するためや特定のパフォーマンス メリットを得るために、属性階層のプロパティを設定します。 たとえば、(すべての) メンバーが意味をなさない属性に AttributeHierarchyEnabled=False を設定することができます。 または、(すべての) メンバーを非表示にするだけなら、AttributeHierarchyVisible=False を設定することができます。 プロパティの詳細については、「 [Dimension Attribute Properties Reference](../../../analysis-services/multidimensional-models/dimension-attribute-properties-reference.md) 」を参照してください。  
  
## <a name="navigation-hierarchies"></a>ナビゲーション階層  
 ピボットテーブル (少なくともこの例の) では、行軸と列軸を展開すると、下位レベルの属性が表示されます。 拡張可能なツリーは、モデル内に作成されたナビゲーション階層を通して実現されます。  AdventureWorks サンプル モデルでは、Sales Territory ディメンションに Country Group、Country、および Region の順で複数レベル階層が含まれています。  
  
 ご存じのように、階層はピボットテーブルまたはその他のデータ要約オブジェクト内のナビゲーション パスを提供するために使用されます。 これには均衡と不均衡という 2 つの基本的な種類があります。  
  
 **均衡階層**  
  
|||  
|-|-|  
|![均衡階層が呼び出されたピボット テーブル](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot4-balancedhierarchy.PNG "均衡階層が呼び出されたピボット テーブル")|**均衡階層** は、最上位メンバーと任意のリーフ メンバーの間のレベル数が等しい階層です。<br /><br /> **自然階層** は基になるデータから自然に発生する階層です。 一般的な例は、それぞれの下位レベルが予想どおり親から派生する、国/地域/州や年/月/日などのカテゴリ/サブカテゴリ モデルです。<br /><br /> 多次元モデルでは、ほとんどの階層が均衡階層で、その多くが自然階層でもあります。<br /><br /> 属性階層とよく対比される、もう 1 つの関連モデリング用語として、 **ユーザー定義階層**があります。 これは、属性を定義すると Analysis Services によって自動的に生成される属性階層とは対照的に、BI 開発者によって作成される階層を意味します。|  
  
 **不均衡階層**  
  
|||  
|-|-|  
|![不規則階層が呼び出されたピボット テーブル](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-pivot15-raggedhierarchy.PNG "不規則階層が呼び出されたピボット テーブル")|**不規則階層** または **不均衡階層** は、トップ レベル メンバーとリーフ メンバーの間に存在するレベルの数が一様でない階層です。 これも、BI 開発者によって作成される階層ですが、データが連続していません。<br /><br /> AdventureWorks サンプル モデルでは、United States に他の国には存在しない追加のレベル (Regions) が含まれている Sales Territory が不規則階層を表しています。<br /><br /> 不規則階層は、クライアント アプリケーションでうまく処理されない場合、BI 開発者が対処する必要があります。 Analysis Services モデルでは、複数レベルのデータ間のリレーションシップを明示的に定義することによって、レベル間のあいまいな関係性を排除した **親子階層** を構築できます。 詳細については、「 [親子ディメンション](../../../analysis-services/multidimensional-models/parent-child-dimension.md) 」を参照してください。|  
  
## <a name="key-attributes"></a>キー属性  
 モデルは、キーとインデックスを使って関連付けを示す関連オブジェクトのコレクションです。 Analysis Services モデルについても違いはありません。 ディメンション (リレーショナル モデルのテーブルに相当することを思い出してください) ごとに、キー属性が存在します。 **キー属性** は、ファクト テーブル (メジャー グループ) に対する外部キー リレーションシップで使用されます。 ディメンション内のすべての非キー属性がキー属性に (直接的または間接的に) リンクされます。  
  
 必ずではありませんが、キー属性の多くは **粒度属性**でもあります。 粒度は、データ内の詳細または精度のレベルを表します。 この場合も、一般的な例が理解の助けになります。 日付の値を考えてみましょう。日次売上の場合は、日付の値を日に設定する必要があります。売上予算の場合は、四半期ごとで十分ですが、分析データがスポーツ イベントのレース結果で構成されている場合は、粒度をミリ秒にする必要があります。 データ値の精度のレベルが粒度です。  
  
 通貨はもう一つの例です: 財務アプリケーションは小数点以下数桁までの金銭的価値を追求する必要があるのに対して、地方の学校の資金調達担当者は 1 ドル単位に四捨五入した値で十分です。 粒度の理解は、不要なデータの保存を避けるという意味でも重要です。 詳細のレベルが分析に影響しない場合は、タイムスタンプからミリ秒を切り捨てる、または、売上高から少額を切り捨てることによって、ストレージと処理時間を節約することができます。  
  
 粒度属性を設定するには、SQL Server Data Tools 内のキューブ デザイナーの [ディメンションの使用法] タブを使用します。 AdventureWorks サンプル モデルでは、Date ディメンションのキー属性は Date キーです。 Sales Orders の場合は、粒度属性がキー属性と等価です。 Sales Targets の場合は、粒度のレベルが四半期ごとであり、それに応じて、粒度属性が Calendar Quarter に設定されます。  
  
 ![粒度属性を示すモデル](../../../analysis-services/multidimensional-models/mdx/media/ssas-keyconcepts-granularityattrib.png "粒度属性を示すモデル")  
  
> [!NOTE]  
>  粒度属性とキー属性が異なる場合は、すべての非キー属性を直接的または間接的に粒度属性にリンクする必要があります。 キューブ内ではディメンションの粒度が粒度属性で定義されます。  
  
## <a name="query-scope-cube-space"></a>クエリ スコープ (キューブ空間)  
 クエリのスコープは、データが選択される境界を意味します。 これは、キューブ全体 (キューブは最大のクエリ オブジェクト) からセルまでの範囲になります。  
  
 **キューブ空間** は、そのキューブのメジャーを伴った、キューブの属性階層のメンバーから構成されます。  
  
 **サブキューブ** は、キューブのフィルターを適用したビューを表す、キューブのサブセットです。 サブキューブは、MDX 計算スクリプト内の Scope ステートメントを使用して、あるいは、MDX クエリ内のサブセレクト句で、または、セッション キューブとして定義することができます。  
  
 **セル** は、メジャー ディメンション メンバーのメンバーとキューブ内の各属性階層からのメンバー間のスペースを意味します。  
  
## <a name="other-modeling-terms"></a>その他のモデリング用語  
 このセクションでは、他のセクションに含めるのは難しいが、知っておく必要のある概念と用語を集めて説明します。  
  
 **計算メンバー** は、クエリ実行時に定義と計算がなされるディメンション メンバーです。 計算されるメンバーをユーザー クエリまたは MDX 計算スクリプトで定義して、サーバーに保存しておくことができます。 計算されるメンバーは、その計算されるメンバーが定義されているディメンション内のディメンション テーブルの行と対応します。  
  
 **個別カウント** は、1 度しかカウントされないデータ項目に使用される特殊なメジャーです。 AdventureWorks サンプル モデルには、Internet Orders、Reseller Orders、および Sales Orders の個別カウント メジャーが含まれています。  
  
 **メジャー グループ** は、1 つ以上のメジャーのコレクションです。 そのほとんどは、ユーザー定義であり、関連メジャーをまとめて保持するために使用します。 個別カウント メジャーは例外です。 このメジャーは、必ず、個別メジャーのみを含む専用のメジャー グループに配置されます。 ピボットテーブルの例ではメジャー グループを確認することはできませんが、メジャーの名前付きコレクションとしてピボットテーブル フィールド リストに表示されます。  
  
 **メジャー ディメンション** は、キューブ内のすべてのメジャーを含むディメンションです。 SQL Server Data Tools で構築する多次元モデルには登場しませんが、まったく同じように存在します。 これにはメジャーが含まれているため、通常は、メジャー ディメンションのすべてのメンバーが集計されます (合計またはカウントによって)。  
  
 **データベース ディメンションとキューブ ディメンション**。 モデル内では、スタンドアロン ディメンションを定義して、同じモデル内の任意の数のキューブに含めることができます。 ディメンションがキューブに追加された場合は、キューブ ディメンションと呼ばれます。 プロジェクト内部では、Object Explorer 内のスタンドアロン項目として、データベース ディメンションと呼ばれます。 どうして区別が必要なのでしょうか。 それは、それぞれに独立的にプロパティを設定できるからです。 製品マニュアルでは、両方の用語が使用されているため、それぞれの意味を理解しておく必要があります。  
  
## <a name="next-steps"></a>次の手順  
 これで、重要な概念と用語が理解できたところで、Analysis Services の基本的な概念をさらに詳しく説明している以下のトピックに進むことができます。  
  
-   [MDX の基本的なクエリ & #40 です。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/mdx-query-the-basic-query.md)  
  
-   [基本的な MDX スクリプト & #40 です。MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/the-basic-mdx-script-mdx.md)  
  
-   [多次元モデリング & #40 です。Adventure Works チュートリアル & #41;](../../../analysis-services/multidimensional-modeling-adventure-works-tutorial.md)  
  
## <a name="see-also"></a>参照  
 [キューブ空間](../../../analysis-services/multidimensional-models/mdx/cube-space.md)   
 [組](../../../analysis-services/multidimensional-models/mdx/tuples.md)   
 [Autoexists](../../../analysis-services/multidimensional-models/mdx/autoexists.md)   
 [メンバー、組、およびセット & #40; の操作MDX と #41 です。](../../../analysis-services/multidimensional-models/mdx/working-with-members-tuples-and-sets-mdx.md)   
 [表示部分の合計と非表示部分の合計](../../../analysis-services/multidimensional-models/mdx/visual-totals-and-non-visual-totals.md)   
 [MDX クエリの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-query-fundamentals-analysis-services.md)   
 [MDX スクリプティングの基礎と #40 です。Analysis Services & #41;](../../../analysis-services/multidimensional-models/mdx/mdx-scripting-fundamentals-analysis-services.md)   
 [MDX 言語リファレンス & #40 です。MDX と #41 です。](../../../mdx/mdx-language-reference-mdx.md)   
 [多次元式 & #40 です。MDX と #41 です。参照](../../../mdx/multidimensional-expressions-mdx-reference.md)  
  
  

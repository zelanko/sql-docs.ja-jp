---
title: MDX 関数リファレンス (MDX) |Microsoft ドキュメント
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
dev_langs:
- kbMDX
helpviewer_keywords:
- member functions [MDX]
- level functions [MDX]
- MDX [Analysis Services], functions
- array functions
- string functions
- Multidimensional Expressions [Analysis Services], functions
- hierarchy functions [MDX]
- numeric functions [MDX]
- tuple functions
- subcube functions [MDX]
- functions [MDX]
- logical functions [MDX]
- set functions [MDX]
ms.assetid: e363722a-3e5b-40a9-a0b5-399dd2d93f6d
caps.latest.revision: 36
author: Minewiskan
ms.author: owend
manager: erikre
ms.openlocfilehash: 8f0be993df9a930e175de9d33aaff92271cda329
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="mdx-function-reference-mdx"></a>MDX 関数リファレンス (MDX)
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)] 多次元式 (MDX) 構文では関数の使用を提供します。 関数は有効な MDX ステートメントで使用でき、多くの場合、クエリ、カスタム ロールアップ定義、その他の計算などに使用されます。 このセクションに含まれている MDX 関数に関する情報が[!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]です。  
  
 以下の表では、戻り値の種類ごとに関数がまとめられています。また、目次には、関数名がアルファベット順に一覧表示されます。  
  
## <a name="array-functions"></a>配列関数  
  
|関数|Description|  
|--------------|-----------------|  
|[SetToArray &#40;MDX&#41;](../mdx/settoarray-mdx.md)|ユーザー定義関数で使用するために、1 つ以上のセットを配列に変換します。|  
  
## <a name="hierarchy-functions"></a>階層関数  
  
|関数|Description|  
|--------------|-----------------|  
|[階層&#40;MDX&#41;](../mdx/hierarchy-mdx.md)|指定されたメンバーまたはレベルを含む階層を返します。|  
|[ディメンション&#40;MDX&#41;](../mdx/dimension-mdx.md)|指定されたメンバー、レベル、階層を含むディメンションを返します。|  
|[ディメンション&#40;MDX&#41;](../mdx/dimensions-mdx.md)|数値式や文字列式で指定された階層を返します。|  
  
## <a name="level-functions"></a>レベル関数  
  
|関数|Description|  
|--------------|-----------------|  
|[レベル&#40;MDX&#41;](../mdx/level-mdx.md)|メンバーのレベルを返します。|  
|[レベル&#40;MDX&#41;](../mdx/levels-mdx.md)|数値式でディメンション内または階層内の位置を指定されたレベル、または文字列式で名前を指定されたレベルを返します。|  
  
## <a name="logical-functions"></a>論理関数  
  
|関数|Description|  
|--------------|-----------------|  
|[IsAncestor &#40;MDX&#41;](../mdx/isancestor-mdx.md)|指定されたメンバーが指定された別のメンバーの先祖かどうかを返します。|  
|[IsEmpty &#40;MDX&#41;](../mdx/isempty-mdx.md)|評価した式が空のセル値かどうかを返します。|  
|[IsGeneration &#40;MDX&#41;](../mdx/isgeneration-mdx.md)|指定されたメンバーが指定された世代内にあるかどうかを返します。|  
|[IsLeaf &#40;MDX&#41;](../mdx/isleaf-mdx.md)|指定されたメンバーがリーフ メンバーであるかどうかを返します。|  
|[IsSibling &#40;MDX&#41;](../mdx/issibling-mdx.md)|指定されたメンバーが指定された別のメンバーの兄弟かどうかを返します。|  
  
## <a name="member-functions"></a>メンバー関数  
  
|関数|Description|  
|--------------|-----------------|  
|[先祖&#40;MDX&#41;](../mdx/ancestor-mdx.md)|メンバーの先祖のうち、指定されたレベルまたは距離にある先祖を返します。|  
|[ClosingPeriod &#40;MDX&#41;](../mdx/closingperiod-mdx.md)|メンバーの子孫の中から、指定されたレベルにある最後の兄弟を返します。|  
|[Cousin &#40;MDX&#41;](../mdx/cousin-mdx.md)|親メンバーからの相対位置が、指定された子メンバーと同じ子メンバーを返します。|  
|[CurrentMember &#40;MDX&#41;](../mdx/currentmember-mdx.md)|繰り返し処理の実行時に、指定されたディメンションまたは階層の現在のメンバーを返します。|  
|[DataMember &#40;MDX&#41;](../mdx/datamember-mdx.md)|ディメンションの非リーフ メンバーに関連付けられたシステム生成データ メンバーを返します。|  
|[DefaultMember &#40;MDX&#41;](../mdx/defaultmember-mdx.md)|ディメンションまたは階層の既定のメンバーを返します。|  
|[FirstChild &#40;MDX&#41;](../mdx/firstchild-mdx.md)|メンバーの先頭の子メンバーを返します。|  
|[FirstSibling &#40;MDX&#41;](../mdx/firstsibling-mdx.md)|メンバーの親の最初の子メンバーを返します。|  
|[項目&#40;メンバー&#41; &#40;MDX&#41;](../mdx/item-member-mdx.md)|指定された組からメンバーを返します。|  
|[Lag &#40;MDX&#41;](../mdx/lag-mdx.md)|ディメンション内の指定されたメンバーから指定された数だけ前にあるメンバーを返します。|  
|[LastChild &#40;MDX&#41;](../mdx/lastchild-mdx.md)|指定されたメンバーの最後の子メンバーを返します。|  
|[LastSibling &#40;MDX&#41;](../mdx/lastsibling-mdx.md)|指定されたメンバーの親の最後の子を返します。|  
|[潜在顧客&#40;MDX&#41;](../mdx/lead-mdx.md)|ディメンション内の指定されたメンバーから指定された数だけ後にあるメンバーを返します。|  
|[LinkMember &#40;MDX&#41;](../mdx/linkmember-mdx.md)|指定された階層の指定されたメンバーと等価のメンバーを返します。|  
|[メンバー&#40;文字列&#41; &#40;MDX&#41;](../mdx/members-string-mdx.md)|文字列式で指定されたメンバーを返します。|  
|[NextMember &#40;MDX&#41;](../mdx/nextmember-mdx.md)|指定されたメンバーを含むレベル内にある次のメンバーを返します。|  
|[OpeningPeriod &#40;MDX&#41;](../mdx/openingperiod-mdx.md)|指定したレベルの子孫で、最初の兄弟を返します。オプションでメンバーも指定できます。|  
|[ParallelPeriod &#40;MDX&#41;](../mdx/parallelperiod-mdx.md)|前の期間から、指定されたメンバーと同じ相対位置にあるメンバーを返します。|  
|[親&#40;MDX&#41;](../mdx/parent-mdx.md)|メンバーの親メンバーを返します。|  
|[PrevMember &#40;MDX&#41;](../mdx/prevmember-mdx.md)|指定されたメンバーを含むレベルにある直前のメンバーを返します。|  
|[StrToMember &#40;MDX&#41;](../mdx/strtomember-mdx.md)|MDX 形式の文字列によって指定されているメンバーを返します。|  
|[UnknownMember &#40;MDX&#41;](../mdx/unknownmember-mdx.md)|レベルまたはメンバーに関連付けられている不明なメンバーを返します。|  
|[ValidMeasure &#40;MDX&#41;](../mdx/validmeasure-mdx.md)|適用できないディメンションをトップ レベルにすることにより、仮想キューブ内の有効なメジャーを返します。|  
  
## <a name="numeric-functions"></a>数値関数  
  
|関数|Description|  
|--------------|-----------------|  
|[集計&#40;MDX&#41;](../mdx/aggregate-mdx.md)|指定されたセットの組に対し、メジャーを集計するか、またはオプションとして指定された数値式を集計することによって、スカラー値を返します。|  
|[Avg &#40;MDX&#41;](../mdx/avg-mdx.md)|指定されたセットに対して評価されるメジャーの平均値、またはオプションで指定した数値式の平均値を返します。|  
|[CalculationCurrentPass (MDX)](../mdx/calculationcurrentpass-mdx.md)|指定されたクエリ コンテキストで、キューブの現在の計算パスを返します。|  
|[CalculationPassValue (MDX)](../mdx/calculationpassvalue-mdx.md)|キューブに対して指定された計算パスを評価し、MDX 式の値を返します。|  
|[CoalesceEmpty &#40;MDX&#41;](../mdx/coalesceempty-mdx.md)|空のセル値を数値または文字列に連結し、連結後の値を返します。|  
|[相関関係&#40;MDX&#41;](../mdx/correlation-mdx.md)|セットに対して評価される 2 つの系列の相関係数を返します。|  
|[カウント&#40;ディメンション&#41; &#40;MDX&#41;](../mdx/count-dimension-mdx.md)|キューブ内のディメンション数を返します。|  
|[カウント&#40;階層レベル&#41; &#40;MDX&#41;](../mdx/count-hierarchy-levels-mdx.md)|ディメンション内または階層内のレベル数を返します。|  
|[カウント&#40;設定&#41; &#40;MDX&#41;](../mdx/count-set-mdx.md)|セット内のセル数を返します。|  
|[カウント&#40;組&#41; &#40;MDX&#41;](../mdx/count-tuple-mdx.md)|組内のディメンション数を返します。|  
|[共変性&#40;MDX&#41;](../mdx/covariance-mdx.md)|バイアスをかけた母集団の公式を使用して、セットに対して評価される 2 つの系列の母共分散を返します。|  
|[CovarianceN &#40;MDX&#41;](../mdx/covariancen-mdx.md)|バイアスをかけない母集団の公式を使用して、セットに対して評価される 2 つの系列のサンプル共分散を返します。|  
|[DistinctCount &#40;MDX&#41;](../mdx/distinctcount-mdx.md)|セット内の重複しない空以外の組の数を返します。|  
|[IIf &#40;MDX&#41;](../mdx/iif-mdx.md)|論理テストによって判別される 2 つの値の 1 つを返します。|  
|[LinRegIntercept &#40;MDX&#41;](../mdx/linregintercept-mdx.md)|セットの線型回帰を計算し、回帰直線の切片の値を返す y ax+b の a を = です。|  
|[LinRegPoint &#40;MDX&#41;](../mdx/linregpoint-mdx.md)|セットの線形回帰を計算しの値を返します*y*回帰直線 y ax+b の a を = です。|  
|[LinRegR2 &#40;MDX&#41;](../mdx/linregr2-mdx.md)|セットの線型回帰を計算し、決定係数 R2 を返します。|  
|[LinRegSlope &#40;MDX&#41;](../mdx/linregslope-mdx.md)|セットの線型回帰を計算し、回帰直線の傾きの値を返す y ax+b の a を = です。|  
|[LinRegVariance &#40;MDX&#41;](../mdx/linregvariance-mdx.md)|セットの線型回帰を計算し、回帰直線に関連付けられた変位を返します y ax+b の a を = です。|  
|[LookupCube &#40;MDX&#41;](../mdx/lookupcube-mdx.md)|同じデータベース内で別に指定されたキューブに対して評価される MDX 式の値を返します。|  
|[最大&#40;MDX&#41;](../mdx/max-mdx.md)|セットに対して評価される数値式の最大値を返します。|  
|[中央値&#40;MDX&#41;](../mdx/median-mdx.md)|セットに対して評価される数値式の中央値を返します。|  
|[Min &#40;MDX&#41;](../mdx/min-mdx.md)|セットに対して評価される数値式の最小値を返します。|  
|[序数&#40;MDX&#41;](../mdx/ordinal-mdx.md)|レベルに関連付けられた 0 から始まる序数値を返します。|  
|[予測&#40;MDX&#41;](../mdx/predict-mdx.md)|データ マイニング モデルに対して評価される数値式の値を返します。|  
|[ランク&#40;MDX&#41;](../mdx/rank-mdx.md)|指定したセット内の指定した組の 1 から始まる順位付けを返します。|  
|[RollupChildren &#40;MDX&#41;](../mdx/rollupchildren-mdx.md)|指定された単項演算子を使用して、指定されたメンバーの子メンバーの値をロール アップして生成した値を返します。|  
|[Stddev &#40;MDX&#41;](../mdx/stddev-mdx.md)|別名[Stdev &#40;MDX&#41;](../mdx/stdev-mdx.md)です。|  
|[StddevP &#40;MDX&#41;](../mdx/stddevp-mdx.md)|別名[StdevP &#40;MDX&#41;](../mdx/stdevp-mdx.md)です。|  
|[Stdev &#40;MDX&#41;](../mdx/stdev-mdx.md)|バイアスをかけない母集団の公式を使用して、セットに対して評価される数値式のサンプル標準偏差を返します。|  
|[StdevP &#40;MDX&#41;](../mdx/stdevp-mdx.md)|バイアスをかけた母集団の公式を使用して、セットに対して評価される数値式の母標準偏差を返します。|  
|[StrToValue &#40;MDX&#41;](../mdx/strtovalue-mdx.md)|MDX 形式の文字列によって指定されている値を返します。|  
|[合計&#40;MDX&#41;](../mdx/sum-mdx.md)|セットに対して評価される数値式の合計を返します。|  
|[値&#40;MDX&#41;](../mdx/value-mdx.md)|メジャーの値を返します。|  
|[Var &#40;MDX&#41;](../mdx/var-mdx.md)|バイアスをかけない母集団の公式を使用して、セットに対して評価される数値式のサンプル分散を返します。|  
|[分散&#40;MDX&#41;](../mdx/variance-mdx.md)|別名[Var &#40;MDX&#41;](../mdx/var-mdx.md)です。|  
|[VarianceP &#40;MDX&#41;](../mdx/variancep-mdx.md)|別名[VarP &#40;MDX&#41;](../mdx/varp-mdx.md)です。|  
|[VarP &#40;MDX&#41;](../mdx/varp-mdx.md)|バイアスをかけた母集団の公式を使用して、セットに対して評価される数値式の母分散を返します。|  
  
## <a name="set-functions"></a>集合関数  
  
|関数|Description|  
|--------------|-----------------|  
|[AddCalculatedMembers &#40;MDX&#41;](../mdx/addcalculatedmembers-mdx.md)|計算されるメンバーを指定されたセットに追加して生成したセットを返します。|  
|[AllMembers &#40;MDX&#41;](../mdx/allmembers-mdx.md)|指定されたディメンション、階層、レベルのすべてのメンバー (計算されるメンバーも含む) を含むセットを返します。|  
|[先祖&#40;MDX&#41;](../mdx/ancestors-mdx.md)|メンバーの先祖のうち、指定されたレベルまたは距離にあるすべての先祖のセットを返します。|  
|[先祖&#40;MDX&#41;](../mdx/ascendants-mdx.md)|指定されたメンバー自体も含めたメンバーの先祖のセットを返します。|  
|[軸&#40;MDX&#41;](../mdx/axis-mdx.md)|軸で定義されるセットを返します。|  
|[BottomCount &#40;MDX&#41;](../mdx/bottomcount-mdx.md)|セットを昇順に並べ替え、値の小さい方から指定された数の組を返します。|  
|[BottomPercent &#40;MDX&#41;](../mdx/bottompercent-mdx.md)|セットを昇順で並べ替え、累積合計が指定された割合以下になるように、値の小さい方から組のセットを作成して返します。|  
|[BottomSum &#40;MDX&#41;](../mdx/bottomsum-mdx.md)|セットを昇順で並べ替え、合計が指定された値以下になるように、値の小さい方から組のセットを作成して返します。|  
|[子&#40;MDX&#41;](../mdx/children-mdx.md)|指定されたメンバーの子メンバーを返します。|  
|[Crossjoin &#40;MDX&#41;](../mdx/crossjoin-mdx.md)|1 つ以上のセットのクロス積を返します。|  
|[CurrentOrdinal &#40;MDX&#41;](../mdx/currentordinal-mdx.md)|繰り返し処理中に、セット内の現在の繰り返し数を返します。|  
|[子孫&#40;MDX&#41;](../mdx/descendants-mdx.md)|メンバーの子孫のうち、指定されたレベルまたは距離にある子孫のセットを返します。他のレベルの子孫を含めたり除外したりすることも可能です。|  
|[Distinct &#40;MDX&#41;](../mdx/distinct-mdx.md)|指定されたセットから重複した組を削除して、セットを返します。|  
|[DrilldownLevel &#40;MDX&#41;](../mdx/drilldownlevel-mdx.md)|セットのメンバーを、そのセットの最下位レベルの 1 レベル下にドリル ダウンします。または、指定されたレベルの 1 レベル下にドリル ダウンします。|  
|[DrilldownLevelBottom &#40;MDX&#41;](../mdx/drilldownlevelbottom-mdx.md)|セットの最下位メンバーを、指定されたレベルから 1 レベル下にドリル ダウンします。|  
|[DrilldownLevelTop &#40;MDX&#41;](../mdx/drilldownleveltop-mdx.md)|セットの最上位メンバーを、指定されたレベルから 1 レベル下にドリル ダウンします。|  
|[DrilldownMember &#40;MDX&#41;](../mdx/drilldownmember-mdx.md)|2 番目に指定されたセット内に存在する、指定されたセットのメンバーをドリル ダウンします。 または、組のセットをドリル ダウンします。|  
|[DrilldownMemberBottom &#40;MDX&#41;](../mdx/drilldownmemberbottom-mdx.md)|2 番目に指定されたセット内に存在する、指定されたセットのメンバーをドリル ダウンします。結果セットは、指定された数のメンバーに限定されます。 また、この関数をドリル ダウン組のセット。|  
|[DrilldownMemberTop &#40;MDX&#41;](../mdx/drilldownmembertop-mdx.md)|2 番目に指定されたセット内に存在する、指定されたセットのメンバーをドリル ダウンします。結果セットは、指定された数のメンバーに限定されます。 または、この関数をドリル ダウン組のセットにします。|  
|[DrillupLevel &#40;MDX&#41;](../mdx/drilluplevel-mdx.md)|セットのメンバーのうち、指定されたレベルの下位に属するメンバーをドリル アップします。|  
|[DrillupMember &#40;MDX&#41;](../mdx/drillupmember-mdx.md)|2 番目に指定したセットに存在するメンバーを指定したセットにドリル アップします。|  
|[除く&#40;MDX&#41;](../mdx/except-mdx-function.md)|2 つのセットの差異を検出します。重複部分を保持することも可能です。|  
|[存在する&#40;MDX&#41;](../mdx/exists-mdx.md)|1 つのセットのメンバーのうち、他の 1 つ以上のセットの 1 つ以上の組に存在するメンバーのセットを返します。|  
|[抽出&#40;MDX&#41;](../mdx/extract-mdx.md)|抽出されたディメンション要素から組のセットを返します。|  
|[フィルター &#40;MDX&#41;](../mdx/filter-mdx.md)|指定されたセットを検索条件に基づいて絞り込み、結果セットを返します。|  
|[生成&#40;MDX&#41;](../mdx/generate-mdx.md)|あるセットを別のセットの各メンバーに適用し、その結果セットを和集合で結合します。 または、セットに対して文字列式を評価し、作成された連結文字列を返します。|  
|[Head &#40;MDX&#41;](../mdx/head-mdx.md)|セットの先頭から、指定された数の要素を返します (重複要素も保持します)。|  
|[Hierarchize &#40;MDX&#41;](../mdx/hierarchize-mdx.md)|セットのメンバーを階層化します。|  
|[Intersect &#40;MDX&#41;](../mdx/intersect-mdx.md)|指定された 2 つのセットの積集合を返します。重複部分を保持することも可能です。|  
|[LastPeriods &#40;MDX&#41;](../mdx/lastperiods-mdx.md)|指定されたメンバーを含む、指定されたメンバーまでのメンバーのセットを返します。|  
|[メンバー&#40;設定&#41; &#40;MDX&#41;](../mdx/members-set-mdx.md)|ディメンション、レベル、階層のメンバーのセットを返します。|  
|[Mtd &#40;MDX&#41;](../mdx/mtd-mdx.md)|時間ディメンションの年 (Year) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。|  
|[NameToSet &#40;MDX&#41;](../mdx/nametoset-mdx.md)|MDX 形式の文字列によって指定されているメンバーを含むセットを返します。|  
|[NonEmptyCrossjoin &#40;MDX&#41;](../mdx/nonemptycrossjoin-mdx.md)|1 つ以上のセットのクロス積を 1 つのセットとして返します。ただし、空の組と、ファクト テーブル データに関連付けられていない組は含まれません。|  
|[順序&#40;MDX&#41;](../mdx/order-mdx.md)|指定されたセットのメンバーを整列します。必要に応じて、階層を保持するか、解除するかを指定できます。|  
|[PeriodsToDate &#40;MDX&#41;](../mdx/periodstodate-mdx.md)|時間ディメンションで指定されているレベル内で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。|  
|[Qtd &#40;MDX&#41;](../mdx/qtd-mdx.md)|以降では最初の兄弟、制約の中で指定されたメンバーで終わると、特定のメンバーと同じレベルからメンバーの兄弟のセットを返します、*四半期*時間ディメンション内のレベルです。|  
|[兄弟&#40;MDX&#41;](../mdx/siblings-mdx.md)|指定されたメンバー自体を含めて、メンバーの兄弟を返します。|  
|[StripCalculatedMembers &#40;MDX&#41;](../mdx/stripcalculatedmembers-mdx.md)|計算されるメンバーを指定されたセットから削除して生成したセットを返します。|  
|[StrToSet &#40;MDX&#41;](../mdx/strtoset-mdx.md)|MDX 形式の文字列によって指定されているセットを返します。|  
|[サブセット&#40;MDX&#41;](../mdx/subset-mdx.md)|指定されたセットから、組のサブセットを返します。|  
|[末尾&#40;MDX&#41;](../mdx/tail-mdx.md)|セットの末尾からサブセットを返します。|  
|[ToggleDrillState &#40;MDX&#41;](../mdx/toggledrillstate-mdx.md)|メンバーのドリル状態を切り替えます。|  
|[TopCount &#40;MDX&#41;](../mdx/topcount-mdx.md)|セットを降順に並べ替え、値の大きい方から指定された数の要素を返します。|  
|[TopPercent &#40;MDX&#41;](../mdx/toppercent-mdx.md)|セットを降順で並べ替え、累積合計が指定された割合以下になるように、値の大きい方から組のセットを作成して返します。|  
|[TopSum &#40;MDX&#41;](../mdx/topsum-mdx.md)|セットを並べ替え、累積合計が指定された値以上になる最上位の要素を返します。|  
|[共用体&#40;MDX&#41;](../mdx/union-mdx.md)|2 つのセットの和集合を返します。重複部分を保持することもできます。|  
|[Unorder &#40;MDX&#41;](../mdx/unorder-mdx.md)|指定されたセットから適用済みの順序設定を解除します。|  
|[VisualTotals &#40;MDX&#41;](../mdx/visualtotals-mdx.md)|指定されたセットの子メンバーの合計を動的に算出することによって生成したセットを返します。結果のセル セットで親メンバーの名前のパターンを使用することも可能です。|  
|[Wtd &#40;MDX&#41;](../mdx/wtd-mdx.md)|時間ディメンションの週 (Week) レベルという制約の中で、指定されたメンバーと同じレベルにある兄弟メンバーのセットを返します。先頭は最初の兄弟、末尾は指定されたメンバーになります。|  
|[Ytd &#40;MDX&#41;](../mdx/ytd-mdx.md)|以降では最初の兄弟、制約の中で指定されたメンバーで終わると、特定のメンバーと同じレベルからメンバーの兄弟のセットを返します、*年*時間ディメンション内のレベルです。|  
  
## <a name="string-functions"></a>文字列関数  
  
|関数|Description|  
|--------------|-----------------|  
|[CalculationPassValue (MDX)](../mdx/calculationpassvalue-mdx.md)|キューブの指定された計算パスを評価し、MDX 式の値を返します。|  
|[CoalesceEmpty &#40;MDX&#41;](../mdx/coalesceempty-mdx.md)|空のセル値を数値または文字列に連結し、連結後の値を返します。|  
|[生成&#40;MDX&#41;](../mdx/generate-mdx.md)|あるセットを別のセットの各メンバーに適用し、その結果セットを和集合で結合します。 または、セットに対して文字列式を評価し、作成された連結文字列を返します。|  
|[IIf &#40;MDX&#41;](../mdx/iif-mdx.md)|論理テストによって判別される 2 つの値の 1 つを返します。|  
|[LookupCube &#40;MDX&#41;](../mdx/lookupcube-mdx.md)|同じデータベース内で別に指定されたキューブに対して評価される MDX 式の値を返します。|  
|[MemberToStr &#40;MDX&#41;](../mdx/membertostr-mdx.md)|指定されたメンバーに対応する MDX 形式の文字列を返します。|  
|[名前&#40;MDX&#41;](../mdx/name-mdx.md)|ディメンション、階層、レベル、メンバーの名前を返します。|  
|[プロパティ & #40 です。MDX と #41 です。](../mdx/properties-mdx.md)|メンバー プロパティ値を含む文字列または厳密に型指定された値を返します。|  
|[SetToStr &#40;MDX&#41;](../mdx/settostr-mdx.md)|指定されたセットに対応する MDX 形式の文字列を返します。|  
|[TupleToStr &#40;MDX&#41;](../mdx/tupletostr-mdx.md)|指定された組に対応する MDX 形式の文字列を返します。|  
|[UniqueName &#40;MDX&#41;](../mdx/uniquename-mdx.md)|指定されたディメンション、階層、レベル、メンバーの一意の名前を返します。|  
|[ユーザー名&#40;MDX&#41;](../mdx/username-mdx.md)|現在の接続のドメイン名とユーザー名を返します。|  
  
## <a name="subcube-functions"></a>サブキューブ関数  
  
|関数|Description|  
|--------------|-----------------|  
|[これと #40 です。MDX と #41 です。](../mdx/this-mdx.md)|現在のサブキューブを返します。|  
|[まま&#40;MDX&#41;](../mdx/leaves-mdx.md)|指定されたディメンション、メンバー、組のリーフ メンバーのセットを返します。|  
  
## <a name="tuple-functions"></a>組関数  
  
|関数|Description|  
|--------------|-----------------|  
|[現在&#40;MDX&#41;](../mdx/current-mdx.md)|繰り返し処理の実行時に、セットから現在の組を返します。|  
|[項目&#40;組&#41; &#40;MDX&#41;](../mdx/item-tuple-mdx.md)|セットから組を返します。|  
|[ルート&#40;MDX&#41;](../mdx/root-mdx.md)|構成される組を返します、**すべて**キューブ、ディメンション、または組内の各属性階層のメンバーです。|  
|[StrToTuple &#40;MDX&#41;](../mdx/strtotuple-mdx.md)|MDX 形式の文字列によって指定されている組を返します。|  
  
## <a name="other-functions"></a>その他の関数  
  
|関数|Description|  
|--------------|-----------------|  
|[エラー &#40;MDX&#41;](../mdx/error-mdx.md)|エラーを発生させます。指定されたエラー メッセージを示すこともできます。|  
  
## <a name="see-also"></a>参照  
 [MDX 言語リファレンス & #40 です。MDX と #41 です。](../mdx/mdx-language-reference-mdx.md)  
  
  

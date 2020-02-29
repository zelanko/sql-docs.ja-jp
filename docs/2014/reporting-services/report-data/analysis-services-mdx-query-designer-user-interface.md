---
title: Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10012"
- sql12.rtp.rptdesigner.dataview.asquerydesigner.f1
helpviewer_keywords:
- MDX [Reporting Services], creating datasets
- query designers [Reporting Services]
ms.assetid: d9c7c0b3-fce4-4a65-b679-408273e6a925
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: c7f4f40fb819cd9686039d7df8f73c5d7ac96c2b
ms.sourcegitcommit: 2d4067fc7f2157d10a526dcaa5d67948581ee49e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/28/2020
ms.locfileid: "78173222"
---
# <a name="analysis-services-mdx-query-designer-user-interface"></a>Analysis Services の MDX クエリ デザイナーのユーザー インターフェイス
  [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] には、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ ソースに対する多次元式 (MDX) クエリやデータ マイニング式 (DMX) クエリを作成するためのグラフィカル クエリ デザイナーが用意されています。 このトピックでは、MDX クエリ デザイナーについて説明します。 DMX クエリ デザイナーの詳細については、「 [DMX のための Analysis Services の接続の種類 &#40;SSRS&#41;](analysis-services-connection-type-for-dmx-ssrs.md)」をご覧ください。

 MDX のグラフィカル クエリ デザイナーには、デザイン モードとクエリ モードという 2 つのモードがあります。 どちらのモードにもメタデータ ペインが表示され、選択したキューブからメンバーをドラッグすることによって MDX クエリを作成できます。レポートの処理時には、このクエリに基づいてデータが取得されます。

> [!IMPORTANT]
>  ユーザーは、クエリを作成して実行する際にデータ ソースにアクセスします。 したがって、データ ソースに対する最小限の権限 (読み取り専用権限など) を付与する必要があります。

## <a name="graphical-mdx-query-designer-in-design-mode"></a>グラフィカル MDX クエリ デザイナー (デザイン モード)
 レポート データセットの MDX クエリを編集する場合、グラフィカル MDX クエリ デザイナーがデザイン モードで開きます。

 次の図は、デザイン モードで表示される各ペインの名称を示しています。

 ![Analysis Services MDX クエリ デザイナー、デザイン ビュー](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqd-dsawas-mdx-designmode.gif "Analysis Services MDX クエリ デザイナー、デザイン ビュー")

 このモードのペインの一覧を次の表に示します。

|ペイン|Function|
|----------|--------------|
|キューブの選択ボタン (**[...]**)|現在選択されているキューブを表示します。|
|メタデータ ペイン|選択されたキューブで定義されているメジャー、主要業績評価指標 (KPI)、およびディメンションの階層リストを表示します。|
|計算されるメンバー ペイン|現在定義されている、クエリに使用することのできる計算されるメンバーを表示します。|
|フィルター ペイン|ディメンションおよび関連する階層を選択することにより、ソースのデータをフィルター処理し、レポートに返されるデータを制限できます。|
|データ ペイン|メタデータ ペインや計算されるメンバー ペインからアイテムをドラッグすると、結果セットの列見出しが表示されます。 
  **[自動実行]** ボタンが選択されている場合、結果セットは自動的に更新されます。 .|

 データ ペインには、メタデータ ペインからディメンション、メジャー、KPI をドラッグしたり、計算されるメンバー ペインから計算されるメンバーをドラッグしたりできます。 フィルター ペインでは、ディメンションや関連する階層を選択し、フィルター式を設定することによって、クエリに利用可能なデータを制限できます。 ツールバーの [**自動実行**] ([![クエリの自動実行](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-autoexecute.gif "クエリの自動実行")]) 切り替えボタンが選択されている場合、データペインにメタデータオブジェクトをドロップするたびにクエリが実行されます。 ツールバーの [**実行**] ([![クエリの実行](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-run.gif "クエリの実行")]) ボタンを使用して、手動でクエリを実行できます。

 このモードで MDX クエリを作成すると、次のような追加のプロパティがクエリに自動的に追加されます。

 **メンバーのプロパティ**MEMBER_CAPTION、MEMBER_UNIQUE_NAME

 **セルのプロパティ**VALUE、BACK_COLOR、FORE_COLOR、FORMATTED_VALUE、FORMAT_STRING、FONT_NAME、FONT_SIZE、FONT_FLAGS

 独自の追加プロパティを指定するには、クエリ モードで MDX クエリを手動で編集する必要があります。

### <a name="graphical-mdx-query-designer-toolbar-in-design-mode"></a>グラフィカル MDX クエリ デザイナーのツール バー (デザイン モード)
 クエリ デザイナーのツール バーにある各種のボタンを使用すると、グラフィカル インターフェイスを使用して MDX クエリをデザインできます。 これらのボタンとその機能を次の表に示します。

|ボタン|説明|
|------------|-----------------|
|**テキストとして編集**|このデータ ソースの種類では使用できません。|
|**[インポート]**|ファイル システムのレポート定義 (.rdl) ファイルから既存のクエリをインポートします。 詳細については、「 [レポート埋め込みデータセットと共有データセット &#40;レポート ビルダーおよび SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)と呼ばれます。|
|![MDX クエリ ビューへの変更](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-commandtypemdx.gif "MDX クエリ ビューへの変更")|コマンドの種類を MDX に切り替えます。|
|![DMX クエリ言語ビューへの変更](../media/rsqdicon-commandtypedmx.gif "DMX クエリ言語ビューへの変更")|コマンドの種類を DMX に切り替えます。|
|![結果データの更新](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-refresh.gif "結果データの更新")|データ ソースからメタデータを更新します。|
|![[計算されるメンバーの追加]](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-addcalculatedmember.gif "[計算されるメンバーの追加]")|
  **[計算されるメンバー ビルダー]** ダイアログ ボックスを表示します。|
|![空のセルの表示/非表示の切り替え](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-showemptycells.gif "空のセルの表示/非表示の切り替え")|データ ペインに空のセルを表示するかどうかを切り替えます。 これは、MDX で NON EMPTY 句を使用することに相当します。|
|![クエリの自動実行](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-autoexecute.gif "クエリの自動実行")|クエリを自動的に実行し、変更が生じるたびに結果を表示します。 結果はデータ ペインに表示されます。|
|![[集計の表示] ボタン](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-showaggregations.gif "[集計の表示] ボタン")|集計をデータ ペインに表示します。|
|![デリート](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-delete.gif "削除")|データ ペインで選択した列をクエリから削除します。|
|![[クエリ パラメーター] ダイアログ ボックスのアイコン](https://docs.microsoft.com/analysis-services/analysis-services/media/iconqueryparameter.gif "[クエリ パラメーター] ダイアログ ボックスのアイコン")|
  **[クエリ パラメーター]** ダイアログ ボックスを表示します。 クエリ パラメーターの値を指定する場合、同じ名前のレポート パラメーターが自動的に作成されます。 クエリ パラメーターの値は、このレポート パラメーターを参照する式に設定されます。|
|![[クエリの準備] ボタン](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-preparequery.gif "[クエリの準備] ボタン")|クエリを準備します。|
|![クエリを実行する](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-run.gif "クエリの実行")|クエリを実行し、結果をデータ ペインに表示します。|
|![クエリをキャンセルする](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-cancel.gif "クエリのキャンセル")|クエリを取り消します。|
|![デザインモードへの切り替え](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-designmode.gif "デザイン モードに切り替える")|デザイン モードとクエリ モードを切り替えます。|

## <a name="graphical-mdx-query-designer-in-query-mode"></a>グラフィカル MDX クエリ デザイナー (クエリ モード)
 グラフィカル クエリ デザイナーを **クエリ** モードに変更するには、ツール バーの **[デザイン モード]** ボタンをクリックします。

 次の図は、クエリ モードで表示される各ペインの名称を示しています。

 ![Analysis Services MDX クエリ デザイナー、クエリ ビュー](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqd-dsawas-mdx-querymode.gif "Analysis Services MDX クエリ デザイナー、クエリ ビュー")

 このモードのペインの一覧を次の表に示します。

|ペイン|Function|
|----------|--------------|
|キューブの選択ボタン (**[...]**)|現在選択されているキューブを表示します。|
|メタデータ/関数/テンプレート ペイン|選択されたキューブで定義されているメジャー、KPI、およびディメンションの階層リストを表示します。|
|クエリ ペイン|クエリ テキストを表示します。|
|結果ペイン|クエリの実行結果を表示します。|

 メタデータ ペインには、 **[メタデータ]**、 **[関数]**、 **[テンプレート]** の各タブが表示されます。 
  **[メタデータ]** タブからは、ディメンション、階層、KPI、およびメジャーを MDX クエリ ペインにドラッグできます。 
  **[関数]** タブからは、関数を MDX クエリ ペインにドラッグできます。 
  **[テンプレート]** タブからは、MDX テンプレートを MDX クエリ ペインに追加できます。 クエリを実行すると、結果ペインに MDX クエリの結果が表示されます。

 デザイン モードで生成された既定の MDX クエリを拡張し、その他のメンバー プロパティおよびセル プロパティを追加できます。 このクエリを実行すると、その値は結果セットに表示されません。 ただし、値が [!INCLUDE[ssRSnoversion](../../../includes/ssrsnoversion-md.md)] に戻され、これらの値をレポートで使用できます。 詳細については、「Analysis Services データベースに対する拡張フィールド プロパティ (SSRS)」を参照してください。

### <a name="graphical-query-designer-toolbar-in-query-mode"></a>グラフィカル クエリ デザイナーのツール バー (クエリ モード)
 クエリ デザイナーのツール バーにある各種のボタンを使用すると、グラフィカル インターフェイスを使用して MDX クエリをデザインできます。

 デザイン モードでもクエリ モードでも、表示されるツール バー ボタンは同じです。ただし、クエリ モードでは、次のボタンが無効になります。

-   **テキストとして編集**

-   **計算されるメンバーの追加**(![計算されるメンバーの追加](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-addcalculatedmember.gif "[計算されるメンバーの追加]"))

-   **空のセルを表示**する (![空のセルを表示](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-showemptycells.gif "空のセルの表示/非表示の切り替え"))

-   **Autoexecute** (![クエリの自動実行](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-autoexecute.gif "クエリの自動実行"))

-   [**集計の表示**![] ([集計の表示] ボタン](https://docs.microsoft.com/analysis-services/analysis-services/media/rsqdicon-showaggregations.gif "[集計の表示] ボタン"))

## <a name="see-also"></a>参照
 [Analysis Services レポートビルダー &#40;の MDX クエリデザイナーでのパラメーターの定義&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md) [共有データセットまたは埋め込みデータセットの作成 &#40;レポートビルダーと ssrs](create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)&#41;Analysis Services[の接続の種類 DMX &#40;Ssrs&#41;](analysis-services-connection-type-for-dmx-ssrs.md) [rsreportdesigner 構成ファイル](../report-server/rsreportdesigner-configuration-file.md) [Analysis Services MDX &#40;の接続の種類](analysis-services-connection-type-for-mdx-ssrs.md)&#41;



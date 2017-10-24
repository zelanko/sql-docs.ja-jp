---
title: "多次元モデル (Analysis Services) での翻訳 |Microsoft ドキュメント"
ms.custom:
- SQL2016_New_Updated
ms.date: 03/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.asvs.dimensiondesigner.deletelanguagefirm.f1
ms.assetid: 5521f8ef-b10a-4861-9df7-1e43e0a1fb3f
caps.latest.revision: 11
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 87f826e36a3fb58cfb1adba2b30a1375e3b84e71
ms.contentlocale: ja-jp
ms.lasthandoff: 09/01/2017

---
# <a name="translations-in-multidimensional-models-analysis-services"></a>多次元モデルの翻訳 (Analysis Services)
  [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] で翻訳を定義するには、翻訳対象の [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトに適したデザイナーを使用します。 翻訳を定義すると、該当する **オブジェクトに関連付けられた** Translation [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトが作成されます。この Translation オブジェクトには、関連付けられた [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのプロパティに対応する、指定した言語の明示的なリテラル値が含まれています。  
  
## <a name="elements-of-a-multi-lingual-data-model"></a>多言語データ モデルの要素  
 多言語ソリューションで使用するデータ モデルには、単にラベル (フィールド名と説明) を翻訳する以上の処置が必要になります。 また、さまざまな言語スクリプトで表記したデータ値を提供する必要もあります。 多言語ソリューションを実現するには、個々の属性に外部データベース内の列をバインドし、データを取得する必要があります。  
  
 Adventure Works サンプル データベース (多次元かつリレーショナルなデータ ウェアハウス) は、Analysis Services の翻訳機能の例を示しています。 このサンプル モデルには、翻訳されたキャプションと説明が含まれています。 サンプルのリレーショナル データ ウェアハウスに含まれる翻訳した値の列が、モデル内のローカライズされた属性メンバーを提供します。  
  
 モデルで使用できる翻訳されたデータ値を表示するには、次の手順を実行します。  
  
1.  デザイナーで、Adventure Works 多次元モデルを開きます。  
  
2.  ソリューション エクスプ ローラーで、データ ソース ビューを開くし、Adventure Works DW をダブルクリック\<バージョン > .dsv です。  
  
3.  dimDate、dimProduct、dimProductCategory、または dimProductSubcateogry を検索します。 これらのすべてのディメンションには、月、曜日、製品名、カテゴリ名などの、翻訳されたメンバーの属性が含まれています。  
  
4.  任意のフィールドを右クリックし、 **[データの探索]**を選択します。 各メンバーの英語、スペイン語、およびフランス語の翻訳が表示されます。  
  
 日付、時刻、通貨の形式は、翻訳を通じては実装されません。 クライアントのロケールに基づいてカルチャに固有の形式を動的に提供するには、通貨変換ウィザードと **FormatString** プロパティを使用します。 「[通貨換算 (Analysis Services)](../../analysis-services/currency-conversions-analysis-services.md)」および「[FormatString 要素 (ASSL)](../../analysis-services/scripting/properties/formatstring-element-assl.md)」をご覧ください。  
  
 Analysis Services のチュートリアルの「[Lesson 9: Defining Perspectives and Translations](../../analysis-services/lesson-9-defining-perspectives-and-translations.md) 」では、翻訳を作成してテストする手順について説明しています。  
  
## <a name="defining-translations"></a>翻訳の定義  
  
### <a name="add-translations-to-a-cube"></a>キューブに翻訳を追加する  
 翻訳は、キューブ、メジャー グループ、メジャー、キューブ ディメンション、パースペクティブ、KPI、アクション、名前付きセット、および計算されるメンバーに追加できます。  
  
1.  ソリューション エクスプローラーで、キューブ名をダブルクリックして、キューブ デザイナーを開きます。  
  
2.  **[翻訳]** タブをクリックします。翻訳をサポートするすべてのオブジェクトが、このページに表示されます。  
  
3.  各オブジェクトについて、対象言語 (内部で LCID に解決される)、キャプションの翻訳、および説明の翻訳を指定します。 Management Studio でサーバーの言語を設定したとしても、1 つの属性に対して翻訳のオーバーライドを追加したとしても、言語の一覧は Analysis Services 全体で一貫性が保たれます。  
  
     照合順序は変更できないことに注意してください。 キャプションの翻訳によって複数の言語をサポートしている場合でも、1 つのキューブは基本的に 1 つの照合順序を使用します (この後説明するとおり、ディメンションの属性は例外)。 照合順序を共有している場合に言語が正しく並べ替えられない場合は、照合順序の要件に対応するためにキューブのコピーを作成する必要があるかもしれません。  
  
4.  プロジェクトをビルドし、配置します。  
  
5.  Excel などのクライアント アプリケーションを使用してデータベースに接続し、ロケール識別子を使用するように接続文字列を変更します。 詳細については、「[グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)」をご覧ください。  
  
### <a name="add-translations-to-a-dimension-and-attributes"></a>ディメンションおよび属性に翻訳を追加する  
 翻訳は、データベース ディメンション、属性、階層、および階層内のレベルに追加できます。  
  
 翻訳されたキャプションは、キーボードまたはコピー/貼り付けを使用して手動でモデルに追加しますが、ディメンションの属性メンバーについては、翻訳された値を外部データベースから取得できます。 具体的には、属性の **CaptionColumn** プロパティをデータ ソース ビューの列にバインドできます。  
  
 照合順序の設定は、属性レベルでオーバーライドできます。たとえば、特定の属性について文字幅の区別で調整したり、バイナリ並べ替えを使用したりできます。 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]では、データ バインドが定義されている場所で照合順序が公開されます。 ディメンション属性の翻訳は DSV 内の別のソース列にバインドするので、ソース列で使用する照合順序を指定できるように、照合順序の設定が可能になっています。 リレーショナル データベース内の列の照合順序について詳しくは、「 [Set or Change the Column Collation](../../relational-databases/collations/set-or-change-the-column-collation.md) 」を参照してください。  
  
1.  ソリューション エクスプローラーで、ディメンション名をダブルクリックして、ディメンション デザイナーを開きます。  
  
2.  **[翻訳]** タブをクリックします。翻訳をサポートするすべてのディメンション オブジェクトが、このページに表示されます。  
  
     各オブジェクトについて、対象言語 (LCID に解決される)、キャプションの翻訳、および説明の翻訳を指定します。 Management Studio でサーバーの言語を設定したとしても、1 つの属性に対して翻訳のオーバーライドを追加したとしても、言語の一覧は Analysis Services 全体で一貫性が保たれます。  
  
3.  翻訳した値を提供する列に属性をバインドするには、次の手順を実行します。  
  
    1.  ディメンション デザイナーの **[翻訳]**タブを表示した状態のまま、新しい翻訳を追加します。 言語を選択します。 ページに新しい列が表示され、翻訳した値を入力できます。  
  
    2.  属性のいずれかに隣接する空のセルにカーソルを置きます。 属性をキーにすることはできませんが、その他のすべての属性は有効な選択肢です。 ドットが表示された小さいボタンが表示されているはずです。 そのボタンをクリックして、 **[属性データの翻訳]**ダイアログ ボックスを開きます。  
  
    3.  キャプションの翻訳を入力します。 これは、対象言語のデータのラベルとして使用されます。たとえば、ピボット テーブルのフィールド一覧のフィールド名です。  
  
    4.  属性メンバーの翻訳済みの値を提供するソース列を選択します。 ディメンションにバインドされたテーブルまたはクエリ内の既存の列のみ使用できます。 列が存在しない場合は、データ ソース ビュー、ディメンション、およびキューブを変更して列を選択する必要があります。  
  
    5.  該当する場合は、照合順序と並べ替えの順序を選択します。  
  
4.  プロジェクトをビルドし、配置します。  
  
5.  Excel などのクライアント アプリケーションを使用してデータベースに接続し、ロケール識別子を使用するように接続文字列を変更します。 詳細については、「[グローバリゼーションのヒントとベスト プラクティス (Analysis Services)](../../analysis-services/globalization-tips-and-best-practices-analysis-services.md)」をご覧ください。  
  
### <a name="add-a-translation-of-the-database-name"></a>データベース名の翻訳を追加する  
 データベース レベルでは、データベースの名前と説明に翻訳を追加できます。 翻訳されたデータベース名は、言語の LCID を指定するクライアント接続に表示されますが、ツールによっては表示されないことがあります。 たとえば、Management Studio でデータベースを表示する場合は、接続のロケール識別子を指定しても翻訳済みの名前は表示されません。 Management Studio で Analysis Services の接続に使用される API は、 **Language** プロパティを読み取りません。  
  
1.  ソリューション エクスプローラーで、プロジェクト名を右クリックし、 **[データベースの編集]** を選択して、データベース デザイナーを開きます。  
  
2.  [翻訳] 内で、対象言語 (LCID に解決される)、キャプションの翻訳、および説明の翻訳を指定します。 Management Studio でサーバーの言語を設定したとしても、1 つの属性に対して翻訳のオーバーライドを追加したとしても、言語の一覧は Analysis Services 全体で一貫性が保たれます。  
  
3.  データベースの [プロパティ] ページで、翻訳に対して指定したのと同じ LCID を **Language** に設定します。 必要であれば、 **Collation** にも値を設定します (既定値が意味をなさなくなった場合)。  
  
4.  データベースをビルドして配置します。  
  
## <a name="deleting-translation-objects"></a>翻訳オブジェクトの削除  
 ディメンションまたはキューブ デザイナーで、完全に削除する翻訳オブジェクトを右クリックします。 削除したオブジェクトは復元および再利用ができないので、続行する前に、影響を受けるオブジェクトの一覧を確認してください。  
  
## <a name="resolving-translations"></a>翻訳の解決  
 クライアント アプリケーションが、指定された言語識別子内の情報を要求すると、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] インスタンスは、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのデータおよびメタデータを、最も近い言語識別子に解決しようとします。 クライアント アプリケーションで既定の言語が指定されていない場合、ニュートラルなロケール識別子 (0) が指定されている場合、または既定の言語識別子 (1024) が処理される場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はインスタンスの既定の言語を使用して [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] オブジェクトのデータおよびメタデータを返します。  
  
 クライアント アプリケーションで既定の言語識別子以外の言語識別子が指定されている場合、インスタンスはすべての使用可能なオブジェクトに対して、可能なすべての翻訳を反復処理します。 指定された言語識別子が翻訳の言語識別子と一致した場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] はその翻訳を返します。 一致する言語識別子が見つからない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は次のいずれかの方法を使用して、指定された言語識別子に最も近い言語識別子を持つ翻訳を返します。  
  
-   次の言語識別子については、指定された言語識別子の翻訳が定義されていない場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は代替言語識別子の使用を試みます。  
  
    |指定された言語識別子|代替言語識別子|  
    |-----------------------------------|-----------------------------------|  
    |3076 - 中国語 (中華人民共和国香港特別行政区)|1028 - 中国語 (台湾)|  
    |5124 - 中国語 (中華人民共和国マカオ特別行政区)|1028 - 中国語 (台湾)|  
    |1028 - 中国語 (台湾)|既定の言語|  
    |4100 - 中国語 (シンガポール)|2052 - 中国語 (中華人民共和国)|  
    |2074 - クロアチア語|既定の言語|  
    |3098 - クロアチア語 (キリル文字)|既定の言語|  
  
-   他のすべての言語識別子の場合、 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] は、指定された言語識別子の第一言語を抽出し、Windows によって指示された言語識別子を第一言語に最適なものとして取得します。 最適な言語識別子の翻訳が見つからない場合や、指定された言語識別子が第一言語に最適なものである場合は、既定の言語が使用されます。  
  
## <a name="see-also"></a>参照  
 [Analysis Services のグローバリゼーションのシナリオ](../../analysis-services/globalization-scenarios-for-analysis-services.md)   
 [言語および照合順序と #40 です。Analysis Services &#41;](../../analysis-services/languages-and-collations-analysis-services.md)  
  
  


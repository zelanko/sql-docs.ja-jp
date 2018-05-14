---
title: CSDLBI の概念 |Microsoft ドキュメント
ms.date: 05/07/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: tabular-models
ms.topic: reference
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 99d7461164bb6d73a0577b817c2f9317889d348d
ms.sourcegitcommit: c12a7416d1996a3bcce3ebf4a3c9abe61b02fb9e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/10/2018
---
# <a name="csdlbi-concepts"></a>CSDLBI の概念
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]
  BI 注釈付き概念スキーマ定義言語 (CSDLBI) は、さまざまなデータセットにプログラムでアクセスしてクエリやエクスポートを実行できるように各種のデータを抽象的に表す、Entity Data Framework に基づく言語です。 CSDLBI はリッチ形式でデータ ドリブンのレポートとアプリケーションをサポートしているため、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] を使用して作成されたデータ モデルを表すために CSDLBI が使用されます。  
  
 このセクションでは、CSDLBI 表現と [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] データ モデルをマップする方法 (テーブルと多次元の両方) を、各モデルの種類の例と共に説明します。  
  
 これらの概念を示すために、Codeplex から入手できる AdventureWorks サンプル データベースの例を使用しています。 サンプルの詳細については、次を参照してください。 [for SQL Server の Adventure Works サンプル](http://go.microsoft.com/fwlink/?linkID=220093)です。  
  
## <a name="structure-of-a-tabular-model-in-csdlbi"></a>CSDLBI のテーブル モデルの構造  
 レポート モデルとそのデータを記述する CSDLBI ドキュメントでは、最初に xsd ステートメントを記述し、その後にモデルの定義を記述します。  
  
 モデルは名前空間として定義されます。主なエンティティ、アソシエーション、およびプロパティを次に示します。  
  
-   **EntityContainer**モデル内のテーブルを一覧表示します。  
  
-   各テーブルが記載されている、 **EntityContainer**として、 **EntitySet**です。  
  
-   2 つのテーブル間のリレーションシップごとの説明として、 **AssociationSet**リレーションシップのエンドポイントとの関係のロールを定義します。  
  
-   **EntityType**要素は、テーブルとは、並べ替えのプロパティを含む列についての詳細を提供し、表示目的に BISM 向けに拡張されています。  
  
-   **メジャー**要素は、モデルのために使用できる計算を定義します。 新しいを使用して、特殊な表示の属性のセットを追加することでメジャーを KPI に変換することができます**KPI**要素。  
  
-   パースペクティブの表現はありません。 フラグが CSDL に列と、パースペクティブに含まれていないテーブルがある、 **Hidden**属性。  
  
### <a name="entities-entitysets-and-entitytypes"></a>Entity、EntitySet、および Entitytype  
 Entity Data Framework のエンティティの表記が拡張され、データ モデルの列やテーブルを表現できるようになっています。 次の抜粋は、一覧表示**EntitySet**単純な内の要素を含む 3 つだけテーブルをモデル化します。  
  
```  
<EntityContainer Name="SimpleModel">  
<EntitySet Name="DimCustomer"EntityType="SimpleModel.DimCustomer">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimDate" EntityType="SimpleModel.DimDate">  
     <bi:EntitySet />  
   </EntitySet>  
<EntitySet Name="DimGeography" EntityType="SimpleModel.DimGeography">  
     <bi:EntitySet />  
   </EntitySet> />  
  
```  
  
 **EntitySet**列またはテーブル内のデータに関する情報は含まれません。 列とそのプロパティの詳細な記述は、EntityType 要素で提供されます。  
  
 **EntitySet**各エンティティ (テーブル) の要素には、キー列、データ型および列で null 許容属性、並べ替えの動作の長さを定義するなどのプロパティのコレクションが含まれています。 たとえば、次の CSDL は、Customer テーブルの 3 つの列の記述部分を抜粋したものです。 最初の列は、モデルの内部で使用される特殊な非表示の列です。  
  
```  
<EntityType Name="Customer">  
  <Key>  
     <PropertyRef Name="RowNumber" />  
  </Key>  
    <Property Name="RowNumber" Type="Int64" Nullable="false">  
     <bi:Property Hidden="true" Contents="RowNumber"  
       Stability="RowNumber" />  
    </Property>  
    <Property Name="CustomerKey" Type="Int64" Nullable="false">  
      <bi:Property />  
    </Property>  
     <Property Name="FirstName" Type="String" MaxLength="Max" FixedLength="false">  
       <bi:Property />  
      </Property>  
  
```  
  
 生成される CSDLBI ドキュメントのサイズを制限するためエンティティで複数回使用されるプロパティが指定されて、既存のプロパティへの参照によってプロパティは、の 1 回だけ表示されます。 必要があるように、 **EntityType**です。 クライアント アプリケーションは、検索してプロパティの値を取得することができます、 **EntityType**に一致する、 **OriginEntityType**です。  
  
### <a name="relationships"></a>リレーションシップ  
 として Entity Data Framework でのリレーションシップが定義されている*アソシエーション*エンティティの間です。  
  
 アソシエーションには必ず 2 つのエンド ポイントがあり、それぞれがテーブルのフィールドまたは列を参照します。 したがって、リレーションシップのエンド ポイントが異なれば、2 つのテーブル間に複数のリレーションシップを定義することができます。 アソシエーションのエンド ポイントにはロール名が割り当てられます。このロール名は、データ モデルのコンテキストにおけるアソシエーションの用途を示します。 ロール名の例があります**ShipTo**Orders テーブルに顧客 ID に関連する顧客 ID に適用される場合、します。  
  
 モデルの CSDLBI 表現には、エンティティがの観点で相互にどのようにマップされる方法を決定するのに関連付けられている属性も含まれています、*多重度*アソシエーションのです。 複数要素の接続性は、テーブル間のリレーションシップのエンド ポイントの属性または列がリレーションシップの "一" 側か "多" 側かを示します。 一対一のリレーションシップを表す値はありません。 CSDLBI 注釈でサポートされる複数要素の接続性の値は、エンティティが他のエンティティと関連付けられていないことを示す 0 と、一対一のリレーションシップまたは一対多のリレーションシップであることを示す 0..1 です。  
  
 次のサンプルは、列 DateAlternateKey で結合された Date および ProductInventory という 2 つのテーブルのリレーションシップの CSDLBI 出力を示しています。 既定の名前でいることを確認、 **AssociationSet**リレーションシップに関係する列の完全修飾の名前を指定します。 ただし、モデルのデザイン時にこの動作を変更すれば、別の名前付け形式を使用できます。  
  
```  
<AssociationSet Name="ProductInventory_Date_DateKey" Association="Model.ProductInventory_Date_DateKey">  
              <End EntitySet="ProductInventory" />  
              <End EntitySet="Date" />  
              <bi:AssociationSet />  
            </AssociationSet>  
  
```  
  
### <a name="visualization-and-navigation-properties"></a>視覚エフェクトとナビゲーション プロパティ  
 CSDLBI 注釈で重要なものに、レポート層での表示を定義するためのプロパティと、エンティティ間のリレーションシップをナビゲートするためのプロパティがあります。 通常、データ モデルを作成する際に、データの順序やグループ化の方法を制御したり既定値を決めたりすることはそれほど重要視されません。これは、順序などの表示に関する詳細はクライアント アプリケーションで指定されると想定されるためです。 ただし、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のテーブル モデルは [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] レポート クライアントと統合できる設計になっており、レポート デザイン画面でのデータ モデルのエンティティの表示をサポートするプロパティと属性が用意されています。  
  
 視覚化についての拡張機能には、数値データで使用する既定の集計を指定するための属性、テキスト フィールドが画像の URL を指すことを示すための属性、現在のフィールドの並べ替えに使用するフィールドを指定するための属性などがあります。  
  
### <a name="name-properties-and-naming-conventions"></a>名前のプロパティと名前付け規則  
 CSDLBI スキーマでは、キーとして使用できる一意の名前と識別子を各エンティティに割り当てるように規定されています。 また、一部のエンティティには、表示目的で使用されるキャプションや、エンティティの使用場所によって変化するコンテキスト名を指定できます。  
  
 **ドキュメント**要素は、ビジネス ユーザーが、データの意味を理解するため、エンティティの説明を提供する、レポート デザイナーの機会を提供します。 一部のエンティティは、1 つまたは複数にも許可**注釈**属性で、アプリケーション、またはクライアントで使用するため追加のメタデータを提供します。  
  
 [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] ツールでモデルを生成すると、オブジェクトの名前付けと名前の一意性に関する [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] の規則に従ってオブジェクトの名前が作成されます。 ただし、CSDLBI は Entity Data Framework (EDF) に基づくため、C# の識別子に関する規則に従って名前を付ける必要があります。そのため、モデルの CSDLBI 出力をサーバーで作成するときに、[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] のスキーマ内で使用されている名前が取得され、EDF の要件を満たす新しいオブジェクト名が自動的に作成されます。 次の表に、新しい名前が生成されるときの処理を示します。  
  
|Rule|操作|  
|----------|------------|  
|禁止されている文字を使用しない|禁止されている文字は、アンダースコアに置き換えられます。|  
|名前は一意でなければならない|同じ文字列が 2 つある場合は、一意にするために、どちらかにアンダースコアと数値が追加されます。|  
  
> [!WARNING]  
>  キャプションと修飾子の両方に翻訳があります。特定の言語では、どちらか一方だけの場合もあります。 つまり、修飾子と名前または修飾子とキャプションを連結した場合、文字列が 2 種類の言語で示されることがあります。  
  
## <a name="additions-to-support-multidimensional-models"></a>多次元モデルをサポートするための追加事項  
 CSDLBI 注釈の Version 1.0 ではテーブル モデルのみがサポートされていました。 Version 1.1 では、従来の BI 開発ツールを使用して作成された多次元モデル (OLAP キューブ) もサポートされます。 その結果、多次元モデルに XML 要求を実行して、レポートで使用するためのモデルの CSDLBI 定義を受信できます。  
  
 **キューブ:** SQL Server[!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)]表形式データベースは 1 つのモードを含めることができます。 一方、多次元データベースには複数のキューブを含めることができ、各データベースは既定のキューブに関連付けられます。 したがって、XML 要求を多次元サーバーに対して実行する場合は、キューブを指定する必要があり、キューブを指定しないと、既定のキューブに対する XML が返されます。  
  
 その場合、キューブの表現はテーブル モデル データベースによく似ています。 キューブ名とキューブが、表形式のデータベース名とデータベース識別子に対応します。  
  
 **ディメンション:** ディメンションは列やプロパティを持つエンティティ (テーブル) として CSDLBI で表されます。 パースペクティブに含まれていない場合でも、モデルに含まれているディメンションとしてマークされて CSDL 出力で表現することに注意してください**Hidden**です。  
  
 **パースペクティブ:** クライアントは個々 のパースペクティブに対する CSDL を要求することができます。 詳細については、次を参照してください。 [DISCOVER_CSDL_METADATA 行セット](../../analysis-services/schema-rowsets/xml/discover-csdl-metadata-rowset.md)です。  
  
 **階層:** 階層がサポートされているし、一連のレベルとして CSDLBI で表現します。  
  
 **メンバー:** サポート、既定のメンバーが追加され、既定値は、CSDLBI 出力に自動的に追加します。  
  
 **計算されるメンバー:** 多次元モデルの子に対して計算されるメンバーをサポートする**すべて**実際のメンバーを 1 つにします。  
  
 **ディメンション属性:** CSDLBI 出力でディメンション属性はサポートされ、自動的に非集計としてマークします。  
  
 **Kpi:** Kpi は CSDLBI version 1.1 でサポートされていましたが、表現が変更されました。 以前の KPI はメジャーのプロパティでした。 バージョン 1.1 でのメジャーを KPI 要素を追加できます。  
  
 **新しいプロパティ:** DirectQuery モデルをサポートする属性が追加されました。  
  
 **制限事項:** セルのセキュリティはサポートされていません。  
  
## <a name="see-also"></a>参照  
 [Business Intelligence & #40; 向けの CSDL 注釈CSDLBI & #41;](../../analysis-services/tabular-model-programming-compatibility-levels-1050-1103/csdl-annotations-for-business-intelligence-csdlbi.md)  
  
  

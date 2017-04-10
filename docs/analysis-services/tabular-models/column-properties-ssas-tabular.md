---
title: "Column Properties (SSAS Tabular) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "analysis-services"
  - "analysis-services/multidimensional-tabular"
  - "analysis-services/data-mining"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.asvs.bidtoolset.columnprop.f1"
ms.assetid: 4046c1a3-46c7-47db-b355-52e9c2f23671
caps.latest.revision: 14
author: "Minewiskan"
ms.author: "owend"
manager: "erikre"
caps.handback.revision: 14
---
# Column Properties (SSAS Tabular)
  このトピックでは、テーブル モデルの列のプロパティについて説明します。  
  
 このトピックのセクション:  
  
-   [列のプロパティ](#bkmk_properties)  
  
-   [列のプロパティの設定を構成する](#bkmk_config_prop)  
  
##  <a name="bkmk_properties"></a> 列のプロパティ  
 **基本**  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|**列名**||モデルに格納され、レポート クライアントのフィールドの一覧に表示される列の名前。|  
|**データ形式**|インポート時に自動的に決定します。|この列のデータに使用される表示形式を指定します。 このプロパティには、次のオプションがあります。<br /><br /> **全般**<br /><br /> **10 進数**<br /><br /> **整数**<br /><br /> **Currency**<br /><br /> **[パーセント]**<br /><br /> **[指数]**<br /><br /> データ形式を定義したら、各形式に固有のプロパティを設定できます。 たとえば、 **[通貨]** 形式を選択した場合は、表示される小数点以下の桁数の設定、桁区切り記号の選択、および通貨記号の選択を行います。<br /><br /> <br /><br /> 列の値に画像が含まれる場合は、「 **基本画像**」を参照してください。|  
|**データ型**|インポート時に自動的に決定します。|列のすべての値のデータ型を指定します。|  
|**Description**||列の説明文です。<br /><br /> 特定のレポート クライアントで、フィールド一覧のこの列にエンド ユーザーがカーソルを重ねると、ツールヒントとしてこの説明が表示されます。|  
|**[非表示]**|False|レポート クライアント フィールドの一覧で、列を非表示にするかどうかを指定します。<br /><br /> このプロパティを **[True]** に設定すると、この列は非表示になります。 たとえば、識別子またはキーを含む列は、通常はエンド ユーザーにとっては役に立ちません。<br /><br /> レポート クライアントで列を非表示にしても、そのフィールドはモデル データでは非表示にはなりません。 モデルに対するクエリを作成すると、そのフィールドが表示されます。 非表示の列は、引き続きグループ化または並べ替えに使用できます。<br /><br /> **[非表示]** プロパティは、データ セキュリティはまったく考慮されません。 データのセキュリティを確保するため、"ロール" では行フィルターを使用してください。 詳細については、「[ロール (SSAS テーブル)](../../analysis-services/tabular-models/roles-ssas-tabular.md)」を参照してください。|  
|**列で並べ替え**||この列の値を並べ替えるために使用するもう 1 つの列を指定します。 2 つの列の間にリレーションシップが存在する必要があります。<br /><br /> この値には、既存の列の名前を指定してください。 数式またはメジャーを指定することはできません。|  
  
 **レポートのプロパティ**  
  
 [!INCLUDE[ssCrescent](../../includes/sscrescent-md.md)] テーブル動作プロパティの設定の詳細については、「[Power View レポートのテーブル動作プロパティの構成 (SSAS テーブル)](../../analysis-services/tabular-models/configure-table-behavior-properties-for-power-view-reports-ssas-tabular.md)」を参照してください。  
  
|プロパティ|既定の設定|Description|  
|--------------|---------------------|-----------------|  
|[既定の画像]|False|行データを表す画像を提供する列 (たとえば、従業員レコードの写真 ID) を指定します。|  
|既定のラベル|False|行データを表す表示名を提供する列 (たとえば、従業員レコードの従業員名) を指定します。|  
|[画像の URL]/[データ カテゴリ] (SP1)|False|サーバー上の画像へのハイパーリンクとして、この列の値を指定します。 たとえば、「http://localhost/images/image1.jpg」のように指定します。|  
|[一意の行を保持]|False|重複している場合でも一意として扱う必要のある値を提供する列を指定します (たとえば、2 人以上の従業員が同じ名前を持つ可能性がある場合の従業員の姓名)。|  
|[行識別子 (ROWID)]|False|一意の値のみ含む列を指定します。その列を内部グループ化キーとして使用できます。|  
|集計の方法|既定値|この列がフィールドの一覧に追加されたとき、列の計算に集計関数 SUM を適用するレポート クライアント ツールを指定します。 既定の計算を変更するには、ドロップダウン リストから選択します。 このプロパティは、集計が可能な種類の列にのみ適用されます。|  
|[テーブルの詳細の位置]|[既定のフィールド セットがありません]|レポート クライアントでテーブルが見やすくなるように、1 つのテーブルのフィールド セットに追加できる、この列またはメジャーを指定します。|  
  
##  <a name="bkmk_config_prop"></a> 列のプロパティの設定を構成する  
  
1.  モデル デザイナーでテーブルから列を選択します。  
  
2.  **[プロパティ]** ウィンドウで、プロパティをクリックして値を入力するか、下矢印をクリックして設定オプションを選択します。  
  
## 参照  
 [Power View レポート プロパティ (SSAS テーブル)](../../analysis-services/tabular-models/power-view-reporting-properties-ssas-tabular.md)   
 [列の非表示または固定 (SSAS テーブル)](../../analysis-services/tabular-models/hide-or-freeze-columns-ssas-tabular.md)   
 [列のテーブルへの追加 (SSAS テーブル)](../../analysis-services/tabular-models/add-columns-to-a-table-ssas-tabular.md)  
  
  
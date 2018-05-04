---
title: モデル オブジェクト (TMSL) |Microsoft ドキュメント
ms.custom: ''
ms.date: 05/30/2017
ms.prod: analysis-services
ms.prod_service: analysis-services, azure-analysis-services
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: reference
ms.assetid: 9382d0d6-2d4b-49ad-a0eb-35970f0f3afb
caps.latest.revision: 7
author: Minewiskan
ms.author: owend
manager: kfile
ms.openlocfilehash: 4bbc2865e6a6bd46f7111cc8c9656909e5855069
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="model-object-tmsl"></a>モデル オブジェクト (TMSL)
[!INCLUDE[ssas-appliesto-sqlas-aas](../../includes/ssas-appliesto-sqlas-aas.md)]
  表形式モデルを定義します。 データベース、および任意のコマンドで指定できる 1 つだけデータベースごとに 1 つのモデルがあります。 データベース オブジェクトは、親オブジェクトです。  
  
 モデルの定義は、1 つのトピックの全体の構文を再現するには大きすぎます。 このため、部分的な構文の主要な部分を強調表示下にある、子オブジェクトへのリンク。  
  
 おそらくモデル定義を理解する最善の方法では、よく理解している表形式モデルから開始します。 使用して、**コードの表示**オプションが SQL Server Data Tools でその定義を表示します。 コードを表示できるように、JSON エディターをインストールしてください。 Visual Studio での JSON エディターを取得できます[Community edition のダウンロード](https://www.visualstudio.com/downloads/download-visual-studio-vs.aspx)または Visual Studio の他のエディション。  
  
> [!NOTE]  
>  任意のスクリプトでは、時にデータベースを 1 つだけを参照できます。 データベース自体以外の任意のオブジェクトのデータベースのプロパティは、モデルを指定する場合は省略可能です。 モデルとを明示的に提供されている場合は、データベース名を推測するために使用するデータベースの間の一対一のマッピングがあります。   
> 同様に、データベースでそのプロパティを設定するモデルを省略できます。  
  
## <a name="object-definition"></a>オブジェクトの定義  
 すべてのオブジェクトは、共通の名前、型、説明、プロパティのコレクション、および注釈を含むプロパティのセットを持ちます。 **モデル**オブジェクトでは、次のプロパティもがあります。  
  
 StorageLocation  
 モデルを配置するディスク上の場所です。  
  
 defaultMode  
 データをパーティションで利用できるようにする既定のメソッドです。  
  
 defaultDataView  
 DirectQuery モードのモデルは、このプロパティは、どのパーティションは、モデルに対するクエリを実行するために使用を決定します。  有効な値には、フル インストール オプションとサンプルが含まれます。  
  
 カルチャ  
 書式設定に使用するカルチャ。  
  
 照合順序 (collation)  
 照合順序です。 参照してください[Analysis Services のグローバリゼーションのシナリオ](../../analysis-services/globalization-scenarios-for-analysis-services.md)詳細についてはします。  
  
 表  
 パーティション、列、メジャー、Kpi、および注釈を含む、モデル内のテーブルのすべてのコレクション。 参照してください[Tables オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tables-object-tmsl.md)詳細についてはします。  
  
 リレーションシップ  
 フィルターの方向とセキュリティ設定のプロパティを含むテーブルの各ペア間のリレーションシップを指定します。 参照してください[リレーションシップ オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/relationships-object-tmsl.md)詳細についてはします。  
  
 データ ソース  
 データ モデルを提供するための外部データベースに 1 つまたは複数の接続は、クエリを通過します。 参照してください[データソース オブジェクト&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/datasources-object-tmsl.md)詳細についてはします。  
  
 ロール  
 データベース アクセス許可、メンバーのアカウント、および必要に応じて、DAX でカスタム アクセス制御のためのセキュリティ フィルターを関連付けるオブジェクト。  
  
## <a name="usage"></a>使用方法  
 **モデル**オブジェクトにはモデル全体が含まれています。 ほとんどのコマンドで 1 つのモデルや、親データベース オブジェクトのいずれかを指定する必要があります。  
  
 作成する場合、置換、または、モデル オブジェクトを変更することは、オブジェクト定義のすべての読み取り/書き込みプロパティを指定します。 読み取り/書き込みプロパティの省略は、削除であると見なされます。  
  
## <a name="partial-syntax"></a>一部の構文  
 このオブジェクトの定義が非常に大きいため、最初のレベル プロパティのみが一覧表示されます。 参照してください[オブジェクト定義を表形式モデル スクリプト言語で&#40;TMSL&#41; ](../../analysis-services/tabular-models-scripting-language-objects/tmsl-reference-tabular-objects.md)子オブジェクトの一覧についてはします。  
  
```  
    "model": {  
      "description": "Model object of a Tabular database",  
      "type": "object",  
      "properties": {  
          "name": {  },  
          "description": {  },  
         "storageLocation": {  },  
         "defaultMode":  {  },  
         "defaultDataView": {  },  
         "culture": {  },  
         "collation": {  },  
         "annotations": {  },  
         "tables": {  },  
         "relationships": {  },  
         "dataSources": {  },  
         "perspectives": {  },  
            "cultures": {  },  
         "roles": {  }  
    }  
  
```  
  
## <a name="see-also"></a>参照  
 [表形式モデルのスクリプト言語 (TMSL) リファレンス](../../analysis-services/tabular-model-scripting-language-tmsl-reference.md)   
 [Analysis Services での表形式モデルの互換性レベル](../../analysis-services/tabular-models/compatibility-level-for-tabular-models-in-analysis-services.md)  
  
  

---
title: "マルチ ディメンション スキーマとデータの概要 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.technology:
- drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- multidimensional schemas and data
ms.assetid: ce37fa06-c581-4d80-9a9b-c3aa66408909
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: cf3e8d6bebd5860df9f52236eecf4d1f287a8f9d
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="overview-of-multidimensional-schemas-and-data"></a>マルチ ディメンション スキーマとデータの概要
## <a name="understanding-multidimensional-schemas"></a>マルチ ディメンション スキーマを理解します。  
 ADO MD で中心的なメタデータ オブジェクトが、*キューブ*、構造化された一連の関連するディメンション、階層、レベル、およびメンバーから構成されます。  
  
 A*ディメンション*は独立したビジネス エンティティから派生した、多次元データベースからのデータのカテゴリ。 通常、ディメンションには、データベースのメジャーのクエリ条件として使用する項目が含まれます。  
  
 A*階層*ディメンションの集計のパスです。 ディメンションが複数のレベル、粒度の親子関係である必要があります。 階層は、これらのレベルがどのように関連しているかを定義します。  
  
 A*レベル*階層内の集計の手順です。 情報の複数のレイヤーを含むディメンションでは、各レイヤーはレベルです。  
  
 A*メンバー*ディメンション内のデータ項目がします。 通常、キャプションを作成したり、メンバーを使用して、データベースのメジャーを記述します。  
  
 キューブがによって表される[CubeDef](../../../ado/reference/ado-md-api/cubedef-object-ado-md.md) ADO MD 内のオブジェクト ディメンション、階層、レベル、およびメンバーが、対応する ADO MD オブジェクトによって表されるも:[ディメンション](../../../ado/reference/ado-md-api/dimension-object-ado-md.md)、[階層](../../../ado/reference/ado-md-api/hierarchy-object-ado-md.md)、[レベル](../../../ado/reference/ado-md-api/level-object-ado-md.md)、および[メンバー](../../../ado/reference/ado-md-api/member-object-ado-md.md)です。  
  
### <a name="dimensions"></a>ディメンション  
 キューブのディメンションは、ビジネス エンティティと、データベースでモデル化するデータの種類によって異なります。 通常、各ディメンションは、独立したエントリ ポイントまたはデータを選択するためのメカニズムです。  
  
 たとえば、売上データを含むキューブには次の 5 つのディメンション: 販売員、Geography、時刻、製品、およびメジャーです。 メジャー ディメンションには、他のディメンションが分類して売上データの値をグループ化する方法を表すに対し、実際の売上データの値が含まれています。  
  
 Geography ディメンションには、次のメンバーのセットがあります。  
  
```  
{All, North America, Europe, Canada, USA, UK, Germany, Canada-West,  
Canada-East, USA-NW, USA-SW, USA-NE, USA-SE, England, Scotland,   
Wales,Ireland, Germany-North, Germany-South, Ottawa, Toronto,   
Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston,   
Shreveport, Miami, Boston, New York, London, Dover, Glasgow,   
Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin,   
Hamburg, Munich, Stuttgart}  
```  
  
### <a name="hierarchies"></a>階層  
 階層は、ディメンションのレベルをロール アップまたはグループ化方法を定義します。 ディメンションには、複数の階層を持つことができます。 Geography ディメンションの自然な階層が存在します。  
  
### <a name="levels"></a>Levels  
 前の図に示されている例 Geography ディメンションには、各ボックスは、階層内のレベルを表します。  
  
 各レベルでは、メンバーのセットを次のようには。  
  
-   世界中`= {All}`  
  
-   大陸`= {North America, Europe}`  
  
-   国`= {Canada, USA, UK, Germany}`  
  
-   地域`= {Canada-East, Canada-West, USA-NE, USA-NW, USA-SE, USA-SW, England, Ireland, Scotland, Wales, Germany-North, Germany-South}`  
  
-   都市`= {Ottawa, Toronto, Vancouver, Calgary, Seattle, Boise, Los Angeles, Houston, Shreveport, Miami, Boston, New York, London, Dover, Glasgow, Edinburgh, Cardiff, Pembroke, Belfast, Derry, Berlin, Hamburg, Munich, Stuttgart}`  
  
### <a name="members"></a>メンバー  
 階層のリーフ レベルのメンバーには、子がなくと親を持つルート レベルのメンバーがありません。 他のすべてのメンバーは、少なくとも 1 つの親とには、少なくとも 1 つの子があります。 たとえば、Geography ディメンションの階層ツリーの部分的なトラバースには、次の親子リレーションシップが得られます。  
  
-   `{All} (parent of) {Europe, North America}`  
  
-   `{North America} (parent of) {Canada, USA}`  
  
-   `{USA} (parent of) {USA-NE, USA-NW, USA-SE, USA-SW}`  
  
-   `{USA-NW} (parent of) {Boise, Seattle}`  
  
 メンバーは、ディメンションごとに 1 つまたは複数の階層に沿って統合できます。 時間ディメンションを検討してくださいが 2 つの方法で、日レベルの Year レベルにロールアップします。  
  
 この例では、他の特性も示しています。 年度の四半期の階層のあらゆるレベルに、年、週の階層レベルが週の一部のメンバーは表示されません。 したがって、階層はディメンションのすべてのメンバーを含める必要はありません。  
  
## <a name="see-also"></a>参照  
 [ADO MD オブジェクト モデル](../../../ado/reference/ado-md-api/ado-md-object-model.md)   
 [ADO (多次元) (ADO MD)](../../../ado/guide/multidimensional/ado-multidimensional-ado-md.md)   
 [ADO MD を使用したプログラミング](../../../ado/guide/multidimensional/programming-with-ado-md.md)   
 [ADO MD と ADO の併用](../../../ado/guide/multidimensional/using-ado-with-ado-md.md)   
 [多次元データの操作](../../../ado/guide/multidimensional/working-with-multidimensional-data.md)


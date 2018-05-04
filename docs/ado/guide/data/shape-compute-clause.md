---
title: 図形の COMPUTE 句 |Microsoft ドキュメント
ms.prod: sql
ms.prod_service: connectivity
ms.component: ado
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- compute clause [ADO]
- data shaping [ADO], COMPUTE clause
ms.assetid: 3fdfead2-b5ab-4163-9b1d-3d2143a5db8c
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 25d89db4052234482846dc752e5c0431bb517164
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="shape-compute-clause"></a>図形の COMPUTE 句
図形の COMPUTE 句には、親が生成されます**レコード セット**、子への参照で構成されている列を持つ**レコード セット**以外の場合は省略可能な列の内容が章では、新しい、または計算列、または子で集計関数の実行結果**レコード セット**以前形または**レコード セット**; 子からの列と**レコード セット**に一覧表示オプションの BY 句。  
  
## <a name="syntax"></a>構文  
  
```  
SHAPE child-command [AS] child-alias  
   COMPUTE child-alias [[AS] name], [appended-column-list]  
   [BY grp-field-list]  
```  
  
## <a name="description"></a>Description  
 この句の各部分は次のとおりです。  
  
 *child-command*  
 次のいずれかで構成されます。  
  
-   中かっこ内のクエリ コマンド ("{}") を返す子**Recordset**オブジェクト。 基になるデータ プロバイダーにコマンドが発行され、その構文は、そのプロバイダーの要件によって異なります。 これは通常なります SQL 言語では、ADO では、特定のクエリ言語は必要はありません。  
  
-   既存の形の名前**Recordset**です。  
  
-   別の図形コマンド。  
  
-   このデータ プロバイダーでのテーブルの名前を続けてテーブル キーワードです。  
  
 *child-alias*  
 使用して参照する別名、 **Recordset**によって返される、*子コマンド。* *子エイリアス*COMPUTE 句で列の一覧で、必須であり、親と子の間の関係を定義**Recordset**オブジェクト。  
  
 *appended-column-list*  
 各要素が生成された親の列を定義するリスト。 各要素には、チャプター列、新しい列、計算列、または子に対する集計関数の結果の値が含まれています。 **Recordset**です。  
  
 *grp-field-list*  
 親と子列の一覧**Recordset**子の行をグループ化する方法を指定するオブジェクト。  
  
 各列に対して、*グループのフィールド リスト*子と親に対応する列が**Recordset**オブジェクト。 親の行ごと**Recordset**、*グループ フィールド リスト*列は一意の値と子要素がある**レコード セット**親によって参照されている行のみで構成される子行を持つ*グループ フィールド リスト*列は、親の行と同じ値を持ちます。  
  
 BY 句が含まれている場合、子**Recordset**の行はグループ化、COMPUTE 句内の列に基づいて。 親**レコード セット**子内の行のグループごとに 1 つの行を含む**Recordset**です。  
  
 BY 句を省略すると、子全体**レコード セット**は 1 つのグループと、親として扱われます**Recordset**は正確に 1 つの行が含まれます。 その行は子全体を参照する**Recordset**です。 BY 句を省略すると、子全体を「総計」集計を計算できます**Recordset**です。  
  
 以下に例を示します。  
  
```  
SHAPE {select * from Orders} AS orders             COMPUTE orders, SUM(orders.OrderAmount) as TotalSales         
```  
  
 どのような方法に関係なく、親**レコード セット**の形式が子に関連するために使用チャプター列が含まれます (COMPUTE を使用または追加を使用)、**レコード セット**です。 場合は、親**Recordset**子の行を集計 (SUM、MIN、MAX、およびなど) を含む列があります。 親と子の両方**レコード セット**内の行に式を含む列を含めることは、**レコード セット**と、新しいと、最初にある列を空にします。  
  
## <a name="operation"></a>操作  
 *子コマンド*、プロバイダーは、子を返しますに発行された**Recordset**です。  
  
 COMPUTE 句は、親の列を指定**レコード セット**、子への参照である**Recordset**、1 つまたは複数の集計、集計式、または新しい列です。 BY 句がある場合を定義する列が、親にも追加**Recordset**です。 BY 句を指定方法、子の行**レコード セット**はグループ化します。  
  
 たとえば、状態、City、および作成のフィールドから成るテーブル、人口統計、という名前があるとします。 (母集団の図は、テーブルには、例としてのみ提供されます。)  
  
|状態|City|[母集団]|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|または|Medford|200,000|  
|または|Portland|400,000|  
|CA|Los Angeles|800,000|  
|CA|サンディエゴ|600,000|  
|WA|Tacoma|500,000|  
|または|Corvallis|300,000|  
  
 ここで、この図形コマンドを発行します。  
  
```  
rst.Open  "SHAPE {select * from demographics} AS rs "  & _  
          "COMPUTE rs, SUM(rs.population) BY state", _  
           objConnection  
```  
  
 このコマンドが、形**Recordset** 2 つのレベル。 親レベルが、生成された**レコード セット**集計列を持つ (`SUM(rs.population)`)、子を参照している列**Recordset** (`rs`)、および子をグループ化するための列**Recordset** (`state`)。 子レベルは、 **Recordset**クエリ コマンドによって返される (`select * from demographics`)。  
  
 子**Recordset**状態によってグループ化されたが、任意の順序でそれ以外の場合に、詳細行になります。 つまり、グループは、アルファベットまたは数字の順序ではできません。 場合は、親**Recordset**使用することができますを順序付ける、**レコード セットの並べ替え**親を順序付ける方法**レコード セット**です。  
  
 開かれている親を移動できるようになりました**Recordset**子詳細へのアクセスと**レコード セット**オブジェクト。 詳細については、次を参照してください。[階層レコード セット内の行のへのアクセス](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)です。  
  
## <a name="resultant-parent-and-child-detail-recordsets"></a>結果の親と子詳細レコード セット  
  
### <a name="parent"></a>Parent  
  
|SUM (rs です。カタログ作成)|rs|状態|  
|---------------------------|--------|-----------|  
|1,300,000|Child1 への参照|CA|  
|1,200,000|Child2 への参照|WA|  
|1,100,000|子 3 への参照|または|  
  
## <a name="child1"></a>Child1  
  
|状態|City|[母集団]|  
|-----------|----------|----------------|  
|CA|Los Angeles|800,000|  
|CA|サンディエゴ|600,000|  
  
## <a name="child2"></a>Child2  
  
|状態|City|[母集団]|  
|-----------|----------|----------------|  
|WA|Seattle|700,000|  
|WA|Tacoma|500,000|  
  
## <a name="child3"></a>子 3  
  
|状態|City|[母集団]|  
|-----------|----------|----------------|  
|または|Medford|200,000|  
|または|Portland|400,000|  
|または|Corvallis|300,000|  
  
## <a name="see-also"></a>参照  
 [階層のレコード セット内の行にアクセスします。](../../../ado/guide/data/accessing-rows-in-a-hierarchical-recordset.md)   
 [データ シェイプの概要](../../../ado/guide/data/data-shaping-overview.md)   
 [Field オブジェクト](../../../ado/reference/ado-api/field-object.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [レコード セット オブジェクト (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)   
 [データ シェイプに必要なプロバイダー](../../../ado/guide/data/required-providers-for-data-shaping.md)   
 [図形の APPEND 句](../../../ado/guide/data/shape-append-clause.md)   
 [一般的な図形コマンド](../../../ado/guide/data/shape-commands-in-general.md)   
 [Value プロパティ (ADO)](../../../ado/reference/ado-api/value-property-ado.md)   
 [Visual Basic for Applications の関数](../../../ado/guide/data/visual-basic-for-applications-functions.md)

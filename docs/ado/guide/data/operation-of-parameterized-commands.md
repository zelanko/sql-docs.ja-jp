---
title: "パラメーター化コマンドの操作 |Microsoft ドキュメント"
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
- data shaping [ADO], parameterized commands
- parameterized commands [ADO]
ms.assetid: 4fae0d54-83b6-4ead-99cc-bcf532daa121
caps.latest.revision: 11
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 65f8a1caba2f709e4583613ced4d6aa03b2d6bf1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="operation-of-parameterized-commands"></a>パラメーター化コマンドの操作
大規模な子で作業している場合**レコード セット**、特に、親のサイズに比べて**レコード セット**、いくつかの子チャプターのみにアクセスする必要がありますが、した方がより効果的に使用、パラメーター化コマンド。  
  
 A*コマンドのパラメーターのない*全体の親と子の両方を取得**レコード セット**親にチャプター列を追加して、親の行ごとに関連する子章への参照を割り当てます.  
  
 A*コマンドをパラメーター化された*全体の親を取得**Recordset**、章のみを取得しますが、**レコード セット**チャプター列にアクセスするとします。 この取得方法の違いには、大幅なパフォーマンスのメリットが得られることができます。  
  
 たとえば、次のように指定できます。  
  
```  
SHAPE {SELECT * FROM customer}   
   APPEND ({SELECT * FROM orders WHERE cust_id = ?}   
   RELATE cust_id TO PARAMETER 0)  
```  
  
 親と子テーブルに、一般的な cust_id で列名がある*です。* *子コマンド*が、"?"プレース ホルダー、RELATE 句で参照する (つまり、".パラメーター 0") です。  
  
> [!NOTE]
>  パラメーターは、図形のコマンド構文にのみ関連します。 それに関連付けられていないか、ADO[パラメーター](../../../ado/reference/ado-api/parameter-object.md)オブジェクトまたは[パラメーター](../../../ado/reference/ado-api/parameters-collection-ado.md)コレクション。  
  
 パラメーター化された shape コマンドを実行すると、以下の処理が行われます。  
  
1.  *親コマンド*を実行して、親を返します**Recordset** Customers テーブルからです。  
  
2.  親にチャプター列が追加されます**Recordset**です。  
  
3.  親行のチャプター列にアクセスする場合、*子コマンド*パラメーターの値として、customer.cust_id の値を使用して実行します。  
  
4.  手順 3 で作成したデータ プロバイダーの行セットのすべての行が、子の作成に使用されます**Recordset**です。 この例では、cust_id customer.cust_id の値に等しいを Orders テーブル内のすべての行です。 既定では、子**Recordset**s は、親へのすべての参照まで、クライアントでキャッシュされます**Recordset**解放されます。 この動作を変更するには、設定、**レコード セット**[動的プロパティ](../../../ado/reference/ado-api/ado-dynamic-property-index.md)**キャッシュ子行**に**False**です。  
  
5.  取得した子の行への参照を (つまり、子のチャプター**レコード セット**) は、親の現在の行のチャプター列に配置されます**レコード セット**です。  
  
6.  別の行のチャプター列にアクセスする場合、手順 3. ~ 5. は繰り返されます。  
  
 **キャッシュ子行**動的プロパティに設定されて**True**既定です。 キャッシュの動作は、クエリのパラメーターの値によって異なります。 子の 1 つのパラメーターを持つクエリ**Recordset**特定のパラメーターの値をその値を持つ子に対する要求間でキャッシュされます。 次のコードでは、これを示しています。  
  
```  
SCmd = "SHAPE {select * from customer} " & _  
         "APPEND({select * from orders where cust_id = ?} " & _  
         "RELATE cust_id TO PARAMETER 0) AS chpCustOrder"  
Rst1.Open sCmd, Cnn1  
Set RstChild = Rst1("chpCustOrder").Value  
Rst1.MoveNext      ' Next cust_id passed to Param 0, & new rs fetched   
                   ' into RstChild.  
Rst1.MovePrevious  ' RstChild now holds cached rs, saving round trip.  
```  
  
 2 つ以上のパラメーターを持つクエリ、キャッシュされた子がすべてのパラメーター値がキャッシュされた値と一致する場合にのみ使用されます。  
  
## <a name="parameterized-commands-and-complex-parent-child-relations"></a>パラメーター化コマンドと複雑な親子関係  
 パラメーター化コマンドを使用して、等結合型階層のパフォーマンスを向上させるために、だけでなくより複雑な親子関係をサポートするためにパラメーター化コマンドを使用できます。 たとえば、次の 2 つのテーブルを持つほとんどリーグ データベース: チーム (team_id、チーム名)、もう一方がゲーム (日付、home_team、visiting_team) から成る 1 つです。  
  
 パラメーターのない階層を使用して、ないようにチームとゲームのテーブルを関連付けるを子**Recordset**チームごとに、完全なスケジュールが含まれています。 ホームのスケジュールと道路スケジュールだけが含まれている章を作成することができます。 これは、RELATE 句によって、フォームの親子関係に制限されているため (pc1 = cc1) AND (pc2 pc2 を =)。 そのため場合は、コマンドには、"RELATE team_id TO home_team、team_id TO visiting_team"が含まれている、する得られるゲームのみここで、チームが再生された自体です。 必要な"(team_id=home_team) または (team_id = visiting_team)"は Shape プロバイダーは、OR 句をサポートしていません。  
  
 目的の結果を得るには、パラメーター化コマンドを使用できます。 例:  
  
```  
SHAPE {SELECT * FROM teams}   
APPEND ({SELECT * FROM games WHERE home_team = ? OR visiting_team = ?}   
        RELATE team_id TO PARAMETER 0,   
               team_id TO PARAMETER 1)   
```  
  
 この例より柔軟に必要な結果を取得する SQL の WHERE 句を悪用します。  
  
> [!NOTE]
>  ときに WHERE 句を使用して、パラメーターいないまたはを使用して SQL データ型 text、ntext および image のエラーが発生する、次の説明が含まれています:`Invalid operator for data type`です。  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な図形コマンド](../../../ado/guide/data/shape-commands-in-general.md)

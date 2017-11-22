---
title: "図形の APPEND 句 |Microsoft ドキュメント"
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: guide
ms.technology: drivers
ms.custom: 
ms.date: 01/19/2017
ms.reviewer: 
ms.suite: sql
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shape commands [ADO]
- data shaping [ADO], APPEND clause
- append clause [ADO]
ms.assetid: f90fcf55-6b24-401d-94e1-d65bd24bd342
caps.latest.revision: "11"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ab01c719611309117308c818930b1553741495e6
ms.sourcegitcommit: 44cd5c651488b5296fb679f6d43f50d068339a27
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/17/2017
---
# <a name="shape-append-clause"></a>図形の APPEND 句
列または列を図形コマンドの APPEND 句が追加され、 **Recordset**です。 多くの場合、これらの列は、チャプター列は、子を参照してください**Recordset**です。  
  
## <a name="syntax"></a>構文  
  
```  
SHAPE [parent-command [[AS] parent-alias]] APPEND column-list  
```  
  
## <a name="description"></a>Description  
 この句の各部分は次のとおりです。  
  
 *親コマンド*  
 次のいずれかです (省略することができます、*親コマンド*完全に)。  
  
-   中かっこ (「{}」) で囲まれたプロバイダーのコマンドを返す、 **Recordset**オブジェクト。 基になるデータ プロバイダーにコマンドが発行され、その構文は、そのプロバイダーの要件によって異なります。 これは通常なります SQL 言語では、ADO では、特定のクエリ言語は必要はありません。  
  
-   別の図形のコマンドは、かっこ内に埋め込まれます。  
  
-   このデータ プロバイダーでのテーブルの名前を続けてテーブル キーワードです。  
  
 *親エイリアス*  
 省略可能な親を参照する別名**Recordset**です。  
  
 *列リスト*  
 1 つ以上の次:  
  
-   集計列です。  
  
-   計算列です。  
  
-   新しい句を使用して作成された新しい列です。  
  
-   チャプター列です。 チャプター列の定義は、かっこ (「()」) で囲まれます。 次の構文を参照してください。  
  
```  
SHAPE [parent-command [[AS] parent-alias]]  
   APPEND (child-recordset [ [[AS] child-alias]   
      RELATE parent-column TO child-column | PARAMETER param-number, ... ])  
   [[AS] chapter-alias]   
   [, ... ]  
```  
  
## <a name="remarks"></a>解説  
 *子レコード セット*  
 -   中かっこ (「{}」) で囲まれたプロバイダーのコマンドを返す、 **Recordset**オブジェクト。 基になるデータ プロバイダーにコマンドが発行され、その構文は、そのプロバイダーの要件によって異なります。 これは通常なります SQL 言語では、ADO では、特定のクエリ言語は必要はありません。  
  
-   別の図形のコマンドは、かっこ内に埋め込まれます。  
  
-   既存の形の名前**Recordset**です。  
  
-   このデータ プロバイダーでのテーブルの名前を続けてテーブル キーワードです。  
  
 *子エイリアス*  
 子を参照する別名**Recordset**です。  
  
 *親列*  
 内の列、 **Recordset**によって返される、*親コマンド。*  
  
 *子列*  
 内の列、 **Recordset**によって返される、*子コマンド*です。  
  
 *パラメーター番号*  
 参照してください[パラメーター化コマンドの操作](../../../ado/guide/data/operation-of-parameterized-commands.md)です。  
  
 *チャプター エイリアス*  
 親に追加されたチャプター列を参照する別名です。  
  
> [!NOTE]
>  *"親列*TO*子列"*句では、一覧では実際には、各リレーションシップが定義されてがコンマで区切られています。  
  
> [!NOTE]
>  APPEND キーワードが実際には、一覧、それぞれの句はコンマで区切るし、親に追加する別の列を定義した後の句。  
  
## <a name="remarks"></a>解説  
 SHAPE コマンドの一部としてユーザー入力からプロバイダーのコマンドを構築するときに図形ユーザーが指定したプロバイダー コマンドととして処理不透明な文字列にプロバイダーに渡します。 たとえば、以下の図形コマンド、  
  
```  
SHAPE {select * from t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 図形は 2 つのコマンドを実行します。`select * from t1`と (`select * from t2 RELATE k1 TO k2)`です。 セミコロンで区切られた複数のプロバイダー コマンドで構成される複合コマンドを指定すると、図形ができない場合は、違いを区別するためにします。 それには、次の図形コマンド  
  
```  
SHAPE {select * from t1; drop table t1} APPEND ({select * from t2} RELATE k1 TO k2)  
```  
  
 図形の実行`select * from t1; drop table t1`と (`select * from t2 RELATE k1 TO k2),`を知らず`drop table t1`は個別のと、この場合、危険な場合は、プロバイダー コマンドでします。 アプリケーションには、ユーザー入力をそのような潜在的なハッカーの攻撃を防ぐに常に検証する必要があります。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [非パラメーター化コマンドの操作](../../../ado/guide/data/operation-of-non-parameterized-commands.md)  
  
-   [パラメーター化コマンドの操作](../../../ado/guide/data/operation-of-parameterized-commands.md)  
  
-   [ハイブリッド コマンド](../../../ado/guide/data/hybrid-commands.md)  
  
-   [介在する Shape COMPUTE 句](../../../ado/guide/data/intervening-shape-compute-clauses.md)  
  
## <a name="see-also"></a>参照  
 [データ シェイプの例](../../../ado/guide/data/data-shaping-example.md)   
 [図形の正式な文法](../../../ado/guide/data/formal-shape-grammar.md)   
 [一般的な Shape コマンド](../../../ado/guide/data/shape-commands-in-general.md)

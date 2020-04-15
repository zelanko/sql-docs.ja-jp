---
title: ステートメント パラメータ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- statement parameters [ODBC]
ms.assetid: 58d5b166-2578-4699-a560-1f1e6d86c49a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 02327ff4bb6a1ac3ac57fbf7d3c6b09b70c11534
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306823"
---
# <a name="statement-parameters"></a>ステートメント パラメーター
*パラメーター*は、SQL ステートメント内の変数です。 たとえば、パーツ テーブルに PartID、説明、価格という名前の列があるとします。 パラメータを指定せずにパーツを追加するには、次のような SQL ステートメントを作成する必要があります。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 このステートメントは新しい注文を挿入しますが、挿入する値をアプリケーションでハードコーディングできないため、注文入力アプリケーションには適していません。 別の方法として、挿入する値を使用して、実行時に SQL ステートメントを作成する方法があります。 また、実行時にステートメントを作成する複雑さがあるため、これは優れた解決策ではありません。 最善の解決策は **、VALUES**句の要素を疑問符 (?) または*パラメータ マーカー*に置き換える方法です。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 これらのパラメーター マーカーは、その後アプリケーション変数にバインドされます。 新しい行を追加するには、アプリケーションは変数の値を設定し、ステートメントを実行するだけです。 ドライバーで、変数から現在値が取得され、データ ソースに送信されます。 ステートメントが複数回実行される場合、アプリケーションはステートメントを準備することでプロセスをさらに効率的にできます。  
  
 この例では、新しい行を挿入するために、注文入力アプリケーションでハードコーディングされたステートメントが使用されている可能性があります。 ただし、パラメーター マーカーは垂直方向のアプリケーションに限定されません。 どのアプリケーションでも、テキストとの変換を回避することで、実行時に SQL ステートメントを作成する際の難しさを緩和します。 たとえば、表示されているパーツ ID は、整数としてアプリケーションに格納される可能性が高くなります。 SQL ステートメントがパラメーター・マーカーなしで構成されている場合、アプリケーションは部品 ID をテキストに変換し、データ・ソースはそれを整数に変換して戻す必要があります。 パラメーター マーカーを使用すると、アプリケーションは、通常、整数としてデータ ソースに送信できる整数として、ドライバーにパーツ ID を送信できます。 これにより、2 つの変換が保存されます。 長いデータ値の場合、このような値のテキスト形式が SQL ステートメントの許容長を超えることが多いため、これは非常に重要です。  
  
 パラメータは、SQL ステートメントの特定の場所でのみ有効です。 たとえば、選択リスト **(SELECT**ステートメントによって返される列のリスト) には、パラメーターの型を判別できないため、等号 (=) などの二項演算子の両方のオペランドとして使用することはできません。 一般に、パラメーターはデータ操作言語 (DML) ステートメントでのみ有効であり、データ定義言語 (DDL) ステートメントでは有効ではありません。 詳細については、「付録 C: SQL 文法[」の「パラメータ マーカー](../../../odbc/reference/appendixes/parameter-markers.md) 」を参照してください。  
  
 SQL ステートメントがプロシージャーを呼び出すときに、名前付きパラメーターを使用できます。 名前付きパラメーターは、SQL ステートメント内での位置ではなく、名前によって識別されます。 **SQLBindParameter**の呼び出しによってバインドできますが、パラメーターは **、SQLBindParameter**の*パラメーター数値*引数ではなく、IPD のSQL_DESC_NAME フィールド (実装パラメーター記述子) によって識別されます。 また **、SQLSetDescField**または**SQLSetDescRec**を呼び出すことによってバインドすることもできます。 名前付きパラメーターの詳細については、後の「[名前によるパラメーターのバインド (名前付きパラメーター)」](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)を参照してください。 記述子の詳細については、[記述子](../../../odbc/reference/develop-app/descriptors.md)を参照してください。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [パラメーターのバインド](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [パラメーターの値の設定](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [長い形式のデータの送信](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [SQLGetData による出力パラメーターの取得](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [プロシージャのパラメーター](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [パラメーター値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)

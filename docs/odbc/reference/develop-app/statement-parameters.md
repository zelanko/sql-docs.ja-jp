---
title: "ステートメントのパラメーター |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- statement parameters [ODBC]
ms.assetid: 58d5b166-2578-4699-a560-1f1e6d86c49a
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 5e56b61d47581f98f37560875de920c45029c2e9
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="statement-parameters"></a>ステートメントのパラメーター
A*パラメーター* SQL ステートメントの変数です。 たとえば、部品テーブルに PartID、説明、および価格をという名前の列があるとします。 パラメーターなしのパーツを追加するには必要とするように SQL ステートメントの構築します。  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (2100, 'Drive shaft', 50.00)  
```  
  
 このステートメントは、新しい注文を挿入はいない受注アプリケーションに適してのため、挿入する値は、アプリケーションにハードコーディングすることはできません。 代わりに挿入する値を使用して、実行時に、SQL ステートメントの構築を開始します。 これはもない良いソリューションの実行時に作成するステートメントの複雑であるためです。 最適なソリューションは、要素を置換する、**値**疑問符 (?) を含む句または*パラメーター マーカー*:  
  
```  
INSERT INTO Parts (PartID, Description, Price) VALUES (?, ?, ?)  
```  
  
 これらのパラメーター マーカーは、その後アプリケーション変数にバインドされます。 新しい行を追加するには、アプリケーションは、変数の値を設定し、ステートメントを実行するだけにします。 ドライバーで、変数から現在値が取得され、データ ソースに送信されます。 ステートメントが複数回を実行できる場合、アプリケーションで作成できますプロセスよりも効率的なステートメントを準備します。  
  
 単に示したステートメントは、新しい行を挿入する受注アプリケーションでハード コードされた可能性があります。 ただし、パラメーター マーカーでは、垂直方向のアプリケーションに制限はありません。 任意のアプリケーションのテキストとの間の変換を回避することで、実行時に SQL ステートメントを構築するが困難な容易になります。 たとえば、示されている一部の ID は最も可能性の高い整数としてアプリケーションに格納されているです。 SQL ステートメントは、パラメーター マーカーを使用せずに作成されて、アプリケーションが部分 ID をテキストに変換する必要があり、データ ソースを使用すると、整数に変換する必要があります。 パラメーター マーカーを使用すると、アプリケーションとして送信できます部分 ID、ドライバーを整数では、通常、整数としてデータ ソースに送信できます。 これは、2 つの変換を保存します。 長い形式のデータ値は、これは非常に重要ですが、そのような値のテキスト形式が頻繁に SQL ステートメントに許容される長さを超えているためです。  
  
 パラメーターは、SQL ステートメントの特定の場所でのみ有効です。 たとえば、これらでは許可されません、選択リスト (によって返される列の一覧、**選択**ステートメント) は、許可されている、等号 (=) などのバイナリ演算子のオペランドは両方ともとしてすることはできませんのでもパラメーターの型を決定します。 一般に、パラメーターは、データ定義言語 (DDL) ステートメントではなく、データ操作言語 (DML) ステートメントでのみ有効です。 詳細については、次を参照してください。[パラメーター マーカー](../../../odbc/reference/appendixes/parameter-markers.md)付録 c: SQL の文法でします。  
  
 SQL ステートメントが、パラメーターをという名前のプロシージャを呼び出す場合は使用できます。 名前付きパラメーターは、SQL ステートメント内の位置ではなく、名前によって識別されます。 呼び出しでバインドすることできます**SQLBindParameter**、パラメーターがなくの IPD (実装パラメーター記述子) の SQL_DESC_NAME フィールドによって識別されるが、 *ParameterNumber*の引数**SQLBindParameter**です。 呼び出すことでバインドすることも**SQLSetDescField**または**SQLSetDescRec**です。 名前付きパラメーターの詳細については、次を参照してください。[名前 (名前付きパラメーター) でのパラメーターのバインド](../../../odbc/reference/develop-app/binding-parameters-by-name-named-parameters.md)、このセクションで後述します。 記述子の詳細については、次を参照してください。[記述子](../../../odbc/reference/develop-app/descriptors.md)です。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [パラメーターのバインド](../../../odbc/reference/develop-app/binding-parameters-odbc.md)  
  
-   [パラメーター値の設定](../../../odbc/reference/develop-app/setting-parameter-values.md)  
  
-   [長い形式のデータを送信します。](../../../odbc/reference/develop-app/sending-long-data.md)  
  
-   [SQLGetData によるパラメーターの出力を取得します。](../../../odbc/reference/develop-app/retrieving-output-parameters-using-sqlgetdata.md)  
  
-   [プロシージャのパラメーター](../../../odbc/reference/develop-app/procedure-parameters.md)  
  
-   [パラメーター値の配列](../../../odbc/reference/develop-app/arrays-of-parameter-values.md)


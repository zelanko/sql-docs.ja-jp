---
title: "名前 (名前付きパラメーター) でパラメーターをバインド |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- named parameters [ODBC]
- binding parameters by name [ODBC]
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
caps.latest.revision: 7
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: b3047d17ff1e9785e203b6be0ab48c7c27fd88d1
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="binding-parameters-by-name-named-parameters"></a>名前 (名前付きパラメーター) でパラメーターのバインド
特定の Dbms では、アプリケーションの代わりに、プロシージャ呼び出し内の位置での名前でストアド プロシージャにパラメーターを指定できるようにします。 このようなパラメーターと呼びます*名前付きパラメーター*です。 ODBC では、名前付きパラメーターの使用をサポートします。 ODBC では、名前付きパラメーターはストアド プロシージャ呼び出しでのみ使用し、他の SQL ステートメントでは使用できません。  
  
 ドライバーでは、パラメーターが使用される名前付きかどうかを決定する IPD の SQL_DESC_UNNAMED フィールドの値を確認します。 SQL_DESC_UNNAMED がときに設定されていない場合、ドライバーは、名前を IPD の SQL_DESC_NAME フィールドに使用して、パラメーターを識別します。 パラメーターをバインドするアプリケーションを呼び出すことができます**SQLBindParameter**にパラメーター情報を指定して呼び出すことができますし、 **SQLSetDescField** IPD の SQL_DESC_NAME フィールドを設定します。 名前付きパラメーターを使用している場合は、プロシージャ呼び出しでパラメーターの順序は重要ではありません、パラメーターのレコード数が無視されます。  
  
 無名のパラメーターと名前付きパラメーターの違いは、記述子のレコード数と、プロシージャのパラメーター番号間のリレーションシップでです。 無名のパラメーターを使用している場合、最初のパラメーター マーカーは、プロシージャ呼び出しで作成順で最初のパラメーターにさらに関連するパラメーター記述子の最初のレコードに関連します。 名前付きパラメーターを使用している場合は、最初のパラメーター マーカーがまだパラメーター記述子の最初のレコードに関連するが、記述子のレコード数と、プロシージャのパラメーター番号間のリレーションシップはもう存在しません。 名前付きパラメーターには、プロシージャのパラメーター位置; を記述子レコード番号のマッピングは使用しないでください。代わりに、記述子レコード名は、プロシージャのパラメーター名にマップされます。  
  
> [!NOTE]  
>  IPD の自動設定が有効になっている場合、ドライバーに挿入されます記述子記述子レコードの順序でプロシージャの定義でパラメーターの順序は一致するよう場合でも、名前付きパラメーターが使用されます。  
  
 場合は、名前付きパラメーターを使用すると、すべてのパラメーターはパラメーターを名前する必要があります。 任意のパラメーターは、名前付きパラメーターではないの場合は、パラメーターという名前パラメーター ca のいずれもあります。 名前付きパラメーターと名前のないパラメーターの組み合わせがあった場合は、ドライバーに依存するをする、動作になります。  
  
 名前付きパラメーターの例は、ストアド プロシージャが次のように定義された SQL Server 場合を考えます。  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 この手順では、最初のパラメーターで@title_idが既定値は 1 です。 アプリケーションでは、次のコードを使用して、1 つだけの動的パラメーターを指定するように、このプロシージャを呼び出します。 このパラメーターは、名前を持つ名前付きパラメーター"@quote"です。  
  
```  
// Prepare the procedure invocation statement.  
SQLPrepare(hstmt, "{call test(?)}", SQL_NTS);  
  
// Populate record 1 of ipd.  
SQLBindParameter(hstmt, 1, SQL_PARAM_INPUT, SQL_C_CHAR, SQL_CHAR,  
                  30, 0, szQuote, 0, &cbValue);  
  
// Get ipd handle and set the SQL_DESC_NAMED and SQL_DESC_UNNAMED fields  
// for record #1.  
SQLGetStmtAttr(hstmt, SQL_ATTR_IMP_PARAM_DESC, &hIpd, 0, 0);  
SQLSetDescField(hIpd, 1, SQL_DESC_NAME, "@quote", SQL_NTS);  
  
// Assuming that szQuote has been appropriately initialized,  
// execute.  
SQLExecute(hstmt);  
```


---
title: 名前によるバインド パラメータ (名前付きパラメータ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- named parameters [ODBC]
- binding parameters by name [ODBC]
ms.assetid: e2c3da5a-6c10-4dd5-acf9-e951eea71a6b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a1e214f50488c4600ed39f76e91618cc5ce53de4
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306373"
---
# <a name="binding-parameters-by-name-named-parameters"></a>名前によるパラメーターのバインド (名前付きパラメーター)
特定の Dbms では、アプリケーションはプロシージャ呼び出しの位置ではなく、名前でストアド プロシージャにパラメーターを指定できます。 このようなパラメータは*名前付きパラメータ と呼ばれます*。 ODBC では、名前付きパラメーターの使用がサポートされています。 ODBC では、名前付きパラメーターはストアド プロシージャの呼び出しでのみ使用され、他の SQL ステートメントでは使用できません。  
  
 ドライバーは、IPD のSQL_DESC_UNNAMEDフィールドの値をチェックして、名前付きパラメーターが使用されているかどうかを判断します。 SQL_DESC_UNNAMEDが SQL_UNNAMED に設定されていない場合、ドライバーは、ipD の SQL_DESC_NAME フィールドの名前を使用して、パラメーターを識別します。 パラメーターをバインドするために、アプリケーションは**SQLBindParameter**を呼び出してパラメーター情報を指定し **、SQLSetDescField**を呼び出して IPD のSQL_DESC_NAME フィールドを設定できます。 名前付きパラメーターを使用する場合、プロシージャー呼び出しのパラメーターの順序は重要ではなく、パラメーターのレコード番号は無視されます。  
  
 名前のないパラメーターと名前付きパラメーターの違いは、記述子のレコード番号とプロシージャー内のパラメーター番号の関係にあります。 名前のないパラメーターを使用する場合、最初のパラメーター・マーカーはパラメーター記述子の最初のレコードに関連付けられ、その後はプロシージャー呼び出しの最初のパラメーター (作成順序) に関連付けられます。 名前付きパラメーターを使用する場合、最初のパラメーター・マーカーはパラメーター記述子の最初のレコードに関連していますが、記述子のレコード番号とプロシージャー内のパラメーター番号の関係はもう存在しません。 名前付きパラメーターは、記述子レコード番号のプロシージャー・パラメーター位置へのマッピングを使用しません。代わりに、記述子レコード名はプロシージャー・パラメーター名にマップされます。  
  
> [!NOTE]  
>  IPD の自動作成が有効になっている場合、名前付きパラメーターが使用されている場合でも、記述子レコードの順序がプロシージャ定義のパラメーターの順序と一致するように、ドライバーが記述子を設定します。  
  
 名前付きパラメーターを使用する場合は、すべてのパラメーターに名前付きパラメーターを指定する必要があります。 いずれかのパラメーターが名前付きパラメーターでない場合は、パラメーターのいずれも名前付きパラメーターです。 名前付きパラメーターと名前なしパラメーターが混在している場合、動作はドライバーに依存します。  
  
 名前付きパラメータの例として、SQL Server のストアド プロシージャが次のように定義されているとします。  
  
```  
CREATE PROCEDURE test @title_id int = 1, @quote char(30) AS <blah>  
```  
  
 この手順では、最初のパラメータは@title_id既定値 1 です。 アプリケーションは、次のコードを使用して、このプロシージャを呼び出して、動的パラメーターを 1 つだけ指定できます。 このパラメーターは名前付きのパラメーターで、"quote"\@という名前が付けられます。  
  
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

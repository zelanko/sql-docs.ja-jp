---
title: "割り当てと解放バッファー |Microsoft ドキュメント"
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
- buffers [ODBC], allocating and freeing
- allocating buffers [ODBC]
- freeing buffers [ODBC]
ms.assetid: 886bc9ed-39d4-43d2-82ff-aebc35b14d39
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 73689fb95eb9b51e7f5f16b10c43256ef63f8dd2
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="allocating-and-freeing-buffers"></a>割り当てと解放バッファー
すべてのバッファーでは、割り当てられ、アプリケーションによって解放することができます。 バッファーを遅延しませんが場合は、必要がある関数への呼び出しの間のみ存在します。 たとえば、 **SQLGetInfo**が指すバッファー内の特定のオプションに関連付けられている値を返します、 *InfoValuePtr*引数。 このバッファーへの呼び出し後すぐに解放できる**SQLGetInfo**次のコード例のように。  
  
```  
SQLSMALLINT   InfoValueLen;  
SQLCHAR *     InfoValuePtr = malloc(50);   // Allocate InfoValuePtr.  
  
SQLGetInfo(hdbc, SQL_DBMS_NAME, (SQLPOINTER)InfoValuePtr, 50,  
            &InfoValueLen);  
  
free(InfoValuePtr);                        // OK to free InfoValuePtr.  
```  
  
 遅延のバッファーでは、1 つの関数で指定され、別の使用、ために、ドライバーもが必要ですが存在するときに、遅延のバッファーを解放すると、アプリケーション プログラミング エラーを勧めします。 アドレスなど、 \* *ValuePtr*にバッファーが渡される**SQLBindCol**によって後で使用できる**SQLFetch**です。 列がバインドされているなどへの呼び出しになるまで、このバッファーを解放できません**SQLBindCol**または**SQLFreeStmt**の次のコード例に示すようにします。  
  
```  
SQLRETURN    rc;  
SQLINTEGER   ValueLenOrInd;  
SQLHSTMT     hstmt;  
  
// Allocate ValuePtr  
SQLCHAR * ValuePtr = malloc(50);  
  
// Bind ValuePtr to column 1. It is an error to free ValuePtr here.  
SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, 50, &ValueLenOrInd);  
  
// Fetch each row of data and place the value for column 1 in *ValuePtr.  
// Code to check if rc equals SQL_ERROR or SQL_SUCCESS_WITH_INFO   
// not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {  
   // It is an error to free ValuePtr here.  
}  
  
// Unbind ValuePtr from column 1.  It is now OK to free ValuePtr.  
SQLFreeStmt(hstmt, SQL_UNBIND);  
free(ValuePtr);  
```  
  
 このようなエラーが; 関数でローカルにバッファーを宣言することによって行われた簡単にアプリケーションが、関数を離れると、バッファーが解放されます。 たとえば、次のコードでは、ドライバーで未定義とおそらく致命的な動作がなります。  
  
```  
SQLRETURN   rc;  
SQLHSTMT    hstmt;  
  
BindAColumn(hstmt);  
  
// Fetch each row of data and try to place the value for column 1 in  
// *ValuePtr. Because ValuePtr has been freed, the behavior is undefined  
// and probably fatal. Code to check if rc equals SQL_ERROR or   
// SQL_SUCCESS_WITH_INFO not shown.  
while ((rc = SQLFetch(hstmt)) != SQL_NO_DATA) {}  
  
   .  
   .  
   .  
  
void BindAColumn(SQLHSTMT hstmt)  // WARNING! This function won't work!  
{  
   // Declare ValuePtr locally.  
   SQLCHAR      ValuePtr[50];  
   SQLINTEGER   ValueLenOrInd;  
  
   // Bind rgbValue to column.  
   SQLBindCol(hstmt, 1, SQL_C_CHAR, ValuePtr, sizeof(ValuePtr),  
               &ValueLenOrInd);  
  
   // ValuePtr is freed when BindAColumn exits.  
}  
```


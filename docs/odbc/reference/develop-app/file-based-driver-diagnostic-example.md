---
title: "ファイル ベースのドライバーの診断例 |Microsoft ドキュメント"
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
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 309bea8c888b7fd057e942dd348125c9b420afb7
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="file-based-driver-diagnostic-example"></a>ファイル ベースのドライバーの診断例
ファイル ベースのドライバーは、ODBC ドライバー、およびデータ ソースとして機能します。 ODBC 接続では、データ ソースとしてのエラーと警告の両方として、コンポーネントがそのため生成できます。 書式化しての引数を返すこともドライバー マネージャーとのインターフェイスと、コンポーネントであるため**SQLGetDiagRec**です。  
  
 たとえば、dBASE の Microsoft® ドライバーは、十分なメモリを割り当てられませんでしたが返す可能性があります、次の値から**SQLGetDiagRec**:  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 このエラーは、データ ソースに関連しないがため、ドライバーにのみ追加プレフィックス診断メッセージ ([Microsoft]) のベンダーと、ドライバー ([ODBC dBASE ドライバー])。  
  
 ドライバー Employee.dbf ファイルが見つかりませんでした、次の値を返す可能性があります**SQLGetDiagRec**:  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 このエラーは、データ ソースに関連しているために、ドライバーでは、プレフィックスとして、データ ソース ([dBASE]) のファイル形式を診断メッセージに追加します。 ドライバーも、データ ソースと接続するコンポーネントであるために、仕入先 ([Microsoft]) およびドライバー ([ODBC dBASE ドライバー]) のプレフィックスを追加します。

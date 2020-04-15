---
title: ファイルベースドライバ診断例 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based driver diagnostic [ODBC]
- diagnostic information [ODBC], examples
- error messages [ODBC], diagnostic messages
ms.assetid: 0575fccd-4641-478d-a3cc-5a764e35bae2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 6f09e4f4758b6276836b08f02b24fb31dd1fadc7
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305640"
---
# <a name="file-based-driver-diagnostic-example"></a>ファイル ベースのドライバー診断の例
ファイル ベースのドライバーは、ODBC ドライバーとデータ ソースの両方として機能します。 そのため、ODBC 接続のコンポーネントとデータ ソースの両方でエラーと警告が生成されます。 また、ドライバー マネージャーとのインターフェイスコンポーネントであるため **、SQLGetDiagRec**の引数を書式設定して返します。  
  
 たとえば、dBASE 用の Microsoft ® ドライバが十分なメモリを割り当てることができなかった場合、次の値を**返**す可能性があります。  
  
```  
SQLSTATE:         "HY001"  
Native Error:      42052  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver]Unable to allocate sufficient memory."  
```  
  
 このエラーはデータ ソースに関連していなかったため、ドライバーはベンダー ([Microsoft] ) とドライバー ([ODBC dBASE ドライバー]) の診断メッセージにプレフィックスのみを追加しました。  
  
 ドライバが Employee.dbf ファイルを見つけることができなかった場合は **、SQLGetDiagRec**から次の値を返す可能性があります。  
  
```  
SQLSTATE:         "42S02"  
Native Error:      -1305  
Diagnostic Msg:   "[Microsoft][ODBC dBASE Driver][dBASE]No such table or object"  
```  
  
 このエラーはデータ ソースに関連しているため、ドライバーは、データ ソース ([dBASE]) のファイル形式を診断メッセージのプレフィックスとして追加しました。 ドライバーは、データ ソースとインターフェイスされたコンポーネントでもあるため、ベンダー ([Microsoft] ) とドライバー ([ODBC dBASE ドライバー]) のプレフィックスを追加しました。

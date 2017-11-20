---
title: "SQLError (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 46696509f9276ac4974604c931c4d77acbaae15b
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の概要については、下の該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)です。  
  
 サポート: 完全  
  
 ODBC API の準拠: コア レベル  
  
 最後のエラーについてのエラー状態や状態の情報を返します。 このドライバーは、スタックまたはを返すことのできるエラーの一覧、 *hstmt*、 *hdbc*、および*henv*方法に応じて、引数への呼び出し**SQLError**が行われます。 エラー キューは、各ステートメントの後にフラッシュされます。  
  
 次の表、 **SQLError**引数と戻り値が、ドライバーが使用されます。  
  
|SQLError 引数|戻り値の説明|  
|-----------------------|------------------------------|  
|*szSQLState*|エラーによって表される SQLSTATE の値です。|  
|*pfNativeError*|0 以外の値、 [Visual FoxPro ODBC ドライバー ネイティブのエラー メッセージ](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)です。 ゼロの値は、エラーをドライバーで検出し、適切にマップされていることを示します。 [ODBC エラー コード](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)です。|  
|*後*|ネイティブのエラーまたは ODBC エラーのテキスト。|  
|*pcbErrorMsg*|メッセージ テキストと、識別子の長さの長さ。|  
  
 ドライバーのエラー メッセージの詳細については、次を参照してください。[エラー メッセージの概要](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md)です。 この関数の詳細については、次を参照してください。 [SQLError](../../odbc/reference/syntax/sqlerror-function.md)で、 *ODBC プログラマ リファレンス*です。


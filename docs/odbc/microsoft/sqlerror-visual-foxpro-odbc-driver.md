---
title: SQLError (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLError function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8315ec16-1c22-447a-a577-39bd94f61070
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 3014c5c2af1a0ef8e5f485c790089e4807834446
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47634050"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックでには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 サポート: 完全な  
  
 ODBC API 準拠: コア レベル  
  
 最後のエラーについてのエラーまたは状態情報を返します。 このドライバーは、スタックまたはに対して返されるエラーの一覧、 *hstmt*、 *hdbc*、および*henv*方法に応じて、引数への呼び出し**SQLError**されます。 エラー キューは、各ステートメントの後にフラッシュされます。  
  
 次の表、 **SQLError**引数と戻り値が、ドライバーによって使用されます。  
  
|SQLError 引数|戻り値の説明|  
|-----------------------|------------------------------|  
|*szSQLState*|エラーによって表される SQLSTATE の値。|  
|*pfNativeError*|0 以外の値を[Visual FoxPro ODBC ドライバー ネイティブ エラー メッセージ](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)します。 値 0 は、エラーをドライバーで検出され、マップを適切なことを示します。 [ODBC エラー コード](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)します。|  
|*後*|ネイティブ エラーまたは ODBC エラーのテキスト。|  
|*pcbErrorMsg*|メッセージ テキストと、識別子の長さの長さ。|  
  
 ドライバーのエラー メッセージの詳細については、[エラー メッセージの概要](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md)を参照してください。 この関数の詳細については、[SQLError](../../odbc/reference/syntax/sqlerror-function.md)で、 *ODBC プログラマ リファレンス*を参照してください。

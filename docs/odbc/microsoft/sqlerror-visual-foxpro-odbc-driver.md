---
title: SQL エラー (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0d1247217905187cfb2dbaca6d7b7b562d0175bd
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298682"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: コア レベル  
  
 最後のエラーに関するエラーまたはステータス情報を返します。 ドライバーは **、SQLError**の呼び出しの方法に応じて *、hstmt* *、hdbc、* および*henv*引数に対して返すことができるエラーのスタックまたはリストを保持します。 エラー キューは、各ステートメントの後にフラッシュされます。  
  
 次の表は、ドライバーによって使用される**SQLError**引数と戻り値を示しています。  
  
|引数|戻り値の説明|  
|-----------------------|------------------------------|  
|*を使用します。*|エラーによって表される SQLSTATE の値。|  
|*エラー*|0 以外の値は[、Visual FoxPro ODBC ドライバーネイティブ エラー メッセージ](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)を示します。 値 0 は、ドライバによってエラーが検出され、適切な[ODBC エラー コード](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)にマップされたことを示します。|  
|*メッセージ*|ネイティブ エラーまたは ODBC エラーのテキスト。|  
|*メッセージ*|メッセージ・テキストの長さに ID の長さを加算した値。|  
  
 ドライバのエラーメッセージの詳細については、エラー[メッセージの概要 を](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md)参照してください。 この関数の詳細については *、ODBC プログラマ リファレンス*の[SQLError](../../odbc/reference/syntax/sqlerror-function.md)を参照してください。

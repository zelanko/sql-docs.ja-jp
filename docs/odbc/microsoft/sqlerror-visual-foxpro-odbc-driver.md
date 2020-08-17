---
description: SQLError (Visual FoxPro ODBC ドライバー)
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 09f901b72d292f962076bff2aa521c8214e8f0e7
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340258"
---
# <a name="sqlerror-visual-foxpro-odbc-driver"></a>SQLError (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: コアレベル  
  
 前回のエラーに関するエラーまたは状態の情報を返します。 ドライバーは、 **SQLError**の呼び出し方法に応じて、 *hstmt*、 *hdbc*、および*henv*引数に対して返される可能性のあるスタックまたはエラーの一覧を保持します。 エラーキューは、各ステートメントの後にフラッシュされます。  
  
 次の表では、ドライバーで使用される **SQLError** 引数と戻り値について説明します。  
  
|SQLError 引数|戻り値の説明|  
|-----------------------|------------------------------|  
|*szSQLState*|エラーによって表される SQLSTATE の値。|  
|*Pfエラー*|0以外の値は、 [Visual FOXPRO ODBC ドライバーのネイティブエラーメッセージ](../../odbc/microsoft/visual-foxpro-odbc-driver-native-error-messages.md)を示します。 値が0の場合は、ドライバーによってエラーが検出され、適切な [ODBC エラーコード](../../odbc/microsoft/odbc-error-codes-visual-foxpro-odbc-driver.md)にマップされていることを示します。|  
|*szErrorMsg*|ネイティブエラーまたは ODBC エラーのテキスト。|  
|*pcbErrorMsg*|メッセージテキストの長さと識別子の長さ。|  
  
 ドライバーのエラーメッセージの詳細については、「 [エラーメッセージの概要](../../odbc/microsoft/error-messages-visual-foxpro-odbc-driver.md)」を参照してください。 この関数の詳細については、 *ODBC プログラマーリファレンス*の「 [SQLError](../../odbc/reference/syntax/sqlerror-function.md) 」を参照してください。

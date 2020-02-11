---
title: SQLGetStmtOption (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetStmtOption function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 984a8b1d-f12c-420c-8be4-f555114c764b
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 5521fb11cad064cf487d38562f4146fd32587993
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898785"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: レベル1  
  
 ステートメントオプションの現在の設定を返します。  
  
|*FOption*|戻り値|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|32-現在のレコード番号のブックマークを表すビット整数値|  
|SQL_ROW_NUMBER|32-結果セット内の現在の行の位置を指定するビット整数|  
|SQL_TRANSLATE_DLL|エラー: "ドライバーに対応していません"|  
  
 Visual FoxPro ODBC ドライバーには、変換 Dll がありません。  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md) 」を参照してください。

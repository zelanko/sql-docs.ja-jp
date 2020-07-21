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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2624783f7bd55903f5741c62190626e455a9096d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81295142"
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

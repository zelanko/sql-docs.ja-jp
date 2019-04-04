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
manager: craigg
ms.openlocfilehash: 373f5e13712ef7b0864401ea3d2c204cb03ebb09
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47647000"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックでには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の詳細については、該当するトピックを参照してください。 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)します。  
  
 サポート: 完全な  
  
 レベル 1 の ODBC API 準拠:  
  
 ステートメント オプションの現在の設定を返します。  
  
|*fOption*|戻り値|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|現在のレコード数のブックマークは、32 ビット整数値|  
|SQL_ROW_NUMBER|結果内の現在の行の位置を指定する 32 ビット整数の設定|  
|SQL_TRANSLATE_DLL|エラー:"Driver できません。"|  
  
 Visual FoxPro ODBC ドライバーには、翻訳の Dll がありません。  
  
 詳細については、[SQLGetStmtOption](../../odbc/reference/syntax/sqlgetstmtoption-function.md)で、 *ODBC プログラマ リファレンス*を参照してください。

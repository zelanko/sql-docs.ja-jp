---
title: をクリックします。マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295142"
---
# <a name="sqlgetstmtoption-visual-foxpro-odbc-driver"></a>SQLGetStmtOption (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 ステートメント オプションの現在の設定値を返します。  
  
|*Fオプション*|戻り値|  
|---------------|-------------|  
|SQL_GET_BOOKMARK|現在のレコード番号のブックマークである 32 ビット整数値|  
|SQL_ROW_NUMBER|結果セット内の現在の行の位置を指定する 32 ビットの整数|  
|SQL_TRANSLATE_DLL|エラー: "ドライバが使用できません"|  
  
 ビジュアル フォックスプロ ODBC ドライバーには、変換 DLL がありません。  
  
 詳細については *、ODBC プログラマ リファレンス*の[「SQLGetStmtOption」](../../odbc/reference/syntax/sqlgetstmtoption-function.md)を参照してください。

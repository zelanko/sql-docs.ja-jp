---
title: SQL 拡張フェッチ (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExtendedFetch function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b28af112-fb47-4143-b11e-3b743b2ae1b8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3ecff538198a2b517f980cc63acfc97d29a9f162
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298652"
---
# <a name="sqlextendedfetch-visual-foxpro-odbc-driver"></a>SQLExtendedFetch (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 2  
  
 [SQLFetch](../../odbc/microsoft/sqlfetch-visual-foxpro-odbc-driver.md)と似ていますが、各列の配列を使用して複数の行を返します。 結果セットは前方スクロール可能であり、カーソルが前方スクロールではなく静的に定義されている場合は、後方スクロール可能にできます。  
  
 既定では、ビジュアル フォックスプロ ODBC ドライバーは、FoxPro テーブルで削除済みとしてマークされた行を返しません。 削除対象としてマークされているが、テーブルからまだ削除されていない行は、結果セットカーソルに含まれません。 この動作は[、SET DELETED](../../odbc/microsoft/set-deleted-command.md)コマンドを使用して変更できます。  
  
 詳細については *、ODBC プログラマ リファレンス*の[「SQLExtendedFetch」](../../odbc/reference/syntax/sqlextendedfetch-function.md)を参照してください。

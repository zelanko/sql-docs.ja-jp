---
title: SQL 特殊列 (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSpecialColumns function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: b72a978d-6a60-475a-b7d9-c424d77bbe30
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 96b439674c8bda3494b4cefd0c1118602b537cd0
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299382"
---
# <a name="sqlspecialcolumns-visual-foxpro-odbc-driver"></a>SQLSpecialColumns (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 テーブル内の行を一意に識別する列の最適なセットを取得します。  
  
 ビジュアル フォックスプロ ODBC ドライバーは、FoxPro テーブルの主キーを構成する列を返します。 (SQL[プライマリキーを](../../odbc/microsoft/sqlprimarykeys-visual-foxpro-odbc-driver.md)参照してください。*fColType*を SQL_ROWVER に設定して呼び出した場合、列は返されません。 **SQLSpecialColumns は**[、 データベース](../../odbc/microsoft/visual-foxpro-terminology.md)であるデータ ソースに対してのみ機能します。  
  
 詳細については *、ODBC プログラマ リファレンス*の[SQLSpecialColumns](../../odbc/reference/syntax/sqlspecialcolumns-function.md)を参照してください。

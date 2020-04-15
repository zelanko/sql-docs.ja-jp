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
- SQLGetTypeInfo function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5f25e20b-a4ef-42da-aeb6-00e0510fb1cc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 23db0350f0f7271f85e2bc5c6a9e6c8767443a85
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299522"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 データ ソースでサポートされているデータ型に関する情報を返します。 ドライバーは、SQL 結果セット内の情報を返します。 次の表は、ODBC データ型と対応する Visual FoxPro データ型の一覧です。  
  
|ODBC 型|ビジュアルフォックスプロタイプ|  
|---------------|------------------------|  
|SQL_BIGINT|サポートされていません。 64 ビットビジュアル フォックスプロタイプはありません。|  
|SQL_BIT|論理|  
|SQL_CHAR|文字|  
|SQL_DATE|Date|  
|SQL_DECIMAL|数値|  
|SQL_DOUBLE|Double|  
|SQL_FLOAT|Double|  
|SQL_INTEGER|Integer|  
|SQL_LONGVARBINARY|メモ(バイナリ)|  
|SQL_LONGVARCHAR|メモ|  
|SQL_NUMERIC|数値*、通貨、浮動小数|  
|SQL_REAL|Double|  
|SQL_SMALLINT|Integer|  
|SQL_TIME|サポートされていません。 ビジュアル フォックスプロ*の時間*の種類はありません。|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|Integer|  
|SQL_VARBINARY|メモ(バイナリ)*,一般|  
|SQL_VARCHAR|文字|  
  
 *デフォルトタイプ  
  
 ビジュアル FoxPro データ型の詳細については、「[テーブルの作成](../../odbc/microsoft/create-table-sql-command.md)」を参照してください。 この関数の詳細については *、ODBC プログラマ リファレンス*の「 [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) 」を参照してください。

---
title: SQLGetTypeInfo (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: f29be5e03a6cc9c1c91809db2b8ec7c686e90f11
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "67898628"
---
# <a name="sqlgettypeinfo-visual-foxpro-odbc-driver"></a>SQLGetTypeInfo (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: レベル1  
  
 データソースでサポートされているデータ型に関する情報を返します。 ドライバーは、SQL 結果セットの情報を返します。 次の表に、ODBC データ型と、対応する Visual FoxPro データ型の一覧を示します。  
  
|ODBC の種類|Visual FoxPro の種類|  
|---------------|------------------------|  
|SQL_BIGINT|サポートされていません。 64ビットの Visual FoxPro の種類がありません。|  
|SQL_BIT|論理|  
|SQL_CHAR|Character|  
|SQL_DATE|Date|  
|SQL_DECIMAL|数値|  
|SQL_DOUBLE|DOUBLE|  
|SQL_FLOAT|DOUBLE|  
|SQL_INTEGER|整数|  
|SQL_LONGVARBINARY|メモ (バイナリ)|  
|SQL_LONGVARCHAR|メモ|  
|SQL_NUMERIC|Numeric *、Currency、Float|  
|SQL_REAL|DOUBLE|  
|SQL_SMALLINT|整数|  
|SQL_TIME|サポートされていません。 Visual FoxPro の*時刻*型はありません。|  
|SQL_TIMESTAMP|DateTime|  
|SQL_TINYINT|整数|  
|SQL_VARBINARY|メモ (バイナリ) *、全般|  
|SQL_VARCHAR|Character|  
  
 * 既定の型  
  
 Visual FoxPro のデータ型の詳細については、「 [CREATE TABLE](../../odbc/microsoft/create-table-sql-command.md)」を参照してください。 この関数の詳細については、 *ODBC プログラマーリファレンス*の「 [SQLGetTypeInfo](../../odbc/reference/syntax/sqlgettypeinfo-function.md) 」を参照してください。

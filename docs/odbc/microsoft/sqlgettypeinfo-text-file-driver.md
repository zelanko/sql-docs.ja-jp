---
title: テキスト ファイル ドライバの取得方法 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLGetTypeInfo function [ODBC], Text File Driver
- text file driver [ODBC], SQLGetTypeInfo
ms.assetid: 05a58975-093c-4bd9-bd72-b5f0026a6e36
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7b70b58e4760959db102450b5f8b7beed042df95
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81295002"
---
# <a name="sqlgettypeinfo-text-file-driver"></a>SQLGetTypeInfo (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **SQLGetTypeInfo**によって生成されるテーブルで返される型 (TYPE_NAME) の名前は、データ ソースで最も一般的に使用される名前になります。  
  
 SQL_ALL_EXCEPT_LIKEは、バイト、カウンター、倍精度、単精度、長整数型、および短いデータ型の SEARCHABLE 列に返されます。 (LIKE 機能は、ODBC 正規変換関数を使用して値を文字に変換し、比較を実行することによって実現できます。  
  
 テキスト ドライバーを使用すると **、SQLGetTypeInfo**は、テキスト データ型 (CHAR と LONGCHAR) のCASE_SENSITIVE値を返しますが、データ型が実際には大文字と小文字を区別します。

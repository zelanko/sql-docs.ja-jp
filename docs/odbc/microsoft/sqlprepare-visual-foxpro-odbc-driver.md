---
title: 準備 (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrepare function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 0c4cb5a4-9729-4b2e-a0c6-52027b92e8fc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 14c9358d04e539eb2c77a00e195e8216cd0f5496
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301558"
---
# <a name="sqlprepare-visual-foxpro-odbc-driver"></a>SQLPrepare (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: コア レベル  
  
 ステートメントの最適化と実行方法を計画して、SQL ステートメントを準備します。 SQL ステートメントは[、SQLExecDirect](../../odbc/microsoft/sqlexecdirect-visual-foxpro-odbc-driver.md)によって実行するためにコンパイルされます。  
  
 テーブル、ビュー、またはフィールド名にスペースが含まれている場合は、名前を引用符 (') で囲みます。 たとえば、データベースに My Table という名前のテーブルとフィールドの [マイ フィールド] が含まれている場合、識別子の各要素を次のように囲みます。  
  
```  
SELECT * FROM `My Table`.`My Field`  
```  
  
 詳細については *、『ODBC プログラマ リファレンス*』の[SQLPrepare](../../odbc/reference/syntax/sqlprepare-function.md)を参照してください。

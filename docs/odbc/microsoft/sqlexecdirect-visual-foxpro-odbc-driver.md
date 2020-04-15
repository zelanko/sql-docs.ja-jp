---
title: SQLExec ダイレクト (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLExecDirect function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 5004060f-8510-4018-87a4-d41789e69d3e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 40c0a3404a3e7a9a67b6f71d197343eddb417955
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298672"
---
# <a name="sqlexecdirect-visual-foxpro-odbc-driver"></a>SQLExecDirect (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: コア レベル  
  
 新しい[、準備可能な SQL ステートメント](../../odbc/microsoft/visual-foxpro-terminology.md)を実行します。 Visual FoxPro ODBC ドライバーは、パラメーターがステートメントに存在する場合は、パラメーター マーカー変数の現在の値を使用します。  
  
 一度に複数の SQL ステートメントをサブミットするバッチ・コマンドを作成するには、セミコロン (;)を使用して、バッチ内の各 SQL ステートメントを区切ります。  
  
 テーブル、ビュー、またはフィールド名にスペースが含まれている場合は、名前を引用符で囲みます。 たとえば、データベースに My Table という名前のテーブルとフィールドの [マイ フィールド] が含まれている場合、識別子の各要素を次のように囲みます。  
  
```  
SELECT `My Table`.`Field1`, `My Table`.`Field2` FROM `My Table`  
```  
  
 詳細については *、ODBC プログラマ リファレンス*の[SQLExecDirect](../../odbc/reference/syntax/sqlexecdirect-function.md)を参照してください。

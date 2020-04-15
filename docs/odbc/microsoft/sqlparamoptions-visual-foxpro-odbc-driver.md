---
title: SQL パラム オプション (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLParamOptions function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 7f94a6e2-9c34-405c-b2b0-304d94269715
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: dd714ce7774265a2afd00d42894d644a516bc402
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299472"
---
# <a name="sqlparamoptions-visual-foxpro-odbc-driver"></a>SQLParamOptions (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 1  
  
 アプリケーションで[、SQLBindParameter](../../odbc/microsoft/sqlbindparameter-visual-foxpro-odbc-driver.md)によって割り当てられたパラメーターのセットに対して複数の値を指定できるようにします。 一連のパラメーターに複数の値を指定する機能は、一括挿入や、データ ソースが同じ SQL ステートメントをさまざまなパラメーター値で複数回処理する必要がある他の作業に役立ちます。 たとえば、アプリケーションでは INSERT**ステートメントに**関連付けられたパラメーターセットに 3 セットの値を指定し **、INSERT**ステートメントを 1 回実行して 3 つの挿入操作を実行できます。  
  
 詳細については *、ODBC プログラマ リファレンス*の[SQLParam オプション](../../odbc/reference/syntax/sqlparamoptions-function.md)を参照してください。

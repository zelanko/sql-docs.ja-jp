---
title: SQL トランスアクト (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTransact function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 92cf86c0-f7a8-44d7-b59f-a1342677440b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 3910f24578bcbc409a84573e994c0680ed5949b2
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299222"
---
# <a name="sqltransact-visual-foxpro-odbc-driver"></a>SQLTransact (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: コア レベル  
  
 接続に関連付けられたすべてのステートメント ハンドル *(hstmt*s) または環境ハンドル*henv*に関連付けられたすべての接続に対して、すべてのアクティブな操作に対してコミットまたはロールバック操作を要求します。 **SQLTransact**は[、 データベース](../../odbc/microsoft/visual-foxpro-terminology.md)であるデータ ソースに対してのみ機能します。  
  
 手動モードでコミットが失敗した場合、トランザクションはアクティブなままです。トランザクションをロールバックするか、コミット操作を再試行するかを選択できます。 自動トランザクション モードでコミット操作が失敗した場合、トランザクションは自動的にロールバックされます。トランザクションを非アクティブにすることはできません。  
  
 詳細については *、『ODBC プログラマ リファレンス*』の[SQLTransact](../../odbc/reference/syntax/sqltransact-function.md)を参照してください。

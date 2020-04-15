---
title: SQL プライマリキー (ビジュアル フォックスプロ ODBC ドライバー) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLPrimaryKeys function [ODBC], Visual FoxPro ODBC Driver
ms.assetid: 8dbe2903-efdc-45e0-a079-9e357c5fd81b
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 83631d22bd07017c4eba8f6af171443ab8c76d9c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81301547"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、ビジュアル フォックス プロ ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 サポート: フル  
  
 ODBC API 準拠: レベル 2  
  
 テーブルの主キーを構成する列名を返します。 **SQL プライマリキー**のビジュアル フォックスプロ ODBC ドライバーの実装は、次のように動作します。  
  
-   *引数を*無視*szTableOwner*します。  
  
-   [データベース](../../odbc/microsoft/visual-foxpro-terminology.md)であるデータ ソースに対してのみ機能します。 データ ソースが[空きテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリである場合、ドライバはエラー "Driver はこの関数をサポートしていません" を返します。  
  
 詳細については *、『ODBC プログラマ リファレンス*』の[SQLPrimaryKeys](../../odbc/reference/syntax/sqlprimarykeys-function.md)を参照してください。

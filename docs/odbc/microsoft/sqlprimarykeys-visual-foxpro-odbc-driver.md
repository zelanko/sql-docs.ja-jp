---
title: SQLPrimaryKeys (Visual FoxPro ODBC ドライバー) |Microsoft Docs
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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: e85e60cde86c9483e69a8c43de14ef64eb914119
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68030705"
---
# <a name="sqlprimarykeys-visual-foxpro-odbc-driver"></a>SQLPrimaryKeys (Visual FoxPro ODBC ドライバー)
> [!NOTE]  
>  このトピックには、Visual FoxPro ODBC ドライバー固有の情報が含まれています。 この関数の一般的な情報については、「 [ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)」の該当するトピックを参照してください。  
  
 サポート: 完全  
  
 ODBC API の準拠: レベル2  
  
 テーブルの主キーを構成する列名を返します。 Visual FoxPro ODBC ドライバーによる**Sqlprimarykeys**の実装は、次のように動作します。  
  
-   *Sztableowner*引数と*cbtableowner*引数は無視されます。  
  
-   [データベース](../../odbc/microsoft/visual-foxpro-terminology.md)であるデータソースに対してのみ機能します。 データソースが[フリーテーブル](../../odbc/microsoft/visual-foxpro-terminology.md)のディレクトリの場合、ドライバーは "ドライバーはこの機能をサポートしていません" というエラーを返します。  
  
 詳細については、 *ODBC プログラマーリファレンス*の「 [sqlprimarykeys](../../odbc/reference/syntax/sqlprimarykeys-function.md) 」を参照してください。

---
title: コネクト (エクセルドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Excel driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Excel Driver
ms.assetid: 285cb1ea-f461-4596-97f2-fc57af05dede
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 1108206bf38183887540b114fda5a1e913aa67d9
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307123"
---
# <a name="sqldriverconnect-excel-driver"></a>SQLDriverConnect (Excel ドライバー)
> [!NOTE]  
>  このトピックでは、Excel ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **データ ソース**(DSN) を作成せずにドライバーに接続することができます。  
  
 すべてのドライバの接続文字列では **、DSN** **、DBQ** **、FIL**の各キーワードがサポートされています。  
  
 次の表は、各ドライバに接続するために必要な最小キーワードを示し **、SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 ドライバID 値の完全な一覧については[、「SQLConfigDataSource](../../odbc/microsoft/odbc-jet-sqlconfigdatasource-excel-driver.md)」を参照してください。  
  
> [!NOTE]  
>  DbQ または DefaultDir が指定されていない場合、Microsoft Excel 3.0 または 4.0 ドライバー、ドライバーは、現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|Excel 3.0 または 4.0|ドライバ、ドライバ ID|ドライバー={マイクロソフトエクセルドライバー(*.xls)}。DBQ=c:\temp;ドライバー ID=278|  
|エクセル 5.0/7.0|ドライバ、ドライバ ID、DBQ|ドライバー={マイクロソフトエクセルドライバー(*.xls)}。DBQ=c:\temp\sample.xls;ドライバー ID=22|  
|マイクロソフトエクセル97以降|ドライバ、ドライバ ID、DBQ|ドライバー={マイクロソフトエクセルドライバー(*.xls)}。DBQ=c:\temp\sample.xls;ドライバー ID=790|

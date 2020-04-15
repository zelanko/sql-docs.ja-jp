---
title: コネクト接続 ( ドライバの使用 ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- DBase driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], dBASE Driver
ms.assetid: c837aa31-068e-4fa3-bc00-aae09bec21de
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 39d3d062ef8371ce37f812216cbb642d103eff98
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302923"
---
# <a name="sqldriverconnect-dbase-driver"></a>SQLDriverConnect (dBASE ドライバー)
> [!NOTE]  
>  このトピックでは、dBASE ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **データ ソース**(DSN) を作成せずにドライバーに接続することができます。  
  
 すべてのドライバの接続文字列では **、DSN** **、DBQ** **、FIL**の各キーワードがサポートされています。  
  
 Paradox ドライバを使用する場合、パスワードで保護されたファイルをユーザーが開いた後、他のユーザーは同じファイルを開くことができません。  
  
 次の表は、各ドライバに接続するために必要な最小キーワードを示し **、SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 ドライバID 値の完全な一覧については[、「SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-dbase-driver.md)」を参照してください。  
  
> [!NOTE]  
>  dBASEdriver に対して DBQ または DefaultDir が指定されていない場合、ドライバーは現行ディレクトリーに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|Dbase|ドライバ、ドライバ ID|ドライバー={マイクロソフト dBASE ドライバー (*.dbf)}DBQ=c:\temp;ドライバー ID=277|

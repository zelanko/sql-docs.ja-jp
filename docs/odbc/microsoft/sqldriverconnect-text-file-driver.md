---
title: SQL ドライバ接続 (テキスト ファイル ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Text File Driver
- text file driver [ODBC], SQLDriverConnect
ms.assetid: d7769021-bd18-4d8e-96e0-e184a82d6ca3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 2768669b7dbb2066de0acedd5711911be0eac8fa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307103"
---
# <a name="sqldriverconnect-text-file-driver"></a>SQLDriverConnect (テキスト ファイル ドライバー)
> [!NOTE]  
>  このトピックでは、テキスト ファイル ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **データ ソース**(DSN) を作成せずにドライバーに接続することができます。  
  
 すべてのドライバの接続文字列では **、DSN** **、DBQ** **、FIL**の各キーワードがサポートされています。  
  
 次の表は、各ドライバに接続するために必要な最小キーワードを示し **、SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 ドライバID 値の完全な一覧については[、「SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-text-file-driver.md)」を参照してください。  
  
> [!NOTE]  
>  テキスト ドライバーに対して DBQ または DefaultDir が指定されていない場合、ドライバーは現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|Text|Driver|ドライバー={マイクロソフトテキストドライバ (*.txt;\*.csv)}デフォルトディレクトリ=c:\temp|

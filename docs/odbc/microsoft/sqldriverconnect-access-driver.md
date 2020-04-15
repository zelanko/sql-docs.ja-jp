---
title: コネクト (アクセス ドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Access driver [ODBC], SQLDriverConnect
- SQLDriverConnect function [ODBC], Access Driver
ms.assetid: 9d133e9b-7545-464d-aa3c-677fa7e2a41d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7a679cbb16ece3f239b1d17daabc8a294b808287
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302913"
---
# <a name="sqldriverconnect-access-driver"></a>SQLDriverConnect (Access ドライバー)
> [!NOTE]  
>  このトピックでは、アクセス ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **データ ソース**(DSN) を作成せずにドライバーに接続することができます。  
  
 すべてのドライバの接続文字列では **、DSN** **、DBQ** **、FIL**の各キーワードがサポートされています。  
  
 **UID**キーワードおよび**PWD**キーワードもサポートされています。  
  
 PWD キーワードには特殊文字を含めることはできません **(SQLGetInfo**戻り値のSQL_SPECIAL_CHARACTERSを参照してください)。  
  
 次の表は、各ドライバに接続するために必要な最小キーワードを示し **、SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 ドライバID 値の完全な一覧については[、「SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-access-driver.md)」を参照してください。  
  
|Driver|必要なキーワード|使用例|  
|------------|-----------------------|--------------|  
|Microsoft Access|ドライバ,DBQ|ドライバー={アクセスドライバー (*.mdb)}DBQ=c:\\\temp\\\サンプル.mdb|

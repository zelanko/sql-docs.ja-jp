---
title: コネクト (パラドックスドライバ) |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLDriverConnect function [ODBC], Paradox Driver
- Paradox driver [ODBC], SQLDriverConnect
ms.assetid: c2ba486e-5e01-4e67-adb1-68511f5f0206
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 68171cfab2b65634433b107d829dd2a6e9b5c985
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81307113"
---
# <a name="sqldriverconnect-paradox-driver"></a>SQLDriverConnect (Paradox ドライバー)
> [!NOTE]  
>  このトピックでは、Paradox ドライバー固有の情報を提供します。 この関数の一般的な情報については[、ODBC API リファレンス](../../odbc/reference/syntax/odbc-api-reference.md)の該当するトピックを参照してください。  
  
 **データ ソース**(DSN) を作成せずにドライバーに接続することができます。  
  
 すべてのドライバの接続文字列では **、DSN** **、DBQ** **、FIL**の各キーワードがサポートされています。  
  
 **PWD**キーワードもサポートされています。 PWD キーワードには特殊文字を含めることはできません **(SQLGetInfo**戻り値のSQL_SPECIAL_CHARACTERSを参照してください)。  
  
 パスワードで保護されたファイルをユーザーが開いた後、他のユーザーは同じファイルを開くことができません。  
  
 次の表は、各ドライバに接続するために必要な最小キーワードを示し **、SQLDriverConnect**で使用されるキーワードと値のペアの例を示しています。 ドライバID 値の完全な一覧については[、「SQLConfigDataSource](../../odbc/microsoft/sqlconfigdatasource-paradox-driver.md)」を参照してください。  
  
> [!NOTE]  
>  PARADOX ドライバに対して DBQ または DefaultDir が指定されていない場合、ドライバは現在のディレクトリに接続します。  
  
|Driver|必要なキーワード|例|  
|------------|-----------------------|-------------|  
|パラドックス|ドライバ、ドライバ ID|ドライバー={マイクロソフトパラドックスドライバー (*.db)};DBQ=c:\temp;ドライバーID=26|

---
title: ドライバの種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- driver compatibility issues [ODBC]
- ODBC drivers [ODBC], backward compatibility
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
ms.assetid: 864c53c1-b68a-48b6-b6bc-5ecb520bb9dc
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: de6d8e1473f127d28c69969e0fc298afd69d3023
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304873"
---
# <a name="types-of-drivers"></a>ドライバーの種類
ODBC ドライバは、次のように分類できます。  
  
-   **32 ビット ODBC 2。**  
     ** _x_ドライバ**A 32 ビット ドライバ:  
  
    -   ODBC *2.x*関数のみをエクスポートします。  
  
    -   動作の変更に対する ODBC *2.x*の動作を示します。  
  
-   **ISOとオープングループ準拠ドライバ**次の 32 ビット ドライバー。  
  
    -   オープングループまたは ISO CLI ドキュメントに記載されているすべての関数をエクスポートします。 これには、ODBC で非推奨になる関数が含まれます。  
  
    -   動作の変更に対する ODBC 3.0 の動作を示します。  
  
    -   必ずしも ODBC 3.0 ドライバ マネージャを通過しません。  
  
-   **ODBC 3.0 ドライバ**次の 32 ビット ドライバー。  
  
    -   ODBC 3.0 から非推奨関数を引いた関数のみをエクスポートします。  
  
    -   SQL_ATTR_APP_ODBC_VERSION環境属性に基づいて、動作の変更に関して ODBC *2.x*の動作または ODBC 3.0 の動作を示すことができます。  
  
-   **ODBC 3.5 (またはそれ以降) ANSI ドライバー**次の 32 ビット ドライバー。  
  
    -   ODBC 3.5 から非推奨関数を引いた関数のみをエクスポートします。  
  
    -   ODBC *2.x*の動作、ODBC 3.0 の動作、またはSQL_ATTR_APP_ODBC_VERSION環境属性に基づく動作の変更に関する ODBC 3.5 の動作を示すことができます。  
  
-   **ODBC 3.5 (またはそれ以降) ユニコードドライバ**次の 32 ビット ドライバー。  
  
    -   ODBC 3.5 ANSI ドライバのすべての機能をサポートします。  
  
    -   すべての ODBC 文字列 API のユニコード バージョンをエクスポートします。  
  
    -   データ ソースに Unicode データを格納および処理できます。  
  
> [!NOTE]  
>  16 ビット ODBC ドライバーは、ODBC *3.x*ドライバー マネージャーで直接は動作しません。 ただし、16 ビット ドライバーは 2.0 ODBC ドライバー マネージャーで動作する可能性があります。 *3.x*

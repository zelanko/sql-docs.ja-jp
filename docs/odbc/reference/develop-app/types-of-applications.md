---
title: アプリケーションの種類 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: f14326c9cec1eb89e431154c91b680e4688fcdfa
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305533"
---
# <a name="types-of-applications"></a>アプリケーションの種類
ODBC アプリケーションは、次のように分類できます。  
  
-   **純粋な ODBC 2。**  
     ** _x_アプリケーション**A 32 ビット アプリケーション:  
  
    -   ODBC 2 のみを呼び出します。*x*関数 (ODBC 1.0 関数**SQLSetParam**を含む)。 これらには、ODBC 1 が含まれます。32 ビットに移植された*x*アプリケーション。  
  
    -   ODBC 2 を想定しています。動作が変更された機能の*x*動作。 (詳細については[、「動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)」を参照してください)。  
  
    -   ODBC 3.5 ヘッダーを使用して再コンパイルされていません。  
  
-   **純粋な ODBC 2。**  
     **_x_再コンパイルされたアプリケーション**A 純粋な ODBC 2。ODBCVER=0x0250 を設定して、ODBC 3.5 ヘッダー ファイルを使用して再コンパイルされた*x*アプリケーション。  
  
-   **純粋な ODBC 2。**  
     **_x_ユニコードアプリケーション**A純粋なODBC 2。*x*は Unicode 準拠で、SQL_WCHARデータ型を使用する再コンパイル済みアプリケーションです。  
  
-   **純粋なオープングループと ISO**-**準拠の ODBC アプリケーション**A 32 ビット アプリケーション:  
  
    -   オープングループまたは ISO CLI 標準で定義されている関数を呼び出します。 (これらの関数には、非推奨の 3.0 関数が含まれている場合があります)。  
  
    -   Unicode データ型を使用しません。  
  
    -   動作が変更された機能に対して ODBC 3.0 の動作が予想されます。  
  
-   **純粋な ODBC 3.0 アプリケーション**次の 32 ビット アプリケーション。  
  
    -   3.0 ヘッダーでコンパイルされます。  
  
    -   非推奨の ODBC 3.0 関数を呼び出します。  
  
    -   動作が変更された機能に対して ODBC 3.0 の動作が予想されます。  
  
-   **純粋な ODBC 3.5 アプリケーション**次の 32 ビットまたは 64 ビット アプリケーション。  
  
    -   Unicode データ型を使用する場合があります。  
  
    -   非推奨の ODBC 3.5 関数を呼び出します。  
  
    -   動作が変更されたフィーチャに対して ODBC 3.5 の動作が予想されます。  
  
-   **純粋な ODBC 3.8 (またはそれ以降) アプリケーション**次の 32 ビットまたは 64 ビット のアプリケーション。  
  
    -   Unicode データ型を使用する場合があります。  
  
    -   非推奨の ODBC 3.8 関数を呼び出します。  
  
    -   動作が変更された機能に対して ODBC 3.8 の動作が予想されます。  
  
-   **置換アプリケーション**次の 32 ビットまたは 64 ビット アプリケーション。  
  
    -   重複した機能に対する新しい動作を実装します。  
  
    -   新しい機能を、条件付きコード内でのみ、新しいバージョンの ODBC で使用します。  
  
    -   動作の変更を処理する条件コードが限定されたか、ODBC アプリケーションの以前のバージョンとして登録されています。

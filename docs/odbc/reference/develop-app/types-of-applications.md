---
title: アプリケーションの種類 |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- upgrading applications [ODBC], application types
- backward compatibility [ODBC], application and driver compatibility
- compatibility [ODBC], application and driver compatibility
- application upgrades [ODBC], application types
- application compatibility issues [ODBC]
ms.assetid: d346a64e-a32c-4153-a40f-5b53c2f57ef2
caps.latest.revision: 9
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 604ab31b47c5c7b0750253ccd50300f143f63c61
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="types-of-applications"></a>アプリケーションの種類
ODBC アプリケーションは、次のように分類できます。  
  
-   **純粋な ODBC 2 です。**  
     ***x*アプリケーション**32 ビット アプリケーションです。  
  
    -   ODBC 2 だけを呼び出します。*x*関数 (ODBC 1.0 関数を含む**SQLSetParam**)。 これらには、ODBC 1 が含まれます。*x* 32 ビットへ移植されたアプリケーション。  
  
    -   ODBC 2 が必要です。*x*の動作の変更があった機能の動作です。 (を参照してください[動作の変更](../../../odbc/reference/develop-app/behavioral-changes.md)詳細についてはします)。  
  
    -   再コンパイルされていない ODBC 3.5 ヘッダー。  
  
-   **純粋な ODBC 2 です。**  
     ***x*アプリケーションの再コンパイル**純粋な ODBC 2 *。x*が再コンパイルされた ODBC 3.5 ヘッダー ファイルを使用してアプリケーション 0x0250 = ODBCVER を設定します。  
  
-   **純粋な ODBC 2 です。**  
     ***x* Unicode アプリケーション**純粋な ODBC 2 *。x*は、Unicode 準拠、SQL_WCHAR データ型を使用してアプリケーションを再コンパイルします。  
  
-   **純粋なグループと ISO**–**準拠 ODBC アプリケーション**32 ビット アプリケーションです。  
  
    -   グループを開くまたは ISO CLI 標準で定義された関数を呼び出します。 (これらの関数は、使用されなくなった 3.0 関数を含めることがあります)  
  
    -   Unicode データ型を使用しません。  
  
    -   動作の変更があった機能 ODBC 3.0 の動作を想定しています。  
  
-   **純粋な ODBC 3.0 アプリケーション**32 ビット アプリケーションです。  
  
    -   3.0 ヘッダーでコンパイルされます。  
  
    -   場合によっては非推奨ものも含めて、任意の ODBC 3.0 関数を呼び出します。  
  
    -   動作の変更があった機能 ODBC 3.0 の動作を想定しています。  
  
-   **純粋な ODBC 3.5 アプリケーション**32 または 64 ビット アプリケーションです。  
  
    -   Unicode データ型を使用することがあります。  
  
    -   場合によっては非推奨ものも含めて、任意の ODBC 3.5 関数を呼び出します。  
  
    -   動作の変更があった機能 ODBC 3.5 の動作を想定しています。  
  
-   **純粋な ODBC 3.8 (またはそれ以降) アプリケーション**32 ビットまたは 64 ビット アプリケーションです。  
  
    -   Unicode データ型を使用することがあります。  
  
    -   場合によっては非推奨ものも含めて、任意の ODBC 3.8 関数を呼び出します。  
  
    -   動作の変更があった機能の ODBC 3.8 動作を想定しています。  
  
-   **アプリケーションの置き換え**32 または 64 ビット アプリケーションです。  
  
    -   重複している機能の新しい動作を実装します。  
  
    -   条件付きコード内でのみ ODBC の以降のバージョンの新機能を使用します。  
  
    -   動作の変更を処理する条件付きコードが制限されているまたは以前のバージョンの ODBC アプリケーションに登録されています。

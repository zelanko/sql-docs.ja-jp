---
title: 診断処理ルール |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- SQLGetDiagField function [ODBC], diagnostic handling rules
- SQLGetDiagRec function [ODBC], diagnostic handling rules
- diagnostic information [ODBC], SqlGetDiagRec
ms.assetid: 74387c3a-d6b3-4c35-b209-b9612602b20a
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 9f7f9d19a5a369e9da0efbc0d62f8e556b0597c1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305843"
---
# <a name="diagnostic-handling-rules"></a>診断の処理規則
次の規則は **、SQLGetDiagRec**および**SQLGetDiagField**での診断処理を制御します。  
  
 すべての ODBC コンポーネントについて:  
  
-   別の ODBC コンポーネントから受け取ったエラーや警告を置換、変更、またはマスクすることはできません。  
  
-   別の ODBC コンポーネントから診断メッセージを受信したときに、ステータス レコードを追加できます。 追加されたレコードは、元のメッセージに実情報値を追加する必要があります。  
  
 データ ソースを直接インターフェイスする ODBC コンポーネントの場合:  
  
-   ベンダー識別子、コンポーネント識別子、データ ソースの識別子の先頭に、データ ソースから受信する診断メッセージを付ける必要があります。  
  
-   データ ソースのネイティブ エラー コードを保持する必要があります。  
  
-   データ ソースの診断メッセージを保持する必要があります。  
  
 データ ソースに関係なくエラーまたは警告を生成する ODBC コンポーネントの場合:  
  
-   エラーまたは警告に対して正しい SQLSTATE を指定する必要があります。  
  
-   診断メッセージのテキストを生成する必要があります。  
  
-   ベンダー識別子とコンポーネント識別子の前に診断メッセージを付ける必要があります。  
  
-   ネイティブ エラー コードが使用可能で意味のある場合は、ネイティブ エラー コードを返す必要があります。  
  
 ドライバー マネージャーとインターフェイスする ODBC コンポーネントの場合:  
  
-   **出力**引数を初期化する必要**があります。**  
  
-   その関数が呼び出されたときに、診断情報を形式設定し **、SQLGetDiagRec**および**SQLGetDiagField**の出力引数として返す必要があります。  
  
 ドライバ マネージャ以外の ODBC コンポーネントの場合:  
  
-   ネイティブ・エラーに基づいて SQLSTATE を設定する必要があります。 ゲートウェイを使用しないファイル ベースのドライバーと DBMS ベースのドライバーの場合、ドライバーは SQLSTATE を設定する必要があります。 ゲートウェイを使用する DBMS ベースのドライバの場合、ODBC をサポートするドライバまたはゲートウェイが SQLSTATE を設定できます。

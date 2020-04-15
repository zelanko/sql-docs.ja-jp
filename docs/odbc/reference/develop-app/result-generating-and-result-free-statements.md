---
title: 結果生成および結果のないステートメント |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: fc94aabd7982fba5879519573980db03b1857ef6
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300092"
---
# <a name="result-generating-and-result-free-statements"></a>結果生成および結果解放ステートメント
SQL ステートメントは、次の 5 つのカテゴリに大きく分けることができます。  
  
-   **結果セット生成ステートメント**これらは、結果セットを生成する SQL ステートメントです。 たとえば **、SELECT**ステートメントです。  
  
-   **行数生成ステートメント**これらは、影響を受ける行の数を生成する SQL ステートメントです。 たとえば **、UPDATE**ステートメントまたは**DELETE**ステートメントを使用します。  
  
-   **データ定義言語 (DDL) ステートメント**これらは、データベースの構造を変更する SQL ステートメントです。 たとえば、**テーブルの作成**や**インデックスの削除**などです。  
  
-   **コンテキスト変更ステートメント**これらは、データベースのコンテキストを変更する SQL ステートメントです。 たとえば、SQL Server の**USE**ステートメントと**SET**ステートメントなどです。  
  
-   **管理ステートメント**これらは、データベース内の管理目的で使用される SQL ステートメントです。 たとえば **、GRANT**と**取り消**し 。  
  
 最初の 2 つのカテゴリの SQL ステートメントは、まとめて*結果生成ステートメント*と呼ばれます。 後者の 3 つのカテゴリの SQL ステートメントは、まとめて*結果のないステートメント*と呼ばれます。 ODBC は、結果生成ステートメントのみを含むバッチのセマンティクスを定義します。 これらのセマンティクスは大きく異なるため、データ ソースに固有です。 たとえば、SQL Server ドライバは、オブジェクトを削除してから、同じバッチ内で同じオブジェクトを参照または再作成することをサポートしていません。 したがって、このマニュアルで使用される*バッチ*という用語は、結果生成ステートメントのバッチのみを参照します。

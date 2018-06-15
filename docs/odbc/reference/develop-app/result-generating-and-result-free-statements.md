---
title: ステートメントの結果を生成して、結果のない |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- result-generating statements [ODBC]
- batches [ODBC], result-generating statements
- batches [ODBC], result-free statements
- SQL statements [ODBC], batches
- result-free statements [ODBC]
ms.assetid: 2f3475d1-3999-4dd8-aba2-a6e1299c95f8
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6d314aa68c02a227f84e6785b722f44dd68964d9
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32913727"
---
# <a name="result-generating-and-result-free-statements"></a>ステートメントの結果を生成して、結果のないステートメント
SQL ステートメントは、次の 5 つのカテゴリに疎分類できます。  
  
-   **結果セットを生成するステートメント**これらは、結果セットを生成する SQL ステートメント。 たとえば、**選択**ステートメントです。  
  
-   **行の数を生成するステートメント**これらは、影響を受けた行の数を生成した SQL ステートメント。 たとえば、**更新**または**削除**ステートメントです。  
  
-   **データ定義言語 (DDL) ステートメント**これらは、データベースの構造を変更する SQL ステートメント。 たとえば、 **CREATE TABLE**または**DROP INDEX**です。  
  
-   **ステートメントのコンテキストを変更する**これらは、データベースのコンテキストを変更する SQL ステートメント。 たとえば、**使用**と**設定**SQL Server でのステートメント。  
  
-   **管理ステートメント**これらは、データベースの管理の目的で使用する SQL ステートメント。 たとえば、 **GRANT**と**取り消す**です。  
  
 最初の 2 つのカテゴリ内の SQL ステートメントは、として総称*ステートメントの結果を生成する*です。 後者の 3 つのカテゴリ内の SQL ステートメントは、として総称*ステートメントの結果のない*です。 ODBC では、ステートメントの結果をもたらすだけを含むバッチのセマンティクスを定義します。 これらのセマンティクスは、大きく異なるし、データ ソース固有であるためです。 たとえば、オブジェクトを削除してを参照するか、同じバッチ内の同じオブジェクトを再作成するには、この SQL Server driver はサポートされません。 そのため、用語*バッチ*このマニュアルは結果を生成するのバッチのみを参照で使用されているステートメント。

---
title: ファイルベースドライバ |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- file-based drivers [ODBC]
- ODBC architecture [ODBC], drivers
- drivers [ODBC], file-based drivers
ms.assetid: d92e0c5c-d176-4282-bbe1-d449e2223d50
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 223bd838754f1d656ac71ae37926389097af3ea1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81306665"
---
# <a name="file-based-drivers"></a>ファイル ベースのドライバー
ファイル ベースのドライバーは、ドライバーが使用するスタンドアロン データベース エンジンを提供しない dBASE などのデータ ソースで使用されます。 これらのドライバーは、物理データに直接アクセスし、SQL ステートメントを処理するデータベース エンジンを実装する必要があります。 標準の方法として、ファイル ベースのドライバのデータベース エンジンは、最小 SQL 準拠レベルで定義された ODBC SQL のサブセットを実装します。この準拠レベルの SQL ステートメントの一覧については、「[付録 C: SQL 文法](../../odbc/reference/appendixes/appendix-c-sql-grammar.md)」を参照してください。  
  
 ファイル ベースドライバと DBMS ベースドライバを比較する場合、ファイルベースドライバは、データベースエンジンコンポーネントのために書き込みにくく、ネットワークピースがないため構成が複雑でなく、データベース企業が作成したほど強力なデータベースエンジンを書く時間が少ないため、強力ではありません。  
  
 次の図は、ファイル ベースのドライバの 2 つの異なる構成を示しています。  
  
 ![ファイル&#45;ベースのドライバの2つの構成](../../odbc/reference/media/pr06.gif "pr06")

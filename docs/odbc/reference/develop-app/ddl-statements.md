---
title: DDL ステートメント |Microsoft ドキュメント
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
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], DDL statements
- DDL statements [ODBC]
ms.assetid: 96ac9859-5976-4b06-ae1f-2fec3231e266
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: d077c86fb7a87658bc62d9530e9019e9f25da987
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ddl-statements"></a>DDL ステートメント
データ定義言語 (DDL) ステートメントは、Dbms によって大幅に異なります。 ODBC SQL ステートメントの最も一般的なデータ定義操作の定義: を作成して、テーブル、インデックス、およびビューを削除します。テーブルの変更付与して、権限の取り消し。 その他のすべての DDL ステートメントは、データ ソース固有です。 そのため、相互運用可能アプリケーションは、一部のデータ定義操作を実行できません。 一般に、これは問題ではなく、ほとんどの Dbms に付属の専用のデータベース管理ソフトウェアを左またはセットアップ プログラムは、ドライバーに付属のような操作は、高 DBMS に固有である傾向があり、最適なためです。  
  
 データ定義内の別の問題は、そのデータ型の名前は Dbms の間で大幅に異なります。 標準的なデータ型の名前を定義し、それらを DBMS に固有の名前に変換するためのドライバーを強制ではなく**SQLGetTypeInfo**アプリケーションを DBMS に固有のデータ型の名前を検出するための手段を提供します。 相互運用可能アプリケーションは作成し、変更テーブルに SQL ステートメントでこれらの名前を使用する必要があります。示した名前[付録 c: SQL 文法](../../../odbc/reference/appendixes/appendix-c-sql-grammar.md)、および[付録 d: データ型](../../../odbc/reference/appendixes/appendix-d-data-types.md)、例のみを示します。

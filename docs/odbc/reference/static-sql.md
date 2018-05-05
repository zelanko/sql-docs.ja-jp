---
title: 静的 SQL |Microsoft ドキュメント
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
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: ff2144ae69c48098324bc0b97ca9c33d5159adc3
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="static-sql"></a>静的 SQL
表示される埋め込み SQL [Embedded SQL 例](../../odbc/reference/embedded-sql-example.md)静的 SQL と呼ばれます。 プログラムでの SQL ステートメントは静的にするために、静的 SQL を呼び出されますつまり、プログラムを実行するたびに、変更しないでください。 前のセクションで説明した、プログラムの残りの部分はコンパイル時にこれらのステートメントがコンパイルされます。  
  
 静的な SQL はさまざまな状況に適しています、プログラムのデザイン時に、データ アクセスを決定できる任意のアプリケーションで使用できます。 たとえば、受注プログラムが常に同じステートメントを使用して、新しい注文を挿入し、航空券予約システムが常に同じステートメントを使ってから予約に使用可能な接続クライアント ライセンスの状態を変更します。 ホストの変数を使用して一般化するとこれらの各ステートメント別の販売注文の値を挿入することができ、異なる座席を予約することができます。 このようなステートメントは、プログラムにハードコーディングすることができますため、このようなプログラムのステートメントが解析、検証し、コンパイル時に 1 回だけは、最適化する必要があるという利点もあります。 これは、比較的高速のコードになります。

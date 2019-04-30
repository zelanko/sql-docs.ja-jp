---
title: 静的 SQL |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- static SQL [ODBC]
- SQL [ODBC], embedded SQL
- SQL statements [ODBC], embedded SQL
- SQL statements [ODBC], static SQL
- embedded SQL [ODBC]
- SQL [ODBC], static SQL
ms.assetid: 667d92ec-fed9-4028-81d4-bb9ba867356a
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cd82e2c3c44f05a27e9d14442d8d0fb58e1986cc
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63232048"
---
# <a name="static-sql"></a>静的 SQL
示すように埋め込まれた SQL [Embedded SQL 例](../../odbc/reference/embedded-sql-example.md)は静的 SQL と呼ばれます。 プログラムで SQL ステートメントは静的にするために、静的 SQL を呼び出されますプログラムを実行するたびに、変更しないでください。 前のセクションで説明した、プログラムの残りの部分はコンパイル時にこれらのステートメントがコンパイルされます。  
  
 静的 SQL は、多くの状況に適しており、プログラム デザイン時に、データ アクセスを決定できる任意のアプリケーションで使用できます。 たとえば、注文入力プログラムを常に新しい注文を挿入する、同じステートメントを使用し、航空券予約システムが常に同じステートメントを使用して、予約に使用可能なから持ち出しての状態を変更します。 これらの各ステートメントは、ホストの変数を使用して一般化するは販売注文に異なる値を挿入することし、別の座席を予約できます。 このようなステートメントは、プログラムにハードコードすることができますため、このようなプログラムは、ステートメントが解析、検証し、コンパイル時に 1 回だけに最適化する必要があるという利点があります。 これは、結果、比較的高速なコードです。

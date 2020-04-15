---
title: 静的 SQL |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 55710d8ea734cba86ae5e4daa725f75e94e65a64
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81279904"
---
# <a name="static-sql"></a>静的 SQL
[組み込み SQL の例に示されている組み込み SQL](../../odbc/reference/embedded-sql-example.md)は、静的 SQL と呼ばれます。 プログラム内の SQL ステートメントが静的であるため、静的 SQL と呼ばれます。つまり、プログラムが実行されるたびに変更されません。 前のセクションで説明したように、これらのステートメントは、プログラムの残りの部分がコンパイルされるときにコンパイルされます。  
  
 静的 SQL は、多くの状況でうまく機能し、プログラムの設計時にデータ アクセスを決定できるアプリケーションで使用できます。 たとえば、注文入力プログラムでは常に同じ明細書を使用して新しい注文を挿入し、航空会社の予約システムでは常に同じ明細書を使用して、座席のステータスを利用可能から予約済みに変更します。 これらのステートメントは、ホスト変数を使用して一般化されます。受注に異なる値を挿入することができ、異なるシートを予約することができます。 このようなステートメントはプログラム内でハードコーディングできるため、このようなプログラムには、コンパイル時にステートメントを解析、検証、および最適化する必要があるという利点があります。 これにより、比較的高速なコードが得られます。

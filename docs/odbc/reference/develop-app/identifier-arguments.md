---
title: 引数の識別子 |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- identifier arguments [ODBC]
- catalog functions [ODBC], arguments
- arguments in catalog functions [ODBC], identifier
ms.assetid: b9de003f-cb49-4dec-b528-14a5b8ff12bd
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: a4aed40268b5e9bb3dd3d4a37d43b45a7b6856ef
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="identifier-arguments"></a>識別子の引数
識別子の引数の文字列が引用符で囲まれた場合、ドライバーは先頭と末尾の空白を削除しは引用符で囲まれた文字列をそのまま処理します。 文字列が引用符で囲まれていない場合、ドライバーを削除末尾の空白およびフォールド文字列を大文字にします。 SQL_ERROR と SQLSTATE HY009 識別子の引数を null ポインターに設定を返します (null ポインターの無効な使用)、ない場合は、引数は、カタログ名のカタログがサポートされていません。  
  
 これらの引数は、SQL_ATTR_METADATA_ID ステートメント属性が SQL_TRUE に設定されている場合、識別子の引数として扱われます。 ここでは、アンダー スコア (_)、パーセント記号 (%) は、検索パターンの文字としてではなく、実際にどの文字として扱わされます。 これらの引数は、この属性は SQL_FALSE に設定されている場合、通常の引数または引数に応じての pattern 引数のいずれかとして扱われます。  
  
 特殊文字を含む識別子は、SQL ステートメントで引用符で囲む必要があります、ですが、必要がありますいない引用符で囲むカタログ関数の引数として渡されるときにカタログ関数に渡された引用符文字を解釈するためです。 たとえば、識別子を引用符文字とします (これは特定のドライバーとを通じて返される**SQLGetInfo**) は二重引用符 (") です。 最初に呼び出す**SQLTables** 2 番目の呼び出しはおそらくありません意図するものとは、"Accounts Payable"テーブルに関する情報を返すときに、Accounts Payable テーブルに関する情報を含む結果セットを返します。  
  
```  
SQLTables(hstmt1, NULL, 0, NULL, 0, "Accounts Payable", SQL_NTS, NULL, 0);  
SQLTables(hstmt2, NULL, 0, NULL, 0, "\"Accounts Payable\"", SQL_NTS, NULL, 0);  
```  
  
 引用符で囲まれた識別子は、Oracle で ROWID など、同じ名前の擬似列の場合は true。 列名を区別するために使用されます。 "ROWID"が、カタログ関数の引数で渡される場合がある場合に、関数は ROWID 擬似列を持つ機能します。 擬似列が存在しない場合、関数は"ROWID"列では動作します。 ROWID がカタログ関数の引数で渡されると場合、関数は、ROWID 列と連動します。  
  
 引用符で囲まれた識別子の詳細については、次を参照してください。[引用符で囲まれた識別子](../../../odbc/reference/develop-app/quoted-identifiers.md)です。

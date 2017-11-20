---
title: "識別子を引用符で囲まれた |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 07a0c8299fc4063e72353025465309c426a3a251
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="quoted-identifiers"></a>引用符で囲まれた識別子
SQL ステートメントで特殊文字または一致するキーワードを含む識別子を囲む必要があります*識別子引用符文字*; このような文字で囲まれた識別子と呼ばれる*の識別子を引用符で囲まれた*(とも呼ばれる*区切られた識別子*sql-92 で)。 次の Accounts Payable の識別子が引用符で囲まれたなど**選択**ステートメント。  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 ステートメントを解析するためには識別子を囲むためです。 たとえば、Accounts Payable が示されていない前のステートメントでは場合、パーサーはアカウントと Payable、2 つのテーブルがと、コンマで区切られたいなかった構文エラーを返します。 引用符文字の識別子はドライバー固有であり SQL_IDENTIFIER_QUOTE_CHAR オプションで取得した**SQLGetInfo**です。 SQL_SPECIAL_CHARACTERS と SQL_KEYWORDS のオプションでキーワードと特殊文字の一覧が取得されます**SQLGetInfo**です。  
  
 安全のため、相互運用可能アプリケーションは、Oracle では、ROWID 列などの擬似列を除くすべての識別子を多くの場合、見積もりです。 **SQLSpecialColumns**擬似列の一覧を返します。 また、オブジェクト名で特殊文字を表示する場所にアプリケーション固有の制限がある場合は相互運用可能なアプリケーションでは、これらの位置で特殊文字を使用してのことをお勧めします。


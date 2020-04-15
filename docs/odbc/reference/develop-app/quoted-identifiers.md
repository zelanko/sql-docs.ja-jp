---
title: 引用符で囲まれた識別子 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- interoperability of SQL statements [ODBC], quoted identifiers
- quoted identifiers [ODBC]
ms.assetid: 729ba55f-743b-4a04-8c39-ac0a9914211d
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 0c03fa8bbc059566288997b29c899056f26de252
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81282005"
---
# <a name="quoted-identifiers"></a>引用符で囲まれた識別子
SQL ステートメントでは、特殊文字または一致キーワードを含む*識別子は、識別子の引用符で*囲む必要があります。このような文字で囲まれた識別子は、*引用符で囲まれた識別子*(SQL-92 では*区切り識別子*とも呼ばれます) と呼ばれます。 たとえば、買掛金勘定の識別子は、次の**SELECT**ステートメントで引用されます。  
  
```  
SELECT * FROM "Accounts Payable"  
```  
  
 識別子を引用符で囲む理由は、文を解析可能にすることです。 たとえば、前のステートメントで買掛金勘定が引用されなかった場合、パーサーは取引先企業と買掛金勘定の 2 つのテーブルがあると仮定し、カンマで区切られていないという構文エラーを返します。 識別子の引用符文字は、ドライバー固有のものであり **、SQLGetInfo**のSQL_IDENTIFIER_QUOTE_CHAR オプションを使用して取得されます。 特殊文字とキーワードのリストは、 **SQLGetInfo**の SQL_SPECIAL_CHARACTERS および SQL_KEYWORDS オプションを使用して取得されます。  
  
 安全のため、相互運用可能なアプリケーションは、Oracle の ROWID 列など、疑似列以外のすべての識別子を引用することがよくあります。 **SQL 特殊列は**、疑似列のリストを返します。 また、オブジェクト名に特殊文字を使用できる場所にアプリケーション固有の制限がある場合は、相互運用可能なアプリケーションで特殊文字を使用しないことをお勧めします。

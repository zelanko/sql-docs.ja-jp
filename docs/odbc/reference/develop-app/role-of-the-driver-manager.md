---
title: ドライバー マネージャーの役割 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], SqlGetDiagField
- diagnostic information [ODBC], driver manager error checking
- SQLGetDiagField function [ODBC], driver manager
- SQLGetDiagRec function [ODBC], driver manager
- ODBC driver manager [ODBC]
- diagnostic information [ODBC], SqlGetDiagRec
- driver manager [ODBC], error checking
ms.assetid: 7b861c82-357e-4590-8074-45136e9ed15e
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ee3d704ea43125c3cd912a4e67d90bf5d50c733e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304303"
---
# <a name="role-of-the-driver-manager"></a>ドライバー マネージャーのロール
ドライバー マネージャーは、最終的に生成する状態レコードを返す順序を決定します。 特に、どのレコードが最高ランクを持ち、最初に返されるレコードを決定します。 ドライバーは、それが生成する状態レコードを並べ替える責任があります。 ドライバー マネージャーとドライバーの両方によって、状態レコードが投稿された場合、ドライバー マネージャーは、それらを順序付けします。 詳細については、「ステータス[レコードの順序](../../../odbc/reference/develop-app/sequence-of-status-records.md)」を参照してください。  
  
 ドライバ マネージャは、できるだけ多くのエラー チェックを実行します。 これにより、すべてのドライバーが同じエラーをチェックするのを防ができます。 たとえば、関数の引数が**SQLSetPos**の*操作*などの値の不連続の数を受け入れる場合、ドライバー マネージャーは、指定された値が有効であることを確認します。  
  
 次のセクションでは、ドライバー マネージャーによってチェックされる条件の種類について説明します。 それらは網羅的であることを意図したものではありません。ドライバー マネージャーが返す SQLSTATEs の完全な一覧については、各関数の「診断」セクションを参照してください。ドライバ マネージャが行った各チェックの説明は、文字 "(DM)" で始まります。 「付録 B: ODBC 状態遷移テーブル 」の[状態遷移表](../../../odbc/reference/appendixes/appendix-b-odbc-state-transition-tables.md)も参照してください。かっこ内に表示されるエラーは、ドライバー マネージャーによって検出されます。  
  
 このセクションでは、次のトピックを扱います。  
  
-   [引数の値のチェック](../../../odbc/reference/develop-app/argument-value-checks.md)  
  
-   [状態遷移の確認](../../../odbc/reference/develop-app/state-transition-checks.md)  
  
-   [一般的なエラー チェック](../../../odbc/reference/develop-app/general-error-checks.md)  
  
-   [ドライバー マネージャーのエラーと警告の確認](../../../odbc/reference/develop-app/driver-manager-error-and-warning-checks.md)

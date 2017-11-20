---
title: "記述子を明示的に割り当てられた |Microsoft ドキュメント"
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 7a4679fa6c6d2185f6e474407882080fea6b7c8a
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="explicitly-allocated-descriptors"></a>明示的に割り当てられた記述子
アプリケーションでは、いつでも、データベースに接続されている接続でのアプリケーションの記述子を明示的に割り当てることができます。 ステートメントの属性の処理を使用して、その記述子ハンドルを指定することによって**SQLSetStmtAttr**アプリケーションは、アプリケーションを暗黙的に割り当てを対応する代わりにその記述子を使用するドライバーに指示記述子。 アプリケーションでは、記述子の代替実装を指定できません。  
  
 アプリケーションは、1 つ以上のステートメントで明示的に割り当てられた記述子を関連付けることができます。 アプリケーションが実際には、データベースに接続されている場合にのみ、記述子は、明示的に割り当てられた記述子を指定できます。 アプリケーションまたは解放できます。 このような記述子明示的に、暗黙的の接続を解放します。


---
title: 記述子を明示的に割り当てられた |Microsoft ドキュメント
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
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7a9b34b2f83491c34d17f44da091dd7824bddb44
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="explicitly-allocated-descriptors"></a>明示的に割り当てられた記述子
アプリケーションでは、いつでも、データベースに接続されている接続でのアプリケーションの記述子を明示的に割り当てることができます。 ステートメントの属性の処理を使用して、その記述子ハンドルを指定することによって**SQLSetStmtAttr**アプリケーションは、アプリケーションを暗黙的に割り当てを対応する代わりにその記述子を使用するドライバーに指示記述子。 アプリケーションでは、記述子の代替実装を指定できません。  
  
 アプリケーションは、1 つ以上のステートメントで明示的に割り当てられた記述子を関連付けることができます。 アプリケーションが実際には、データベースに接続されている場合にのみ、記述子は、明示的に割り当てられた記述子を指定できます。 アプリケーションまたは解放できます。 このような記述子明示的に、暗黙的の接続を解放します。

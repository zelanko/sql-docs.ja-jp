---
title: 明示的に割り当てられた記述子 |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- descriptors [ODBC], allocating and freeing
- explicitly allocated descriptors [ODBC]
- allocating and freeing descriptors [ODBC]
ms.assetid: f590251d-56a6-4d58-a405-9e85e68fbc47
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: a9950bc23a1e75606316039e6c2d66f3dba59940
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81305693"
---
# <a name="explicitly-allocated-descriptors"></a>明示的に割り当てられた記述子
アプリケーションは、データベースに接続されているときはいつでも、接続上でアプリケーション記述子を明示的に割り当てることができます。 **SQLSetStmtAttr**を使用してステートメント ハンドルの属性として記述子ハンドルを指定することにより、アプリケーションは、対応する暗黙的に割り当てられたアプリケーション記述子の代わりに、その記述子を使用するようにドライバーに指示します。 アプリケーションは、代替実装記述子を指定できません。  
  
 アプリケーションは、明示的に割り当てられた記述子を複数のステートメントに関連付けることができます。 アプリケーションがデータベースに実際に接続されている場合にのみ、記述子を明示的に割り当てられた記述子にすることができます。 アプリケーションは、このような記述子を明示的に解放するか、または接続を解放することによって暗黙的に解放できます。

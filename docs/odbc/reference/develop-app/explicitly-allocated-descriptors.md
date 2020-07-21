---
title: 明示的に割り当てられた記述子 |Microsoft Docs
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
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81305693"
---
# <a name="explicitly-allocated-descriptors"></a>明示的に割り当てられた記述子
アプリケーションは、データベースに接続されているときはいつでも、アプリケーション記述子を接続に明示的に割り当てることができます。 **SQLSetStmtAttr**を使用して、その記述子ハンドルをステートメントハンドルの属性として指定することにより、アプリケーションは、暗黙的に割り当てられた対応アプリケーション記述子の代わりに、その記述子を使用するようにドライバーに指示します。 アプリケーションで代替の実装記述子を指定することはできません。  
  
 アプリケーションでは、明示的に割り当てられた記述子を複数のステートメントに関連付けることができます。 アプリケーションが実際にデータベースに接続されている場合にのみ、記述子を明示的に割り当てられた記述子にすることができます。 アプリケーションは、このような記述子を明示的に解放するか、接続を解放することによって暗黙的に解放することができます。

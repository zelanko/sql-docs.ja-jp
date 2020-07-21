---
title: 文字列に関する制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC desktop database drivers [ODBC]
- desktop database drivers [ODBC]
ms.assetid: ec1da65f-c69d-415d-bf75-8fda8aa2b39f
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 61f81ff3da882095a0a6c41bb5061addd497a5d2
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81306063"
---
# <a name="string-limitations"></a>文字列の制限事項
SQL ステートメント文字列の最大長は65000文字です。  
  
 Microsoft Access ドライバーが使用されている場合は、SQL-92 文字列定数 (二重引用符ではなく、単一引用符で囲む) のみがサポートされます。  
  
 文字が逆引用符で囲まれているかどうかにかかわらず、パイプ文字 (&#124;) を文字列内で使用することはできません。  
  
 相互運用性を最大にするために、アプリケーションは、引用符で囲まれた文字列を渡すのではなく、パラメーターに文字列を渡す必要があります。

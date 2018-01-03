---
title: "Jet: 日付、時刻、およびタイムスタンプのリテラル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 819b40dd4cc3e8481ed5e0795debca13c0779fd6
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: 日付、時刻、およびタイムスタンプのリテラル
相互運用性を最大にするため、アプリケーションは、エスケープ句の構文を使用して ODBC 正規の形式で日付リテラルを渡す必要があります。  
  
-   日付リテラルの {d '*値*'} ここで、 *valu*電子メール形式は、"yyyy mm dd"  
  
-   時刻リテラルの {t '*値*'} ここで、 *valu*"hh:mm:ss"形式では、e  
  
 タイムスタンプのリテラルの {ts'*値*'} ここで、 *valu*電子メールの形式は"- yyyy-mm-dd hh:mm:ss [. f.]"です。

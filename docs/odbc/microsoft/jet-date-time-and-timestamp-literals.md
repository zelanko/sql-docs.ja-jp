---
title: "Jet: 日付、時刻、およびタイムスタンプのリテラル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: microsoft
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
ms.openlocfilehash: 780b8ade4417aac4ee4b5a6472d0b3e14776cd10
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: 日付、時刻、およびタイムスタンプのリテラル
相互運用性を最大にするため、アプリケーションは、エスケープ句の構文を使用して ODBC 正規の形式で日付リテラルを渡す必要があります。  
  
-   日付リテラルの {d '*値*'} ここで、 *valu*電子メール形式は、"yyyy mm dd"  
  
-   時刻リテラルの {t '*値*'} ここで、 *valu*"hh:mm:ss"形式では、e  
  
 タイムスタンプのリテラルの {ts'*値*'} ここで、 *valu*電子メールの形式は"- yyyy-mm-dd hh:mm:ss [. f。..]"です。

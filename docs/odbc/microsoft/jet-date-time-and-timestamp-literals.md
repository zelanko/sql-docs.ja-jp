---
title: 'Jet: 日付、時刻、およびタイムスタンプのリテラル |Microsoft ドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cc36c46885a358e1ca453901fd72362ed1dbb32b
ms.sourcegitcommit: 2ddc0bfb3ce2f2b160e3638f1c2c237a898263f4
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: 日付、時刻、およびタイムスタンプのリテラル
相互運用性を最大にするため、アプリケーションは、エスケープ句の構文を使用して ODBC 正規の形式で日付リテラルを渡す必要があります。  
  
-   日付リテラルの {d '*値*'} ここで、 *valu*電子メール形式は、"yyyy mm dd"  
  
-   時刻リテラルの {t '*値*'} ここで、 *valu*"hh:mm:ss"形式では、e  
  
 タイムスタンプのリテラルの {ts'*値*'} ここで、 *valu*電子メールの形式は"- yyyy-mm-dd hh:mm:ss [. f.]"です。

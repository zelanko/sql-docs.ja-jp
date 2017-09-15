---
title: "Jet: 日付、時刻、およびタイムスタンプのリテラル |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
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
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: c1a98ca0b68198dada19e4ac81f8637798a99b95
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: 日付、時刻、およびタイムスタンプのリテラル
相互運用性を最大にするため、アプリケーションは、エスケープ句の構文を使用して ODBC 正規の形式で日付リテラルを渡す必要があります。  
  
-   日付リテラルの {d '*値*'} ここで、 *valu*電子メール形式は、"yyyy mm dd"  
  
-   時刻リテラルの {t '*値*'} ここで、 *valu*"hh:mm:ss"形式では、e  
  
 タイムスタンプのリテラルの {ts'*値*'} ここで、 *valu*電子メールの形式は"- yyyy-mm-dd hh:mm:ss [. f。..]"です。

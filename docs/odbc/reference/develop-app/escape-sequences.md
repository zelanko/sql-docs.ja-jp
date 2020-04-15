---
title: エスケープ シーケンス | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 5d9589230183b198cb7d59cf9739dab75625441e
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81298712"
---
# <a name="escape-sequences"></a>エスケープ シーケンス
ODBC は、日付、時刻、タイムスタンプ、および日時間隔リテラル、スカラー関数呼び出し **、LIKE**述語エスケープ文字、外部結合、およびプロシージャー呼び出しの標準文法を含むエスケープ・シーケンスを定義します。 相互運用可能なアプリケーションでは、可能な限りこれらのシーケンスを使用する必要があります。  
  
 ドライバーが日付、時刻、タイムスタンプ、または日時間隔リテラルのエスケープ シーケンスをサポートするかどうかを判断するには、アプリケーションは**SQLGetTypeInfo**を呼び出します。 データ ソースが日付、時刻、タイムスタンプ、または日時間隔のデータ型をサポートしている場合は、対応するエスケープ シーケンスもサポートする必要があります。 他のエスケープ シーケンスがサポートされているかどうかを確認するために、アプリケーションは**SQLGetInfo**を呼び出します。  
  
 詳細については、このセクション[の後半の「ODBC でのエスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」を参照してください。

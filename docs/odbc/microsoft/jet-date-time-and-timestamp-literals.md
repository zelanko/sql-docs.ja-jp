---
title: 'Jet: 日付、時刻、およびタイムスタンプのリテラル |マイクロソフトドキュメント'
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- literals [ODBC], SQL grammar
- SQL grammar [ODBC], literals
- date literals [ODBC]
- timestamp literals [ODBC]
- time literals [ODBC]
ms.assetid: 37db1ae1-ca4e-4cd8-9b47-7f1a38e7fcad
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 372b7c1dab1ad8ff000fb88729c3b02e05d4a21c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299938"
---
# <a name="jet-date-time-and-timestamp-literals"></a>Jet: 日付、時刻、およびタイムスタンプのリテラル
相互運用性を最大限に高めるには、アプリケーションはエスケープ句構文を使用して、ODBC 正規形式の日付リテラルを渡す必要があります。  
  
-   日付リテラルの場合、{d '*値*'}、valu e は "yyyy-mm-dd" の形式です。 *valu*  
  
-   時間リテラルの場合、{t '*値*'}、valu e は "hh:mm:ss" の形式です。 *valu*  
  
 タイムスタンプリテラル {ts '*value*'}の場合 *、valu*e は "yyyy-mm-dd hh:mm:ss[.f.]" の形式です。

---
title: サポートされている同時実行モデル (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 253a6dd86f6dc974d53dd151636bb8b8132e4d02
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81307718"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>サポートされているコンカレンシー モデル (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーでは、読み取り専用の*同時実行*がサポートされています。 アプリケーションでは、SQL_CONCUR_READ_ONLY の SQL_CONCURRENCY オプションを使用して[SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md)を呼び出すことができます。  
  
 詳細については、 [ODBC プログラマーズリファレンス](../../odbc/reference/odbc-programmer-s-reference.md)を参照してください。  
  
## <a name="read-only-concurrency"></a>読み取り専用の同時実行  
 カーソルを更新できません。  
  
## <a name="row-versioning"></a>行のバージョン管理 (row versioning)  
 基本的にはタイムスタンプサポート。更新時に行バージョンが比較されます。

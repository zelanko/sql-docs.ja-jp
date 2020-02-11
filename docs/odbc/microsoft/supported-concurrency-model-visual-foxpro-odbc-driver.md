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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 597d1022fa6946e0ae768cb9600a3f4534c67a25
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68080689"
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>サポートされているコンカレンシー モデル (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーでは、読み取り専用の*同時実行*がサポートされています。 アプリケーションでは、SQL_CONCUR_READ_ONLY の SQL_CONCURRENCY オプションを使用して[SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md)を呼び出すことができます。  
  
 詳細については、 [ODBC プログラマーズリファレンス](../../odbc/reference/odbc-programmer-s-reference.md)を参照してください。  
  
## <a name="read-only-concurrency"></a>読み取り専用の同時実行  
 カーソルを更新できません。  
  
## <a name="row-versioning"></a>行のバージョン管理 (row versioning)  
 基本的にはタイムスタンプサポート。更新時に行バージョンが比較されます。

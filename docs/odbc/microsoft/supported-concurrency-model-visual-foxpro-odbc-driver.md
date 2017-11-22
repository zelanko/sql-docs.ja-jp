---
title: "同時実行モデル (Visual FoxPro ODBC ドライバー) をサポート |Microsoft ドキュメント"
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
- Visual FoxPro ODBC driver [ODBC], concurrency
- concurrency models [ODBC]
- FoxPro ODBC driver [ODBC], concurrency
ms.assetid: c39ed963-3af1-4888-8631-6083692ddcd7
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: e06adec755df6c412d13fd8c2b892db8977b3a53
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="supported-concurrency-model-visual-foxpro-odbc-driver"></a>サポートされている同時実行モデル (Visual FoxPro ODBC ドライバー)
Visual FoxPro ODBC ドライバーをサポートしている*読み取り専用の同時実行*です。 アプリケーションが呼び出すことができます[SQLSetStmtOption](../../odbc/microsoft/sqlsetstmtoption-visual-foxpro-odbc-driver.md) SQL_CONCUR_READ_ONLY の SQL_CONCURRENCY オプションを使用します。  
  
 詳細については、次を参照してください。、 [ODBC プログラマ リファレンス](../../odbc/reference/odbc-programmer-s-reference.md)です。  
  
## <a name="read-only-concurrency"></a>読み取り専用の同時実行  
 カーソルは更新できません。  
  
## <a name="row-versioning"></a>行のバージョン管理 (row versioning)  
 基本的にタイムスタンプ、サポートでは、行のバージョンを比較して、更新時にします。

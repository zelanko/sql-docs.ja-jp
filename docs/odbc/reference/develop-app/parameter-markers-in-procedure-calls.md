---
title: "プロシージャ呼び出し内のパラメーター マーカー |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: reference
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
caps.latest.revision: "6"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 859b9b573ef17b2f874d0046742c668b35d2642f
ms.sourcegitcommit: 7f8aebc72e7d0c8cff3990865c9f1316996a67d5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/20/2017
---
# <a name="parameter-markers-in-procedure-calls"></a>プロシージャ呼び出し内のパラメーター マーカー
パラメーターを受け取るプロシージャを呼び出すときに、相互運用可能アプリケーションは、リテラル パラメーター値の代わりにパラメーター マーカーを使用する必要があります。 一部のデータ ソースは、プロシージャ呼び出しにリテラル パラメーター値の使用をサポートしていません。 パラメーターの詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。 プロシージャの呼び出しの詳細については、次を参照してください。[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)、このセクションで後述します。

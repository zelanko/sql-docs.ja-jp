---
title: "プロシージャ呼び出し内のパラメーター マーカー |Microsoft ドキュメント"
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
- SQL statements [ODBC], interoperability
- parameter markers [ODBC]
- interoperability of SQL statements [ODBC], parameter markers
ms.assetid: cda56f2b-6eec-4cbc-8dbb-36d8fa9f9216
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 206f9072242ba103bb39b01ead1393cc469a4700
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="parameter-markers-in-procedure-calls"></a>プロシージャ呼び出し内のパラメーター マーカー
パラメーターを受け取るプロシージャを呼び出すときに、相互運用可能アプリケーションは、リテラル パラメーター値の代わりにパラメーター マーカーを使用する必要があります。 一部のデータ ソースは、プロシージャ呼び出しにリテラル パラメーター値の使用をサポートしていません。 パラメーターの詳細については、次を参照してください。[ステートメント パラメーター](../../../odbc/reference/develop-app/statement-parameters.md)です。 プロシージャの呼び出しの詳細については、次を参照してください。[プロシージャ呼び出し](../../../odbc/reference/develop-app/procedure-calls.md)、このセクションで後述します。


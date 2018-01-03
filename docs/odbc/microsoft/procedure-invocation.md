---
title: "プロシージャの呼び出し |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.prod_service: drivers
ms.service: 
ms.component: odbc
ms.reviewer: 
ms.suite: sql
ms.technology: drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: "5"
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: 10af4e60b9fb30e8030d31f80c93681e73375e1e
ms.sourcegitcommit: cc71f1027884462c359effb898390c8d97eaa414
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/21/2017
---
# <a name="procedure-invocation"></a>プロシージャの呼び出し
使用して、ドライバーからプロシージャを呼び出すことが Microsoft Access ドライバーを使用すると、 **SQLExecDirect**または**SQLPrepare**関数に次の構文: {呼び出す*プロシージャ名* [(*パラメーター*[、*パラメーター*]...)]} です。 式が呼び出されるプロシージャのパラメーターとしてサポートされていないことに注意してください。  
  
 プロシージャ名には、ダッシュが含まれている場合、名前は逆引用符 (') で区切る必要があります。  
  
 前のステートメントを使用してパラメーター化クエリを呼び出すことができます。

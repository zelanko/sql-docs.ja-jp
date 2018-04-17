---
title: プロシージャの呼び出し |Microsoft ドキュメント
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
ms.topic: article
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 97e86097ecb5e9a58e5a37a0ec02646e9dcf855a
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="procedure-invocation"></a>プロシージャの呼び出し
使用して、ドライバーからプロシージャを呼び出すことが Microsoft Access ドライバーを使用すると、 **SQLExecDirect**または**SQLPrepare**関数に次の構文: {呼び出す*プロシージャ名* [(*パラメーター*[、*パラメーター*]...)]} です。 式が呼び出されるプロシージャのパラメーターとしてサポートされていないことに注意してください。  
  
 プロシージャ名には、ダッシュが含まれている場合、名前は逆引用符 (') で区切る必要があります。  
  
 前のステートメントを使用してパラメーター化クエリを呼び出すことができます。

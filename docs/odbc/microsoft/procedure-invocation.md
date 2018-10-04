---
title: プロシージャの呼び出し |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL grammar [ODBC], procedure invocation
- procedure invocation [ODBC]
ms.assetid: b9ff2c3a-2003-4832-adbe-08dd0f5ad948
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7b33bc399646a6d274c875abd36d53219a2814e1
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47833780"
---
# <a name="procedure-invocation"></a>プロシージャの呼び出し
使用して、ドライバーからプロシージャを呼び出すことが Microsoft Access ドライバーを使用すると、 **SQLExecDirect**または**SQLPrepare**関数に次の構文: {呼び出す*プロシージャ名* [(*パラメーター*[、*パラメーター*]...)]} です。 式が呼び出されたプロシージャにパラメーターとしてサポートされていないことに注意してください。  
  
 プロシージャ名には、ダッシュが含まれている場合、名前はバック引用符 (') で区切る必要があります。  
  
 前のステートメントを使用してパラメーター化クエリを呼び出すことができます。

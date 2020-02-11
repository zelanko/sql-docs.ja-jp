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
ms.openlocfilehash: bc37ef6d268dba71f8270909ea9c5b938ef3ee75
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68070491"
---
# <a name="procedure-invocation"></a>プロシージャの呼び出し
Microsoft Access ドライバーを使用する場合、次の構文で**SQLExecDirect**または**SQLPrepare**関数を使用して、プロシージャをドライバーから呼び出すことができます: {CALL *procedure-name* [(*parameter*[,*parameter*]...)]}。 式は、呼び出されたプロシージャのパラメーターとしてはサポートされていないことに注意してください。  
  
 プロシージャ名にダッシュが含まれている場合は、名前を引用符 (') で区切る必要があります。  
  
 パラメーター化されたクエリは、前のステートメントを使用して呼び出すことができます。

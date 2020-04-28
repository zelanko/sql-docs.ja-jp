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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 32617cdb753f5fc1b9c52520cb609d2902137b54
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81290773"
---
# <a name="procedure-invocation"></a>プロシージャの呼び出し
Microsoft Access ドライバーを使用する場合、次の構文で**SQLExecDirect**または**SQLPrepare**関数を使用して、プロシージャをドライバーから呼び出すことができます: {CALL *procedure-name* [(*parameter*[,*parameter*]...)]}。 式は、呼び出されたプロシージャのパラメーターとしてはサポートされていないことに注意してください。  
  
 プロシージャ名にダッシュが含まれている場合は、名前を引用符 (') で区切る必要があります。  
  
 パラメーター化されたクエリは、前のステートメントを使用して呼び出すことができます。

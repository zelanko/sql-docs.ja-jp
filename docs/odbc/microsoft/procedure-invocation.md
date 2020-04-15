---
title: プロシージャの呼び出し |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81290773"
---
# <a name="procedure-invocation"></a>プロシージャの呼び出し
Access ドライバーを使用する場合は、次の構文を使用*parameter*して**SQLExecDirect**または**SQLPrepare**関数を使用してドライバーからプロシージャを*procedure-name*呼び出すことができます。*parameter* 式は、呼び出されたプロシージャのパラメータとしてサポートされていません。  
  
 プロシージャ名にダッシュが含まれる場合、名前は引用符 (') で区切る必要があります。  
  
 パラメータ化クエリは、前のステートメントを使用して呼び出すことができます。

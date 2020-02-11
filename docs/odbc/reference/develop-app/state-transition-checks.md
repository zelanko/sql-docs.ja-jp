---
title: 状態遷移の確認 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- diagnostic information [ODBC], driver manager error checking
- state transition checks [ODBC]
- driver manager [ODBC], error checking
ms.assetid: 0706db7d-e125-4845-a13a-7fe4308f7360
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b337d317092ad6ae20cc91236d69c1314de96bce
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68107284"
---
# <a name="state-transition-checks"></a>状態遷移の確認
ドライバーマネージャーは、環境、接続、またはステートメントの状態が、呼び出される関数に適しているかどうかを確認します。 たとえば、 **SQLConnect**が呼び出されたときに、接続が割り当て済みの状態になっている必要があります。**Sqlexecute**が呼び出されると、ステートメントは準備済みの状態である必要があります。 ドライバーマネージャーは、状態遷移エラーの SQL_ERROR を返します。

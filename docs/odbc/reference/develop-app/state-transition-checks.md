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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 7dc1ddc126a2d652dfdb038cbb0e510f9735d7b0
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299707"
---
# <a name="state-transition-checks"></a>状態遷移の確認
ドライバーマネージャーは、環境、接続、またはステートメントの状態が、呼び出される関数に適しているかどうかを確認します。 たとえば、 **SQLConnect**が呼び出されたときに、接続が割り当て済みの状態になっている必要があります。**Sqlexecute**が呼び出されると、ステートメントは準備済みの状態である必要があります。 ドライバーマネージャーは、状態遷移エラーの SQL_ERROR を返します。

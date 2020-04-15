---
title: 状態遷移チェック |マイクロソフトドキュメント
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
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81299707"
---
# <a name="state-transition-checks"></a>状態遷移の確認
ドライバー マネージャーは、環境、接続、またはステートメントの状態が呼び出される関数に適切であることを確認します。 たとえば **、SQLConnect**が呼び出されたときに、接続が割り当てられた状態である必要があります。**ステートメントは、SQLExecute**が呼び出されたときに準備された状態にする必要があります。 ドライバー マネージャーは、状態の遷移エラーのSQL_ERRORを返します。

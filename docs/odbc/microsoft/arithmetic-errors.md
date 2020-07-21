---
title: 算術エラー |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- arithmetic errors [ODBC]
- desktop database drivers [ODBC], arithmetic errors
ms.assetid: 1c47bfac-7455-4487-b673-6b47d2a2d756
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ab1b472540d1978a6e7a06d94da7542cc641e999
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299902"
---
# <a name="arithmetic-errors"></a>算術エラー
ODBC ドライバーは、各行をフェッチするときに、SELECT ステートメント内の WHERE 句を評価します。 0除算や数値オーバーフローなどの算術エラーが発生する値が行に含まれている場合、ドライバーはすべての行を返しますが、算術エラーが発生している列に対してはエラーを返します。 ただし、挿入または更新する場合、最初の算術エラーが発生すると、ODBC ドライバーはデータの挿入または更新を停止します。

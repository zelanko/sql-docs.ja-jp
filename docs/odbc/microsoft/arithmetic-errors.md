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
author: MightyPen
ms.author: genemi
ms.openlocfilehash: 2e0880e1746b4b65070fb28bf8d83aadec301aa4
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68138180"
---
# <a name="arithmetic-errors"></a>算術エラー
ODBC ドライバーは、各行をフェッチするときに、SELECT ステートメント内の WHERE 句を評価します。 0除算や数値オーバーフローなどの算術エラーが発生する値が行に含まれている場合、ドライバーはすべての行を返しますが、算術エラーが発生している列に対してはエラーを返します。 ただし、挿入または更新する場合、最初の算術エラーが発生すると、ODBC ドライバーはデータの挿入または更新を停止します。

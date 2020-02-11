---
title: ORDER BY 句の制限事項 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC SQL grammar, ORDER BY clause limitations
- ORDER BY clause limitations [ODBC]
ms.assetid: fd4ddc7c-9c7e-4a0c-a781-e5427dfb2e18
author: MightyPen
ms.author: genemi
ms.openlocfilehash: b58afff444c09622027f50a87bd77fcd6ed45640
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68100784"
---
# <a name="order-by-clause-limitations"></a>ORDER BY 句の制限事項
SELECT ステートメントに GROUP BY 句と ORDER BY 句が含まれている場合、ORDER BY 句には、結果セット内の列、または GROUP BY 句の式のみを含めることができます。

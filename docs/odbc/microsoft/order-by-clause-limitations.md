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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e80fcf8b1f2e3e83182e3278b63bdb856c7189fe
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81292932"
---
# <a name="order-by-clause-limitations"></a>ORDER BY 句の制限事項
SELECT ステートメントに GROUP BY 句と ORDER BY 句が含まれている場合、ORDER BY 句には、結果セット内の列、または GROUP BY 句の式のみを含めることができます。

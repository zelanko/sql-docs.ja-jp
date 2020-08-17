---
description: ORDER BY 句の制限事項
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
ms.openlocfilehash: c116c40bdb16f3417b2b92295b0d13056dfcc18a
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/17/2020
ms.locfileid: "88340628"
---
# <a name="order-by-clause-limitations"></a>ORDER BY 句の制限事項
SELECT ステートメントに GROUP BY 句と ORDER BY 句が含まれている場合、ORDER BY 句には、結果セット内の列、または GROUP BY 句の式のみを含めることができます。

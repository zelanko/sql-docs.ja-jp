---
title: ExtendedAnsiSQL を使用して有効になっているデータの切り捨ての検出 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 95b7d538c2ace45b42c947b56ca5a5bd5f981ec5
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "62744271"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>ExtendedAnsiSQL を使用して有効になっているデータの切り捨ての検出
ExtendedAnsiSQL フラグがオンになっていると、アプリケーションが文字またはバイナリ列にデータを挿入すると、データは切り捨てられます、切り捨てが検出されます。 ExtendedAnsiSQL フラグがオフの場合、ODBC のデスクトップ データベース ドライバーの以前のバージョンが、警告なしのデータは切り捨てられます。

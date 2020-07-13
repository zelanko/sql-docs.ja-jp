---
title: ExtendedAnsiSQL | を使用したデータ切り捨て検出の有効化Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: ae1aa7a8a8b9ea2c3f3054717546506e660d5270
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81280701"
---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>ExtendedAnsiSQL を使用して有効になっているデータの切り捨ての検出
ExtendedAnsiSQL フラグが有効になっていて、アプリケーションが char 列またはバイナリ列にデータを挿入しているときに、データが切り捨てられると、切り捨てが検出されます。 ExtendedAnsiSQL フラグがオフになっている場合、以前のバージョンの ODBC Desktop データベースドライバのように、データは警告なしに切り捨てられます。

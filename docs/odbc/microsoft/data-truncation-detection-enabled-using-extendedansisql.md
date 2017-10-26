---
title: "ExtendedAnsiSQL を使用して有効になっているデータの切り捨て検出 |Microsoft ドキュメント"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- truncating data [ODBC]
- extendedANSISQL [ODBC], data truncation detection
ms.assetid: cec2359b-917d-4e1d-9625-5cd678b62f10
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 87affbd567a817ea119c405b64f96effe2358052
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="data-truncation-detection-enabled-using-extendedansisql"></a>ExtendedAnsiSQL を使用して有効になっているデータの切り捨ての検出
ExtendedAnsiSQL フラグがオンになっていると、アプリケーションが char 型または binary 型の列にデータを挿入するデータは切り捨てられます、ときに、切り捨てが検出されます。 ExtendedAnsiSQL フラグがオフの場合は、デスクトップの ODBC データベース ドライバーの以前のバージョンが、警告なしデータが切り捨てられます。


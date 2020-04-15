---
title: 序数でロード |マイクロソフトドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], loading by ordinal
- compatibility [ODBC], loading by ordinal
- loading by ordinal [ODBC]
ms.assetid: 337d90ab-68eb-4940-a2f3-f7d5693ee766
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 64bff8dcdd3802f75dc402c9ada60f82580aca5c
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81288722"
---
# <a name="loading-by-ordinal"></a>序数での読み込み
ODBC *2.x*では、序数による読み込みを行って、接続プロセスのパフォーマンスを向上させることができます。 ODBC *2.x*ドライバは、序数 199 でダミー関数をエクスポートします。ドライバ マネージャは、ドライバ マネージャが検出すると、名前ではなく序数で ODBC 関数のアドレスを解決します。 ODBC *2.x*ドライバーでは、この機能は引き続きサポートされていますが、ODBC *3.x*ドライバーではサポートされていません。

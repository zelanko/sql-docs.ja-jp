---
title: 序数での読み込み |Microsoft Docs
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
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 702e1fe58080cc370ab9a858c985a7744df85050
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63181333"
---
# <a name="loading-by-ordinal"></a>序数での読み込み
ODBC 2。*x*序数で読み込みを実行すると、接続処理のパフォーマンスを向上させる可能性があります。 ODBC 2。*x*ドライバー序数 199 でダミー関数をエクスポートする; 序数で、名前ではなく、ODBC 関数のアドレスは、ドライバー マネージャーが検出された場合、解決します。 この機能は、ODBC 2 for 引き続きサポートされます。*x*ドライバーは ODBC 3 のサポートされていませんが、*.x*ドライバー。

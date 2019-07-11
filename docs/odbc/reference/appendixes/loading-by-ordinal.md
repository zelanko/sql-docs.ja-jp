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
ms.openlocfilehash: ccecc541143e971d82a225e24e1c8caf6a03c32c
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67793187"
---
# <a name="loading-by-ordinal"></a>序数での読み込み
ODBC で*2.x*序数で読み込みを実行すると、接続処理のパフォーマンスを向上させる可能性があります。 ODBC *2.x*ドライバー序数 199 でダミー関数をエクスポートする; 序数で、名前ではなく、ODBC 関数のアドレスは、ドライバー マネージャーが検出された場合、解決します。 この機能は ODBC のサポートも*2.x*ドライバーは ODBC のサポートされていませんが、 *3.x*ドライバー。

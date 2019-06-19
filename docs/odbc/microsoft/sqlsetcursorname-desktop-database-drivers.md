---
title: SQLSetCursorName (デスクトップ データベース ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: e433e6aee341085965f361992fc8ea9ac8744353
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305631"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (デスクトップ データベース ドライバー)
ドライバーから位置指定更新をサポートします。 または、WHERE CURRENT OF によって削除されないため*カーソル名*構文、 **SQLSetCursorName**はサポートされていますが、位置指定更新は使用できません。 のみ使用できます、カーソル ライブラリを有効にして、アプリケーションを使用して**SQLExtendedFetch**します。

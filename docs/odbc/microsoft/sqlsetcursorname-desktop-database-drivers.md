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
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/01/2018
ms.locfileid: "47786260"
---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (デスクトップ データベース ドライバー)
ドライバーから位置指定更新をサポートします。 または、WHERE CURRENT OF によって削除されないため*カーソル名*構文、 **SQLSetCursorName**はサポートされていますが、位置指定更新は使用できません。 のみ使用できます、カーソル ライブラリを有効にして、アプリケーションを使用して**SQLExtendedFetch**します。

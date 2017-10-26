---
title: "SQLSetCursorName (デスクトップ データベース ドライバー) |Microsoft ドキュメント"
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
- SQLSetCursorName function [ODBC], Desktop Database Drivers
ms.assetid: 9bd7c87b-d99d-4e23-b2db-868d3b461c94
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: ee0a3a3d5aa5404a062a11410f0ae2adf072e240
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="sqlsetcursorname-desktop-database-drivers"></a>SQLSetCursorName (デスクトップ データベース ドライバー)
ドライバーが位置指定更新をサポートまたは、WHERE CURRENT OF を削除していないため*カーソル名*構文、 **SQLSetCursorName**はサポートされているが、位置指定更新は使用できません。 カーソル ライブラリが有効になっているアプリケーションを使用しているときにしか使用できません**SQLExtendedFetch**です。


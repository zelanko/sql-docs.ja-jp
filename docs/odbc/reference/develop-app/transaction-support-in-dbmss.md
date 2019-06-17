---
title: Dbms でのトランザクションのサポート |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 2fed5ea04e15002d31e35e25fac405a729929be8
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/15/2019
ms.locfileid: "63305686"
---
# <a name="transaction-support-in-dbmss"></a>DBMS でのトランザクションのサポート
特にデスクトップ データベース dBASE、Paradox、市販など、一部のデータベースでは、トランザクションはサポートされません。 トランザクションをサポートするデータベースの間でもはバリエーションの 1 つの SQL ステートメントの種類がトランザクションにすることができます。 詳細についてで SQL_TXN_CAPABLE オプションを参照して、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。

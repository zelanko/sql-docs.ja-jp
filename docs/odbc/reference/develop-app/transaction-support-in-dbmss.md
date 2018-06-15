---
title: Dbms でのトランザクションのサポート |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.suite: sql
ms.technology: connectivity
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 7095120f0a41bb4df5a3607c55abeb3a9da194f2
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32914807"
---
# <a name="transaction-support-in-dbmss"></a>Dbms でのトランザクションのサポート
特にデスクトップ データベース dBASE、Paradox、市販など、一部のデータベースは、トランザクションをサポートしていません。 トランザクションをサポートするデータベースの間でも、トランザクションにすることが SQL ステートメントの種類のバリエーションがあります。 詳細についてで SQL_TXN_CAPABLE オプションを参照して、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。

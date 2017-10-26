---
title: "Dbms でのトランザクションのサポート |Microsoft ドキュメント"
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
- interoperability [ODBC], transaction support
- transactions [ODBC], DBMS support
ms.assetid: 0fc2ae34-4748-4120-9fc3-bb28c8ed867e
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.workload: Inactive
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: 14c1519122484542b57e286c248c25c3fd6c0886
ms.contentlocale: ja-jp
ms.lasthandoff: 09/09/2017

---
# <a name="transaction-support-in-dbmss"></a>Dbms でのトランザクションのサポート
特にデスクトップ データベース dBASE、Paradox、市販など、一部のデータベースは、トランザクションをサポートしていません。 トランザクションをサポートするデータベースの間でも、トランザクションにすることが SQL ステートメントの種類のバリエーションがあります。 詳細についてで SQL_TXN_CAPABLE オプションを参照して、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明。


---
title: Dbms | でのトランザクションのサポートMicrosoft Docs
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
ms.openlocfilehash: 72353e9917996ecacdc5971b4a11f9c73718ba43
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68037631"
---
# <a name="transaction-support-in-dbmss"></a>DBMS でのトランザクションのサポート
一部のデータベース (特に、dBASE、Paradox、および Btrieve などのデスクトップデータベース) では、トランザクションはサポートされていません。 トランザクションをサポートするデータベース間でも、トランザクション内で使用できる SQL ステートメントの種類には違いがあります。 詳細については、 [SQLGetInfo](../../../odbc/reference/syntax/sqlgetinfo-function.md)関数の説明の SQL_TXN_CAPABLE オプションを参照してください。

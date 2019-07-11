---
title: C データ型の旧バージョンとの互換性 |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- backward compatibility [ODBC], C data types
- compatibility [ODBC], C data types
- data types [ODBC], backward compatibility
- C data types [ODBC], backward compatibility
ms.assetid: b1453a65-ae03-4061-b0cf-a8434d8bc40b
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: eecc56b357b580d791d5c7c7b3fc7b57e99654fd
ms.sourcegitcommit: 56b963446965f3a4bb0fa1446f49578dbff382e0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 07/11/2019
ms.locfileid: "67794139"
---
# <a name="backward-compatibility-of-c-data-types"></a>C データ型の下位互換性
SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT に置換された ODBC の符号付きと符号なし型。SQL_C_SSHORT、SQL_C_USHORT、SQL_C_SLONG、SQL_C_ULONG と SQL_C_STINYINT および SQL_C_UTINYINT。 ODBC *3.x*動作する ODBC ドライバー *2.x*アプリケーションは、そのドライバー マネージャーを使用して渡されるから呼び出されると、SQL_C_SHORT、SQL_C_LONG、SQL_C_TINYINT、サポートする必要があります、ドライバー。

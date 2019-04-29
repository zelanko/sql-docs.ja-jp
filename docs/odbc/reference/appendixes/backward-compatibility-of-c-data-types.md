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
ms.openlocfilehash: f1105f3adc3762e01c601d9c882bfbf0f05b9bad
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/23/2019
ms.locfileid: "63026649"
---
# <a name="backward-compatibility-of-c-data-types"></a>C データ型の下位互換性
SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT に置換された ODBC の符号付きと符号なし型。SQL_C_SSHORT、SQL_C_USHORT、SQL_C_SLONG、SQL_C_ULONG と SQL_C_STINYINT および SQL_C_UTINYINT。 ODBC 3 *.x* ODBC 2 で動作するドライバー *。x*アプリケーションから呼び出されると、ドライバー マネージャーに渡すためのドライバー、SQL_C_SHORT、SQL_C_LONG、および SQL_C_TINYINT をサポートする必要があります。

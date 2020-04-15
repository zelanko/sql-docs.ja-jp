---
title: C データ型の下位互換性 |マイクロソフトドキュメント
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 4a89b282a2229b6f34833b4371081661ea51b231
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/14/2020
ms.locfileid: "81304587"
---
# <a name="backward-compatibility-of-c-data-types"></a>C データ型の下位互換性
SQL_C_SHORT、SQL_C_LONG、SQL_C_TINYINTは、ODBC では、SQL_C_SSHORT型と SQL_C_USHORT符号なし型、SQL_C_SLONG型とSQL_C_ULONG型、SQL_C_STINYINT型とSQL_C_UTINYINT型に置き換えられています。 ODBC *2.x*アプリケーションで動作する ODBC *3.x*ドライバーは、SQL_C_SHORT、SQL_C_LONG、およびSQL_C_TINYINTをサポートする必要があります。

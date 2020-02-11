---
title: エスケープシーケンス |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
author: MightyPen
ms.author: genemi
ms.openlocfilehash: d73282cde4d0598d7e6a35ac6273935626b96969
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 02/08/2020
ms.locfileid: "68001373"
---
# <a name="escape-sequences"></a>エスケープ シーケンス
ODBC では、日付、時刻、タイムスタンプ、および日時間隔リテラルの標準文法、スカラー関数呼び出し (**述語エスケープ**文字、外部結合、プロシージャ呼び出しなど) を含むエスケープシーケンスが定義されています。 相互運用可能なアプリケーションでは、可能な限りこれらのシーケンスを使用する必要があります。  
  
 ドライバーが日付、時刻、タイムスタンプ、または datetime の各間隔のリテラルのエスケープシーケンスをサポートするかどうかを判断するために、アプリケーションは**SQLGetTypeInfo**を呼び出します。 データソースが date、time、timestamp、または datetime の各 interval データ型をサポートしている場合は、対応するエスケープシーケンスもサポートする必要があります。 他のエスケープシーケンスがサポートされているかどうかを判断するために、アプリケーションは**SQLGetInfo**を呼び出します。  
  
 詳細については、後の「 [ODBC でのエスケープシーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)」を参照してください。

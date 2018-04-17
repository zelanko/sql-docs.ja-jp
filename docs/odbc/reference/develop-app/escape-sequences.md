---
title: エスケープ シーケンス |Microsoft ドキュメント
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: f3779fc33ef11cd89339aacf0e87cc3805c8864e
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/16/2018
---
# <a name="escape-sequences"></a>エスケープ シーケンス
ODBC 日付、時刻、タイムスタンプ、および datetime 間隔リテラル スカラー関数の呼び出しの標準的な文法を含むエスケープ シーケンスを定義する**と同様に**エスケープ文字、外部結合、およびプロシージャの呼び出しの述語。 相互運用可能アプリケーションは、可能な限り、これらのシーケンスを使用してください。  
  
 調べるには、ドライバーが、日付、時刻、タイムスタンプ、または datetime 間隔のリテラルのエスケープ シーケンスをサポートしているかどうか、アプリケーションが呼び出す**SQLGetTypeInfo**です。 データ ソースは、日付、時刻、タイムスタンプ、または datetime interval データ型をサポートする場合、対応するエスケープ シーケンスもサポートする必要があります。 アプリケーションを呼び出す他のエスケープ シーケンスはサポートされているかどうかを判断するのに**SQLGetInfo**です。  
  
 詳細については、次を参照してください。 [odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)、このセクションで後述します。

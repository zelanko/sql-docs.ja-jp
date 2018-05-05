---
title: エスケープ シーケンス |Microsoft ドキュメント
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
- SQL statements [ODBC], interoperability
- escape sequences [ODBC], determining if supported
- interoperability of SQL statements [ODBC], escape sequences
ms.assetid: 5913abfa-d280-43e4-a2f1-05a924388bf9
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a2e9dc60d4cb598c777527aa6825ef2ee3a35b2b
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="escape-sequences"></a>エスケープ シーケンス
ODBC 日付、時刻、タイムスタンプ、および datetime 間隔リテラル スカラー関数の呼び出しの標準的な文法を含むエスケープ シーケンスを定義する**と同様に**エスケープ文字、外部結合、およびプロシージャの呼び出しの述語。 相互運用可能アプリケーションは、可能な限り、これらのシーケンスを使用してください。  
  
 調べるには、ドライバーが、日付、時刻、タイムスタンプ、または datetime 間隔のリテラルのエスケープ シーケンスをサポートしているかどうか、アプリケーションが呼び出す**SQLGetTypeInfo**です。 データ ソースは、日付、時刻、タイムスタンプ、または datetime interval データ型をサポートする場合、対応するエスケープ シーケンスもサポートする必要があります。 アプリケーションを呼び出す他のエスケープ シーケンスはサポートされているかどうかを判断するのに**SQLGetInfo**です。  
  
 詳細については、次を参照してください。 [odbc エスケープ シーケンス](../../../odbc/reference/develop-app/escape-sequences-in-odbc.md)、このセクションで後述します。

---
title: 国際化サポート (Visual FoxPro ODBC ドライバー) |Microsoft ドキュメント
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
- double-byte character sets [ODBC]
- FoxPro ODBC driver [ODBC], international support
- DBCS [ODBC]
- international support [ODBC]
- sort order [ODBC]
- collating sequences [ODBC]
- Visual FoxPro ODBC driver [ODBC], international support
ms.assetid: cd3fab32-13f1-4a86-abc4-5e18667669fc
caps.latest.revision: 5
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 151d3989737d221e46f6771055d0775c69f7e576
ms.sourcegitcommit: 1740f3090b168c0e809611a7aa6fd514075616bf
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>国際化サポート (Visual FoxPro ODBC ドライバー)
Microsoft Visual FoxPro ODBC ドライバーをサポートします。  
  
-   2 バイト文字セット (DBCS)  
  
-   複数の照合順序  
  
 照合順序を定義、*並べ替え順*Visual FoxPro テーブルまたはデータベースに格納されています。 既定では、ドライバーは、オペレーティング システムの言語バージョンをサポートする照合順序を使用するように構成します。  
  
 サポートされている照合順序の一覧は、次を参照してください。 [COLLATE 設定](../../odbc/microsoft/set-collate-command.md)です。  
  
## <a name="locale"></a>ロケール (locale)  
 特定の言語および国/地域に対応する情報のセット。 ロケールでは、桁区切り記号、日付と時刻の形式、および文字の並べ替え順序などの特定の設定を示します。  
  
## <a name="sort-order"></a>並べ替え順 (sort order)  
 並べ替え順序は、別の並べ替え規則を組み込む*ロケール*s、それらの言語でデータを正しく並べ替えるにすることができます。 Visual FoxPro には、現在の並べ替え順序は、文字式の比較と、レコード内の表示インデックスまたはテーブルの並べ替え順序の結果を決定します。

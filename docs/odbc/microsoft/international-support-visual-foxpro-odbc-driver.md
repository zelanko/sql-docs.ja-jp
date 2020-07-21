---
title: インターナショナルサポート (Visual FoxPro ODBC ドライバー) |Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: b4b0c758bb478ea6a468e6756c3d6f0f52c766f5
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2020
ms.locfileid: "81299972"
---
# <a name="international-support-visual-foxpro-odbc-driver"></a>国際化サポート (Visual FoxPro ODBC ドライバー)
Microsoft Visual FoxPro ODBC ドライバーでは、次の機能がサポートされています。  
  
-   2バイト文字セット (DBCS)  
  
-   複数の照合シーケンス  
  
 照合シーケンスは、Visual FoxPro テーブルまたはデータベースに格納されているデータの*並べ替え順序*を定義します。 既定では、ドライバーは、オペレーティングシステムの言語バージョンをサポートする照合シーケンスを使用するように構成されています。  
  
 サポートされている照合シーケンスの一覧については、「 [COLLATE の設定](../../odbc/microsoft/set-collate-command.md)」を参照してください。  
  
## <a name="locale"></a>locale  
 特定の言語と国/地域に対応する情報のセット。 ロケールは、小数点記号、日付と時刻の形式、文字の並べ替え順序など、特定の設定を示します。  
  
## <a name="sort-order"></a>並べ替え順 (sort order)  
 並べ替え順序には、さまざまな*ロケール*の並べ替え規則が組み込まれており、それらの言語のデータを正しく並べ替えることができます。 Visual FoxPro では、現在の並べ替え順序によって、文字式の比較結果と、インデックスまたは並べ替えられたテーブルにレコードが表示される順序が決まります。
